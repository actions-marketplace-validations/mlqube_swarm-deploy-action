# Swarm Deploy Action

A [GitHub Action](https://github.com/features/actions) that enables you to publish your app as a [Docker stack](https://docs.docker.com/engine/swarm/stack-deploy/) to a remote Docker swarm.

## Example

Below is a brief example on how the action can be used:

```yaml
- name: Deploy to swarm
  uses: mlqube/swarm-deploy-action@v1
  with:
    remote_host: swarm.server.com
    ssh_private_key: ${{ secrets.DOCKER_SSH_PRIVATE_KEY }}
    args: docker stack deploy -c stack.yml coolapp
```

If you are deploying any private Docker images, you can use the [Docker Login](https://github.com/marketplace/actions/docker-login) action to first log in to your private registry, and then provide the `--with-registry-auth` flag to `docker stack deploy` to use the logged in credentials during deployment.

## Inputs

Below are all of the supported inputs. Some inputs used to authenticate with your swarm should be kept private, and should be supplied as secrets for security.

### `args`

Command that should be executed using docker context, for example `docker stack deploy -c stack.yml coolapp`

### `remote_host`

This must be a manager node in your swarm for most operations to work.

### `ssh_private_key`

When connecting to Docker over SSH, this must contain the SSH private key to use to connect.

## License

This project is licensed under the MIT license. See the [LICENSE](LICENSE) file for details.