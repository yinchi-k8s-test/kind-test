# Test cluster using Minikube

This repo contains configuration files for setting up a test cluster on Minikube. See the 2nd-level `README.md` files for information about each component.

- To launch the cluster: execute
  ```bash
  ./init.sh
  ```
  This installs the **base services only**: the Kubernetes dashboard, Traefik, and a simple `whoami` service.
- To expose Traefik, execute
  ```bash
  ./traefik/portforward.sh
  ```
- To expose the Kubernetes dashboard, execute
  ```bash
  ./dashboard/portforward.sh
  ```
- To launch service `foo`: execute
  ```bash
  ./foo/init.sh
  ```
  In general, each service will have an `init.sh` and `delete.sh` script.


## Port forwarding and SSH tunneling

Our port-forwarding scripts are set up to forward to `localhost` only. To access the Traefik endpoint remotely, use:
```bash
ssh -L 8000:localhost:8000 <user>@<hostname>
```
The endpoint should then be available at `http://<hostname>:8000`. Similarly, create tunnels on the other forwarded ports to access the Traefik and Kubernetes dashboards.