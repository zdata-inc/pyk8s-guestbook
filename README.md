###Forked from  https://github.com/kubernetes/examples.git
 
# Example: Guestbook application on Kubernetes running Python and Flask

This directory contains the source code and Kubernetes manifests for Python, Redis, and Nginx.

All yaml files have been updated to use Flask in place of PHP. This should boot up multiple containers for:
- Ngnix as a frontend and traffic management
- Python Flask as worker
- Redis and slave nodes as data store

Each piece does have its own container and image to maintain.
  
#To Do
- Add Test cases to ensure each container works (This can be simple curl tests to ensure responses)
- image names in the yaml files still need to be changed for EKS
- explore Helm if that will be easier for deployment
- Documentation!!! Should be commited to this github please



