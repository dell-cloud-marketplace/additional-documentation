# Tips and Tricks

* Remove all images and stopped containers, please do:

```no-highlight
sudo docker rm -f $(docker ps -a -q) ; docker rmi $(docker images -q -a)
```

* Remove all stopped containers, please do:

```no-highlight
sudo docker rm -f $(docker ps -a -q)
```
