# docker-nfs-client

Docker image for a light NFS client (~10.9MB). By default NFS 4 is used.



## Usage

### Build

    $ docker build -t nfs-client .

### Run

Basic example, mounting NFS within container:


Writing back to the host:

    $ docker run -itd \
    --privileged=true \
    --net=host \
    --name nfs-pi\
    -v /mnt/NFS-PI:/mnt/nfs-1:shared \
    -e SERVER=192.168.2.204 \
    -e SHARE=/ \
      nfs-client

#### Runtime Environment Variables

There should be a reasonable amount of flexibility using the available variables. If not please raise an issue so your use case can be covered!

- `SERVER` - the hostname of the NFS server to connect to
- `SHARE` - the name of the NFS share to mount
- `MOUNT_OPTIONS` - mount options to mount the NFS share with
- `FSTYPE` - the filesystem type; specify `nfs3` for NFSv3, default is `nfs` i.e. NFSv4
- `MOUNTPOINT` - the mount point for the NFS share within the container
