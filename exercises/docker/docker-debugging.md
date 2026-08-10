# Docker Debugging Exercises

## 1. Debug a container that exits immediately

**Problem:** A container exits right after starting.

**Solution:** Check the logs and run it in interactive mode.

```bash
docker logs <container-id>
docker run -it <image> /bin/bash
```

## 2. Debug a container that is running but not responding

**Problem:** The container is running but you can't connect to it.

**Solution:** Inspect the container's network settings and processes.

```bash
docker inspect <container-id>
docker top <container-id>
```

## 3. Debug a Dockerfile build failure

**Problem:** The build fails at a step.

**Solution:** Use `docker build` with `--progress=plain` and check the step output.

```bash
docker build --progress=plain -t my-image .
```

## 4. Debug a volume mount issue

**Problem:** Files are not appearing in the mounted volume.

**Solution:** Verify the mount path and permissions.

```bash
docker inspect <container-id> | grep -A 5 Mounts
```

## 5. Debug a network issue between containers

**Problem:** Containers on the same network can't ping each other.

**Solution:** Check the network and use `docker exec` to test connectivity.

```bash
docker network ls
docker exec <container-id> ping <other-container>
```

## 6. Debug resource exhaustion

**Problem:** Container is killed due to OOM or CPU limits.

**Solution:** Check `docker stats` and adjust limits.

```bash
docker stats
docker run --memory=512m --cpus=0.5 my-image
```

## 7. Debug a container that can't start due to port conflict

**Problem:** Port already in use.

**Solution:** Find the process using the port and change the mapping.

```bash
sudo lsof -i :8080
docker run -p 8081:80 my-image
```

## 8. Debug a container that is in a restart loop

**Problem:** Container keeps restarting.

**Solution:** Check the logs and the restart policy.

```bash
docker logs <container-id> --tail 50
docker inspect <container-id> | grep RestartPolicy
```

## 9. Debug a Docker daemon issue

**Problem:** Docker commands hang or fail.

**Solution:** Check daemon status and logs.

```bash
sudo systemctl status docker
sudo journalctl -u docker
```

## 10. Debug a container that is not reachable from the host

**Problem:** Can't access a published port.

**Solution:** Verify the port binding and firewall rules.

```bash
docker port <container-id>
sudo ufw status
```

## Common commands cheat sheet

```bash
docker ps -a
docker logs <container-id>
docker inspect <container-id>
docker exec -it <container-id> /bin/sh
docker stats
```

## Tips

- Use `docker system events` to see real-time events.
- Use `docker system df` to check disk usage.
- Use `docker system prune` to clean up unused resources.