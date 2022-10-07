# https://github.com/kran0/dind-alternative/blob/master/Dockerfile
#
FROM redhat/ubi8-minimal

COPY /repo/ubi.repo  /etc/yum.repos.d/ubi.repo
COPY /repo/centos-8.repo /etc/yum.repos.d/centos-8.repo
COPY /gpg /etc/pki/rpm-gpg
COPY /daemon.json /etc/docker/daemon.json

RUN set -eux \
 && microdnf repolist --disableplugin=subscription-manager\
 && microdnf -y upgrade --disableplugin=subscription-manager\
 && microdnf -y update --disableplugin=subscription-manager\
 && microdnf -y install --disableplugin=subscription-manager wget podman openscap openscap-scanner openscap-utils scap-security-guide\
 && wget -O - https://www.redhat.com/security/data/oval/v2/RHEL8/rhel-8.oval.xml.bz2 | bzip2 --decompress > rhel-8.oval.xml\
 && microdnf clean all --disableplugin=subscription-manager\
 && rm -rf /var/cache/yum

ENTRYPOINT ["tail"]
CMD ["-f","/dev/null"]


# podman pull alpine:latest
# podman pull redhat/ubi8:latest
# podman images
# oscap-podman 10f854072e7e oval eval --report vulnerability.html rhel-8.oval.xml
# ${BUILD_CONTAINER_ID}
# podman cp <container_id>:/home/jenkins/workspace /home/jenkins/workspace
