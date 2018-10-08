# Dasar Docker 
- image seperi class, container seperti object, container is instance of image  

## show list image
```
docker images
```
## remove all image
```
docker rmi -f $(docker images -q)
```
## convert image to container (instansiasi)
```
docker run <Repo>
```
## menghentikkan container yg running 
```
docker stop <container id>
```
## menjalankan container
```
docker start <container id>
```
## melihat container yg running
```
docker ps
```
## melihat container baik yg running maupun yg tidak 
```
docker ps -a
```
## hapus container 
```
docker rm <container id>
```
## remove all container 
docker rm $(docker ps -a -q)
## masuk kedalam container dan menjalankan perintah linux didalamnya 
```
docker exec -it <namacontainer> bash
```
## masuk ke mysql didalam container
```
docker exec -it <namecontainer> mysql -u root -p
```

# Langkah mengaktifkan image menjadi container
## save image dari server 
```
docker save -o <path for generated tar file> <image name>
```
## load image dari server
```
docker load -i <path to image tar file>
```
## instansiasi image yang sudah loaded menjadi sebuah container
### container mysql
```
docker run --name sample-mysql -e MYSQL_DATABASE=laravel_docker -e MYSQL_USER=iruel -e MYSQL_PASSWORD=iruel -e MYSQL_ROOT_PASSWORD=root -p 13306:3306 -d mysql:5.6

note : db yang baru di instance selalu kosong
```

### instance container laravel sekaligus link ke mysql
```
docker run --name linku --link sample-mysql:mysql -e DB_HOST=mysql -e DB_DATABASE=laravel_docker -e DB_USERNAME=root -e DB_PASSWORD=root -p 8700:80 -d laravel-docker

note : file yang dirubah lalu container di simpan sebagai image, maka perubahan tetap tersimpan
```
