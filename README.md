# Create local Kata CI environment
This setup is based on the Jenkins scripts for the Kata CI, and it locally reproduces the same environment used in the CI. More details about the environment in the [Jenkins setup docs](https://github.com/kata-containers/ci/blob/master/Jenkins_setup.md#job-build-script).

Create a VM with:
```bash
$ ./virt-build-kata <distro>
```
Create a hosts.yaml file with the IP of your VM like this:
```yaml
all:
  hosts:
    192.168.122.99
```
This setup syncronize your local kata-containers and tests repo inside the VM. Currently, this setup expect to find the kata repos under `$HOME/go/src/github.com/kata-containers`. 

Prepare and run the Kata CI tests:
```bash
$ ansible-playbook  -i hosts.yaml install.yaml 
```

