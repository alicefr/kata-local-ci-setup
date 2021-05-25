# Create local Kata CI environment
This setup is based on the Jenkins scripts for the Kata CI, and it locally reproduces the same environment used in the CI. More details about the environment in the [Jenkins setup docs](https://github.com/kata-containers/ci/blob/master/Jenkins_setup.md#job-build-script).

Create a VM with:
```bash
$ ./virt-build-kata -d <distro> -k <path-to-your-public-ssh-key> -o <image>
```
This script uses the default network, and you have to run it with `sudo` to configure it correctly. You can also run it as standard user, but you have to configure the network accordingly and pass it with the option `-n`.

Create a hosts.yaml file with the IP or name (if you have dns resolution) of your VM like this:
```yaml
all:
  hosts:
    192.168.122.99
```
This setup syncronize your local kata-containers and tests repo inside the VM. As default, this setup looks for the kata repo in `$HOME/go/src/github.com/kata-containers`. If you have the code under under path, you have to change the variable `kata_containers_repo_path` in `env_var.yaml`.

Prepare and run the Kata CI tests:
```bash
$ ansible-playbook  -i hosts.yaml run-local-kata-ci.yaml
```
When the the ansible-playbook finished (with errors or not),and it will copy the output in the directory `kata-ci-job.log`.

If you want to check the log of the script while it is running:
```bash
$ ssh kata@192.168.122.99 tail -f /home/kata/kata_ci_job.log
```
You can customize the this setup by modifying the file `env_var.yaml`.
