you like this work ?

[!["You like it ?"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/sorriso)

# kube-docker-scap-ubi8-min

Kubernetes yaml configuration files for openscap scan based on UBI8
to be used by jenkins via kubernetes to scan docker images

## prerequisite:

- Rancher desktop (or equivalent) installed locally & running with "containerd" selected as main command tool

## How to make it working :

- run /build/0-build-image.sh to build & upload the image "l_docker:scap" in k8s.io local repository

- use the image "l_docker:scap" as template in your jenkins build
