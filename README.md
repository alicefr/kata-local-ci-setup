# Create local Kata CI environment
This setup is based on the Jenkins scripts for the Kata CI. It reproduces locally the same environment used in the Kata CI. More detailsabout the environment in the [Jenkins setup docs](https://github.com/kata-containers/ci/blob/master/Jenkins_setup.md#job-build-script).

Create a VM with:
```bash
$ ./virt-build-kata
```
Modify the IP of you VM in `hosts.yaml`

Prepare and run the Kata CI tests:
```bash
$ ansible-playbook  -i hosts.yaml install.yaml 
```

