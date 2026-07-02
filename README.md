# claude-sandbox

## Build

```
podman build --build-arg USER_UID=$(id -u) --build-arg USER_GID=$(id -g) -t claude-sandbox -f Containerfile
```


## Run 

```
podman run -it --rm --hostname=claude-sandbox \
  --network=host \
  --userns=keep-id:uid=1000,gid=1000 \
  -e HOME=/home/ubuntu \
  -v "$(pwd):/home/ubuntu/$(basename $(pwd)):Z" \
  -v "$HOME/.claude.json:/home/ubuntu/.claude.json:Z" \
  -v "$HOME/.claude:/home/ubuntu/.claude:Z" \
  claude-sandbox
```
