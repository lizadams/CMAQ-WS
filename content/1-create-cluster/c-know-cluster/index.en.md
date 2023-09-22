---
title: Get to know the cluster
weight: 23
--- 

Now that you are connected to the head node, you can familiarize yourself with the cluster structure by running the following set of commands.

:::alert{type=info}
[SLURM](https://slurm.schedmd.com/) from SchedMD is one of the resource manager that you can use in AWS ParallelCluster. For an overview of the SLURM commands, see the [SLURM Quick Start User Guide](https://slurm.schedmd.com/quickstart.html). If you are familar with PBS, here is the [PBS-Slurm Conversion Cheat Sheet](https://www.nrel.gov/hpc/assets/pdfs/pbs-to-slurm-translation-sheet.pdf)
:::

If you create a new shell, or switch between a shell in the Terminal on SSM Connect versus a Terminal on the DCV, you will need to verify your username and verify that you are using the tcsh shell..

Your user should be similar to `ec2-user@ip-<IP-address>`. If it is otherwise something like `sh-4.2` or `ssm-user@<IP-address>`, then run the following command before proceeding:

1. Check username

```csh
whoami
```

Your user should be similar to `ec2-user@ip-<IP-address>`. If it is otherwise something like `sh-4.2` or `ssm-user@<IP-address>`, then run the following command before proceeding:

2. Switch username to ec2-user

```bash
sudo su ec2-user
```

![ec2-user](/static/images/1-gettoknow-ec2user.png)

3. **Verify shell**

   ```csh
   echo $SHELL
   ```

4. **If not in tcsh shell, then change shell to use tcsh**
The tcsh shell loads the custom module environment required to run CMAQ. 

   ```csh
   /bin/tcsh
   ```


5. **List existing partitions and nodes per partition.** 

    ```bash
    sinfo
    ```

    Running `sinfo` shows both the instances we currently have running and those that are not running (think of this as a queue limit). Initially we’ll see all the node in state `idle~`, which means that no instances are running. When we submit a job we’ll see some instances go into state `alloc` meaning that they’re currently completely allocated, or `mix` meaning that some but not all cores are allocated. After the job completes the instance stays around for a few minutes (the [default cooldown](https://docs.aws.amazon.com/parallelcluster/latest/ug/Scheduling-v3.html#yaml-Scheduling-SlurmSettings-ScaledownIdletime) is 10 mins) in state `idle%`. This can be confusing, so we’ve tried to simplify it in the following table:

    | State   | Description                                                 |
    | -----   | ----------------------------------------------------------- |
    | `idle~` | Instance is not running but can launch when a job is submitted. |
    | `idle%` | Instance is running and will shut down after Scaledownidletime (default 10 mins). |
    | `mix`   | Instance is partially allocated.                            |
    | `alloc` | Instance is completely allocated.                           |

    **Output**:

    ![sinfo](/static/images/1-gettoknow-sinfo.png)


#### Module Environment

[Environment Modules](http://modules.sourceforge.net/) or [Lmod](https://lmod.readthedocs.io/en/latest/) are fairly standard tools in HPC that are used to dynamically change your environment variables (`PATH`, `LD_LIBRARY_PATH`, etc.).

6. **List available modules**  The cluster has *openmpi* pre-installed by amazon. This MPI version of openmpi was compiled with support for the high-speed interconnect EFA.

    ```csh
    module avail
    ```

    **Output**:

    ![module avail](/static/images/1-gettoknow-moduleavail.png)

7. **List the modules that are loaded, and the path to the version of mpirun that is being used** 

    ```csh
    module list
    which mpirun
    ```

    **Output**:

    ![module load intelmpi](/static/images/1-gettoknow-whichmpirun.png)

#### Filesystems

8. **List mounted volumes.** A few volumes are shared by the head-node via NFS and will be mounted on compute instances when they boot up. Both /fsx and /home are accessible by all nodes.

* **Check the amount of available disk space for all file systems**. When we created the cluster, we also created a Lustre filesystem with FSx Lustre. We can see where it was mounted and the storage size by running:

    ```csh
    df -hT
    ```
  
    **Output**:
    ![dfht](/static/images/1-gettoknow-dfht.png)

* Print the list of exported NFS-based filesystems on the head node.

    ```csh
    showmount -e localhost
    ```

    **Output**:

    ![Showmount](/static/images/1-gettoknow-showmount.png)

In the next section, we will explore the CMAQ software installed on the /shared filesystem!
