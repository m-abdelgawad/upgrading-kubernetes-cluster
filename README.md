<a name="readme-top"></a>

[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<div align="center">
  <img src="readme_files/logo.png" alt="Logo" width="100">
  <h3 align="center">Upgrading a Kubernetes Cluster</h3>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project">About The Project</a></li>
    <li><a href="#introduction">Introduction</li>
    <li>
        <a href="#steps">Steps</a>
        <ul>
            <li><a href="#initial-steps">Initial Steps</a></li>
            <li><a href="#master-node-steps">Master Node Steps</a></li>
            <li><a href="#worker-node-steps">Worker Node Steps</a></li>
      </ul>
    </li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#references">References</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

<img src="readme_files/cover.jpg" alt="Cover Image">

* Project Name: Upgrading a Kubernetes Cluster
* Version: v1.0.0
* Organization Department: Technology

## Introduction

In this project, I've documented upgrading a Kubernetes cluster from v1.29.0 to v1.29.1.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Steps

### Initial Steps

1. Check available nodes and their current version. We can see that the cluster has one master node and two worker nodes. All of them are running kubelet v1.29.0
<img src="readme_files/1.jpg">

2. Open the documentation page of <a href="https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/">Upgrading kubeadm clusters</a>.
<img src="readme_files/2.jpg">

3. Determine which OS we're running using `cat /etc/*release*`. We can see that we're running Ubuntu on the servers. So, we will follow all Ubuntu instructions in the documentation page.
<img src="readme_files/3.jpg">

4. Determine which version to upgrade to. We can see that the latest version is `1.29.1-1.1`. So, we'll upgrade everything to that version.
```
# Find the latest 1.29 version in the list.
# It should look like 1.29.x-*, where x is the latest patch.
apt update
apt-cache madison kubeadm
```
<img src="readme_files/4.jpg">

### Master Node Steps

1. Upgrade kubeadm:
```
# replace x in 1.29.x-* with the latest patch version
apt-mark unhold kubeadm && \
apt-get update && apt-get install -y kubeadm='1.29.1-1.1' && \
apt-mark hold kubeadm
```
<img src="readme_files/5.jpg">

2. Verify that the download works and has the expected version:
```
kubeadm version
```
<img src="readme_files/6.jpg">

3. Verify the upgrade plan:
```
kubeadm upgrade plan
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Mohamed AbdelGawad Ibrahim - [@m-abdelgawad](https://www.linkedin.com/in/m-abdelgawad/) - <a href="tel:+201069052620">+201069052620</a>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## References

* https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/m-abdelgawad/
