# README

Transparent proxy server that works as a poor man's VPN

## Installation

Copy `bin/sshuttle` into your executable folder (like `/usr/local/bin` or `$HOME/bin`):

```sh
sudo curl --location --output /usr/local/bin/sshuttle "https://github.com/timonier/sshuttle/raw/master/bin/sshuttle"
sudo chmod +x /usr/local/bin/sshuttle
```

Linux users can use the [installer](https://github.com/timonier/sshuttle/blob/master/bin/installer):

```sh
curl --location "https://github.com/timonier/sshuttle/raw/master/bin/installer" | sudo sh -s -- install
```

## Usage

Run the command `sshutle`:

```sh
# See all sshuttle options

sshuttle --help

# Run sshuttle

sshuttle \
    --remote username@sshserver \
    --ssh-cmd 'ssh -oStrictHostKeyChecking=no -oUserKnownHostsFile=/dev/null' \
    0/0
# client: Connected.
```

__Note 1__: To stop sshuttle, you have to send a `SIGINT` signal. If you send a `SIGTERM` or a `SIGKILL`, the iptables chain `sshuttle-12300` will not be flushed.

__Note 2__: You can define the path of the SSH key via the environment variable `SSH_KEY` (default value is `${HOME}/.ssh/id_rsa`).

## Contributing

1. Fork it.
2. Create your branch: `git checkout -b my-new-feature`.
3. Commit your changes: `git commit -am 'Add some feature'`.
4. Push to the branch: `git push origin my-new-feature`.
5. Submit a pull request.

__Note__: Use the script `bin/build` to test your modifications locally.

## Links

* [image "timonier/sshuttle"](https://hub.docker.com/r/timonier/sshuttle/)
* [sshuttle/sshuttle](https://github.com/sshuttle/sshuttle)
* [timonier/dumb-entrypoint](https://github.com/timonier/dumb-entrypoint)
* [timonier/version-lister](https://github.com/timonier/version-lister)
