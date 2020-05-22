# README

Transparent proxy server that works as a poor man's VPN

## Installation

```sh
# Define installation folder

export INSTALL_DIRECTORY=/usr/bin

# Use local installation

sudo bin/installer install

# Use remote installation

curl --location "https://gitlab.com/timonier/sshuttle/raw/master/bin/installer" | sudo sh -s -- install
```

__Note__: If you do not define `INSTALL_DIRECTORY`, `installer` will use in `/usr/local/bin`.

## Usage

Run the command `sshuttle`:

```sh
# See all sshuttle options

sshuttle --help

# Run sshuttle

sshuttle --remote username@sshserver --ssh-cmd 'ssh -oStrictHostKeyChecking=no -oUserKnownHostsFile=/dev/null' 0/0
# client: Connected.
```

__Note 1__: To stop sshuttle, you have to send a `SIGINT` signal. If you send a `SIGTERM` or a `SIGKILL`, the iptables chain `sshuttle-12300` will not be flushed.

__Note 2__: You can define the path of the SSH key via the environment variable `SSH_KEY` (default value is `${HOME}/.ssh/id_rsa`).

## Contributing

1. Fork it.
2. Create your branch: `git checkout -b feature/my-new-feature`.
3. Commit your changes: `git commit -am 'Add some feature'`.
4. Push to the branch: `git push origin feature/my-new-feature`.
5. Submit a [merge request](https://docs.gitlab.com/ee/user/project/merge_requests/).

__Note__: [GitHub repository](https://github.com/timonier/sshuttle) is a mirror. [Merge request](https://docs.gitlab.com/ee/user/project/merge_requests/) has to be submitted to the [GitLab repository](https://gitlab.com/timonier/sshuttle).

If you like / use this project, please let me known by adding a [★](https://help.github.com/articles/about-stars/) on the [GitHub repository](https://github.com/timonier/sshuttle) or on the [GitLab repository](https://gitlab.com/timonier/sshuttle).

## Links

* [image "timonier/sshuttle"](https://hub.docker.com/r/timonier/sshuttle/)
* [sshuttle/sshuttle](https://github.com/sshuttle/sshuttle)
