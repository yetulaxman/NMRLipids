# Provisioning  a custom Jupyter notebook on Puhti web interface for NMRLipids course (WIP)

A custom Jupyter notebook for NMRLipids course (NMRlipids summer school 2022) can be provisioned through [Puhti web interface](https://www.puhti.csc.fi). The customisation of computational environment involves the following steps:

- [Installing necessary python packages to projappl directory using tykky](#installing-necessary-python-packages-to-projappl-directory-using-tykky)
- [Creating a course environment/module(s)](#creating-a-course-environment-modules)
- [Accessing notebook via Puhti web interface](#accessing-notebook-via-puhti-web-interface)
- [Useful CSC documentation](useful-CSC-documentation)

### Installing necessary python packages to *projappl* directory using *tykky*:

Tykky wraps installations inside singularity container for improved performance cinluding faster startup times, reduced IO load, and  few number of files on large parallel filesystems. Please refer to CSC documentation on Tykky](#https://docs.csc.fi/computing/containers/tykky/) for more detailed information.

For the installation of computational environment required for NMRLIpids course, we use the tykky in the following way:

```bash
cd /scartch/project_xxxx/
git clone https://github.com/NMRLipids/Databank.git
mkdir NMRLipids  && cd NMRLipids 

module load tykky
mkdir /projappl/project_xxxx/NMRLipids
conda-containerize new --prefix /projappl/project_xxxx/NMRLipids  env_nmr.yml 

```
Tykky will install all needed packages (as mentioned in env_nmr.yml)
### Creating a course environment modules

The files for course environments (modules) can be created in /projappl/<project>/www_puhti_modules/. The www_puhti_modules directory can be created if it does not exist.

The course environment is only visible for the project that it was created for. Note that you may need to Restart Web Server in the Help menu in the web interface if the course environment is not visible in the form after creating the files and selecting the correct project.

Two files are needed for the course modules:

    a <course>.lua file that defines the module that sets up the Python environment. Only files containing the text Jupyter will be visible in the app.
    a <course>-resources.yml that defines the default resources used for Jupyter.
  
    
### Accessing notebook via Puhti web interface

1. Access Open OnDemand (OoD) interface on [Puhti login page](https://www.puhti.csc.fi/public/login.html)
2. Login with CSC or course credentials (Users should have accepted Puhti service in [myCSC](https://my.csc.fi/welcome) page under a course ( or own) project before using this service). Login page is as shown below:

<img src="./Puhti_login.png" width="80%">

3. Once login is successfull, select "Apps" on the top menu bar and then click "Gromacs course". Fill all the necessary information ( e.g., select your CSC project, partition (use "small" when using reservation), computing resources among others) and then click "Launch" 
4. Upon successful launching a job, you can see the following window: 

5. Click on "Connect to VNC" to launch GUI desktop to then VMD (see below picture) 
7. Again on OoD job page, click on "Connect to Jupyter" to launch Gromacs notebook.




###  Useful CSC documentation

- Jupyter for course (https://docs.csc.fi/computing/webinterface/jupyter-for-courses/)
- Tykky containerisation (https://docs.csc.fi/computing/containers/tykky/)



