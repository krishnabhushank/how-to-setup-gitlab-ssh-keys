# How To Setup Gitlab SSH keys and Passwordless Authentication

You got access to a Unix Server and access to GitLab. You want to setup Password authentication. Follow the below steps.

- On your Unix Box, (Say - app01), login and create SSH keys
  - Enter ` ssh-keygen -t dsa ` and press the enter key three times to generate the ssh keys.
  - Enter ` cd ~/.ssh ` to switch to the directory where the ssh keys are stored.
  - Enter ` cat id_dsa.pub >> authorized_keys ` to authorize no-password ssh logon for your ID.
  - Enter ` chmod 700 ~/.ssh; chmod 600 authorized_keys id_dsa id_dsa.pub ` to set the proper permissions on these files in order for this feature to work.
  - Enter ` chmod g-w,o-w ~ ` to ensure that your $HOME home directory permissions is set to `755 (rwxr-xr-x)` or less.
- Test SSH setup
  - Test the ssh keys by entering ` ssh $HOSTNAME `. If you can ssh to yourself without the need to enter a password, it is set-up correctly.
- Note your SSH public key
  - ` cd ~/.ssh; cat  id_dsa.pub `
- Login to GitLab > go to https://<gitlab_url>/profile > go to SSH Key tab
  - Paste Public Key
  - Change Title to show Correct Description
  - Click on ` Add Key `