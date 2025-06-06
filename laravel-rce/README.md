<h1 align="center">Remote Code Execution: Laravel (CVE-2021-3129)</h1>

<p align="center">
    <img src="https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fjoshuavanderpoll%2FCVE-2021-3129&label=Views&countColor=%2337d67a" />
    <a href="https://www.python.org/">
      <img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54" alt="Python">
    </a>
</p>

## 📜 Description 
This script is designed to exploit the Remote Code Execution (RCE) vulnerability identified in several Laravel versions, known as CVE-2021-3129. By leveraging this vulnerability, the script allows users to write and execute commands on a target website running a vulnerable Laravel instance, provided that the "APP_DEBUG" configuration is set to "true" in the ".env" file.

## 📚 Table of Contents
- 📜 [Description](#-description)
- 🛠️ [Installation](#️-installation)
- ⚙️ [Usage](#️-usage)
- 🐋 [Docker POC](#-docker-poc)
- 💻 [Example](#-example)
- 🩹 [Patch options](#-patch-options)
- 🕵🏼 [References](#-references)
- 📢 [Disclaimer](#-disclaimer)

## 🛠️ Installation
> [!NOTE]
> To ensure a clean and isolated environment for the project dependencies, it's recommended to use Python's venv module.
```bash
$ git clone https://github.com/joshuavanderpoll/CVE-2021-3129.git
$ cd CVE-2021-3129
$ python3 -m venv .venv
$ source .venv/bin/activate
$ pip3 install -r requirements.txt
```

## ⚙️ Usage
![Usage](/assets/usage.jpg)

## 🐋 Docker POC
```bash
$ docker build -t laravel_vulnerable .
$ docker run -p 8000:8000 laravel_vulnerable
```

## 💻 Example
![Example](/assets/example.jpg)

## 🩹 Patch options
- ``env`` (Updates the .env file to set APP_DEBUG to false)
- ``index`` (Injects code into index.php which prevents access to "/_ignition/execute-solution")
- ``private`` (Same as the index option, but allows specific header to access "_ignition/execute-solution")
  
## 🕵🏼 References
- https://github.com/ambionics/phpggc

## 📢 Disclaimer
This tool is provided for educational and research purposes only. The creator assumes no responsibility for any misuse or damage caused by the tool.
