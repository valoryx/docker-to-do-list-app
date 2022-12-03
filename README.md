# Created a "To-Do-List" app container with persistent DB access

- Each container starts from the image definition each time it starts. While containers can create, update, and delete files, those changes are lost when the container is removed and all changes are isolated to that container. With volumes, we can change all of this. Named volumes provide the ability to connect specific filesystem paths of the container back to the host machine. If a directory in the container is mounted, changes in that directory are also seen on the host machine. If we mount that same directory across container restarts, we’d see the same files.

- By default, the To-Do-List app stores its data in a SQLite Database at /etc/todos/todo.db in the container’s filesystem. With the database being a single file, if we can persist that file on the host and make it available to the next container, it should be able to pick up where the last one left off. By creating a volume and attaching it to the directory the data is stored in, we can persist the data. As the container writes to the todo.db file, it will be persisted to the host in the volume.

- As mentioned, we are going to use a named volume. Docker maintains the physical location on the disk and only needs to remember the name of the volume. Every time you the volume is referenced, Docker will make sure the correct data is provided.

- Pushed to [Docker Hub] (https://hub.docker.com/repository/docker/valoryx/to-do-list-app)

- Run with: `docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started`

![image](https://user-images.githubusercontent.com/111099302/205428128-e3103042-ce57-43a2-9a28-34e2edfc64ee.png)

# Created a Notify_Telegram" workflow to send a Telegram message when git repo changes

- 
