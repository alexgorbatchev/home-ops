# Storage

{% import 'links.jinja2' as links %}

Storage in my cluster is handled in a number of ways.
The in-cluster storage is provided by a {{ links.external('rook-ceph') }} cluster that is running on a number of my nodes.

## rook-ceph block storage

The bulk of my cluster storage relies on my `CephBlockPool` ({{ links.repoUrl('link', 'blob/main/cluster/core/rook-ceph/storage/cephblockpool.yaml') }}). This ensures that my data is replicated across my storage nodes.

## NFS storage

Finally, I have my NAS that exposes several exports over NFS. Given how NFS is a very bad idea for storing application data (see for example [this Github issue](https://github.com/Sonarr/Sonarr/issues/1886)) I only use it to store data at rest, such as my personal media files, Linux ISO's, backups, etc.
