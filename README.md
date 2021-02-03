# Create local CI machine 
Create a VM with:
```bash
$ ./virt-build-kata
```
Modify the IP of you VM in `hosts.yaml`
This setup syncronize your local kata-containers and tests repo inside the VM.

Prepare and run the Kata CI tests:
```bash
$ ansible-playbook  -i hosts.yaml install.yaml 
```

