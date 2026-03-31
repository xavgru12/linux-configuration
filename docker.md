Install docker:
https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

execute these:
sudo usermod -aG docker <your_user>
sudo chmod 666 /var/run/docker.sock

sudo nano /etc/docker/daemon.json with this content:
{
  "default-ulimits": {
    "nofile": {
      "Name": "nofile",
      "Hard": 65535,
      "Soft": 65535
    }
  }
}

sudo systemctl restart docker

