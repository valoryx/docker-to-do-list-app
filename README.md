# Created a "To-Do-List" app container with persistent DB access

![image](https://user-images.githubusercontent.com/111099302/205532189-ca6dee80-9c2b-4892-9613-219d433ac96d.png)


- Each container starts from the image definition each time it starts. While containers can create, update, and delete files, those changes are lost when the container is removed and all changes are isolated to that container. 

Docker containers ![image](https://user-images.githubusercontent.com/111099302/205532024-23c7b3f0-7bac-4b2b-8749-f806ecfc569b.png)

- Named volumes provide the ability to connect specific filesystem paths of the container back to the host machine. If a directory in the container is mounted, changes in that directory are also seen on the host machine. If we mount that same directory across container restarts, we’d see the same files.

- By default, the To-Do-List app stores its data in a SQLite Database at /etc/todos/todo.db in the container’s filesystem. With the database being a single file, if we can persist that file on the host and make it available to the next container, it should be able to pick up where the last one left off. 

- By creating a volume and attaching it to the directory the data is stored in, we can persist the data. As the container writes to the todo.db file, it will be persisted to the host in the volume. Docker maintains the physical location on the disk and only needs to remember the name of the volume. Every time you the volume is referenced, Docker will make sure the correct data is provided.

- Pushed to [Docker Hub] (https://hub.docker.com/repository/docker/valoryx/to-do-list-app)

- Run with: `docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started`
- Experience running app at Play with Docker (time sensitive link): http://ip172-18-0-83-ce7955m3tccg00fr10tg-3000.direct.labs.play-with-docker.com/

![image](https://user-images.githubusercontent.com/111099302/205428128-e3103042-ce57-43a2-9a28-34e2edfc64ee.png)

#
# Created a Notify_Telegram" workflow to send a Telegram message when git repo changes 
Ref: (https://github.com/marketplace/actions/telegram-notify)

- yml code: 

![image](https://user-images.githubusercontent.com/111099302/205428389-7548cc61-5041-43de-abd9-990ef65478a0.png)

- workflow dashboard: 

![image](https://user-images.githubusercontent.com/111099302/205428450-ef775399-374b-433f-9c76-685cec93166a.png)

- Telegram chat notifications:

![IMG_EF2172689F7D-1](https://user-images.githubusercontent.com/111099302/205428693-3004d237-3c2f-48e1-ab4b-1bbc9d880fdc.jpeg)

#
# Challenges
- Figuring out how to get Telegram to issue a token so that chats can be received on my Telegram app
- How to configure the Telegram bot
- Adding the Telegram token and ID to git and reference it from the yml code.


