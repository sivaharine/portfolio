# portfolio
A personal portfolio website built with HTML and CSS. Showcases my education, skills, projects, and achievements. Easily deployable using Ansible for automated server setup. Clean, responsive, and lightweight design for all devices.

------------------------------
open wsl in windows powershell.
------------------------------
WSL stands for Windows Subsystem for Linux.
It is a feature in Windows that allows you to run a Linux environment directly on Windows without the need for a virtual machine or dual-boot setup

--------------------------------
cd ~/html_hosting
--------------------------------

 To navigate to your project folder where you keep your website or portfolio files (e.g., index.html).
✅ Necessary before running commands like ansible-playbook, git, or copying files.
✅ Keeps your work organized in a specific directory instead of cluttering your home or root folders.

----------------------------------
ls
-----------------------------------

📂 ls = "list"
It is used to list files and directories in the current working directory.

-----------------------------------
nano index.html
-----------------------------------
✅ To create or edit an HTML file (like your portfolio page).
✅ Runs directly in the terminal — no need for a separate GUI text editor.
✅ Good for quick edits on remote servers (especially with SSH).

-----------------------------------
nano webserver.yml code
-----------------------------------


✅ To write or modify an Ansible playbook named webserver.yml.
✅ Typically contains tasks to set up a web server (like installing Nginx, copying your portfolio HTML, etc.)
✅ Useful when working in a terminal environment (especially on WSL, Linux, or remote SSH).

inside webserver.yml running using apache webserver

 tasks:
    - name: Install Apache
      apt:
        name: apache2
        state: present
        update_cache: yes

    - name: Copy HTML file to web root
      copy:
        src: index.html
        dest: /var/www/html/index.html
        owner: www-data
        group: www-data
        mode: '0644'

    - name: Ensure Apache is running
      service:
        name: apache2
        state: started
        enabled: yes

------------------------------------------------
 ansible-playbook webserver.yml --ask-become-pass
 ------------------------------------------------

 
ansible-playbook: This is the Ansible command used to run a playbook. A playbook is a YAML file that defines a set of tasks to automate configuration or deployment on one or more remote machines.

webserver.yml: This is the name of the playbook file you want to run. Usually, this file contains tasks related to installing, configuring, or managing a web server (like Apache or Nginx).

--ask-become-pass: This option tells Ansible to prompt you for the sudo (or privilege escalation) password. It is needed if the tasks in the playbook require elevated privileges on the target machines (for example, installing software or modifying system files).

Finally website got hosted in localhost
