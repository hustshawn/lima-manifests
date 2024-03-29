lima-manifests
===

Using `lima` to create VM on M1 Mac.

## Install Lima
```
brew install lima
```


- `lima-x86.yaml`, simulate x86 arch on M1 Mac, and provide docker env to the host.
- `minikube.yaml`, create x86 arch VM, and run `minikube` inside.


## Basic Usage
### Create VM
```
limactl start <manifest-file>
```
use `--name=default` if you wanna make it as the default VM.


### List VM
```
limactl list
```

### Exec shell inside VM
```
limactl shell <vm-instance-name>
```

## Use the docker context
```
docker context create amd64 --docker "host=unix://${HOME}/.lima/lima-x86/sock/docker.sock"
docker docker context use amd64
```

## FAQ
- Facing an error like  `Error saving credentials: error storing credentials - err: exit status 1, out: `Post "http://ipc/registry/credstore-updated": dial unix /Users/xxx/Library/Containers/com.docker.docker/Data/backend.sock: connect: no such file or directory`

  **Solution**: Simply remove `"credStore": "desktop"` from the `~/.docker/config.json`.
