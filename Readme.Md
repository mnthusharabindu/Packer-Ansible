$env:AWS_ACCESS_KEY_ID="anaccesskey"
$env:AWS_SECRET_ACCESS_KEY="asecretkey"
$env:AWS_REGION="us-west-2"

1. Configured S3 backend
2. Terraform state rm and mv
3. Terraform dependencies.
4. Terraform AWS env variables.


ssh-agent & ssh-add
https://www.cs.swarthmore.edu/newhelp/ssh-agent.html

To set up SSH agent to avoid retyping passwords, you can do:
ssh-agent bash
ssh-add ~/.ssh/id_rsa

- name: Run Apt Update
  shell: apt update
- name: Install Nginx Server
  apt: >
    name=nginx
    state=present
- name: Copy the index.j2 Template to index destination folder.
  template: >
     src=index.j2
     dest=/var/www/html/index.nginx-debian.html
     owner=root
     group=root
     mode=0644
 - name: Copy the style files to destination folder.
   copy: >
      src=style.css
      dest=/var/www/html/style.css
      owner=root
      group=root
      mode=0644
 - name: Copy the javascript files to destination folder.
   copy: >
      src=scorekeeper.js
      dest=/var/www/html/scorekeeper.js
      owner=root
      group=root
      mode=0644
 - name: restart nginx
   command: service nginx restart