---
title: "CMAQ on AWS HPC Workshop"
weight: 00
---

Amazon Web Services (AWS) provides the most elastic and scalable cloud infrastructure to run your air quality workloads. High Performance Computing (HPC) clusters are built on high performance processors with high speed memory, storage, and networking. With virtually unlimited capacity, engineers, researchers, HPC system administrators, and organizations can innovate beyond the limitations of on-premises HPC infrastructure.

HPC on AWS removes the long wait times and lost productivity often associated with on-premises HPC clusters. Flexible HPC cluster configurations and virtually unlimited scalability allows you to grow and shrink your infrastructure as your workloads dictate, not the other way around. Additionally, with access to a broad portfolio of cloud-based services for Data Analytics, Artificial Intelligence (AI), and Machine Learning (ML), you can reinvent traditional Air Quality Modeling workflows to derive results faster and under budget.

Find our Air Quality and Weather related HPC customer case studies at https://aws.amazon.com/hpc/customers/, under **Weather**.

Doing all parts of this workshop should take approximately 3 hours.

This workshop is designed for modelers who want to learn more about running CMAQ using AWS HPC.

![Surface temperature](static/images/0-PM25_VERDI.gif)

**Region specific constraints**

In order to successfully run this workshop requires a snapshot that is only available in the us-east-1 region. The yaml file uses the HPC7g compute node, and these compute nodes are available in a limited number of regions, including the us-east-1 region.

The snapshot that contains the software installation that was built on Alinux2 is open to the public, and is available in the us-east-1 region.

Users can copy the public snapshot from the us-east-1 region to any region where the hpc7g instance is available and modify the yaml file to create a ParallelCluster in another region where hpc7g instances are available. Alternatively, you can use the c7g EC2 instances in more regions, but the cost will be higher.

If you would like to build a ParallelCluster using a different operating system or EC2 compute node, you will need to follow the instructions in the Developer Guide section of the CMAQ on AWS Tutorial to install the libraries and CMAQ software. https://pcluster-cmaq.readthedocs.io/en/latest/user_guide_pcluster/developers_guide/index.html


**Disclaimer**

The statements in this training manual are those of the staff of the Community Modeling and Analysis Center and not necessarily those of the University of North Carolina at Chapel Hill nor United States Environmental Protection Agency.  The material in this training manual has not been subjected to the U.S. EPA’s peer and administrative review, nor has it been approved for publication as an EPA document. The mention of commercial products, their source, or their use in connection with material reported herein is not to be construed as actual or implied endorsement of such products.

**Acknowledgements**

The U.S. EPA, through its Office of Research and Development, partially funded and collaborated in the research described here under EP-W-16-014 to UNC Chapel Hill. We also thank Amazon Web Services for offering cloud credits to use in this workshop.


© 2023 Institute for the Environment, University of North Carolina at Chapel Hill, https://cmascenter.org/
