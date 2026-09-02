# Docker Commands

Here are some sets of Docker commands that can assist you in your day-to-day activities.

- Build an Image with Desired Docker Compose File
```bash
docker-compose -f /data/App/docker-compose-uat.yml up --build
```

- Save Built Image
```bash
docker save -o [Image-Name.tar] [Image Name:latest]
```

- Load Built Image
```bash
docker load -i [Image-Name.tar]
```

- Attach to Container Bash
```bash
Sudo docker exec -it [Container Name] bash
```

- Reload Docker Uwsgi Container
```bash
Sudo docker exec -it [Container Name] uwsgi --reload uwsgi-master.pid
```

- Python Container Shell
```bash
Sudo docker exec -it [Container Name] python manage.py shell
```

- Python Container Migrate
```bash
Sudo docker exec -it [Container Name] python manage.py migrate
```

- Copy a File From a Docker Container
```bash
sudo docker cp [Container Name]:[File Path] [File New Path]
```

- Copy a File To a Docker Container                                                                                                                         ```bash
sudo docker cp [File Name] [Container Name]:[File Path]
```
