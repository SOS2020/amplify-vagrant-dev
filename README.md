# amplify-vagrant-dev
Vagrant AWS Amplify development environment

# Instructions
1.) Set the Amplify development directory on the host pc.

Mac and Linux:
```
export amplify_host_dir="some_path"
```
Windows PowerShell:
```
$env:amplify_host_dir="some_path"
```
2.) Launch the VM.
```
vagrant up centos8vb
```
3.) Configure Amplify
```
amplify configure
```
See: [Option 2: Follow the instructions](https://docs.amplify.aws/start/getting-started/installation/q/integration/react#option-2-follow-the-instructions)

#
To shutdown the VM
```
vagrant halt centos8vb
```

To destroy the VM
```
vagrant destroy centos8vb
```