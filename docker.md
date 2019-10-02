# Docker seminar:

## Vì sao dùng docker:
- Những vấn đề khi setup môi trường cho dự án (development and deployment).
	- environment giữa development và deployment khác nhau.
	- Setup các môi trường local cho developer mới mất thời gian, khác version, lặp đi lặp lại.
- Docker giải quyết vấn đề gì?
	- Tạo ra một môi trường để application có thể chạy được. Môi trường này chứa các chương trình cần thiết như: web server, database, các packages. 
	- Ưu điểm: dùng được ở linux, window, mac. Các version của chương trình của các môi trường sẽ như nhau, điều đó giảm thiểu khả năng lỗi do khác version. Nhanh chóng setup môi trường cho team để develop(không cần lặp đi lặp lại). 
VD: cho vi du

## Khái niệm căn bản:
#### - Docker là gì:
![alt text](https://www.docker.com/sites/default/files/d8/2018-11/docker-containerized-appliction-blue-border_2.png)
![alt text](https://www.docker.com/sites/default/files/d8/2018-11/container-vm-whatcontainer_2.png)

Docker theo mô hình Containerlization: chia sẽ chung một Host os. 

#### Image và Container:

Docker image là nền tảng của container, có thể hiểu Docker image như khung xương giúp định hình cho container, nó sẽ tạo ra container khi thực hiện câu lệnh chạy image đó. Nếu nói với phong cách lập trình hướng đối tượng, Docker image là class, còn container là thực thể (instance, thể hiện) của class đó.


#### - DockerFile là gì:
- Chức năng:là một file dạng text, không có đuôi, giúp thiết lập cấu trúc cho docker image nhờ chứa một tập hợp các câu lệnh. Từ đó tạo ra docker image.
![alt text](https://github.com/BrianLe1507/docker_docs/blob/master/docker_container.png?raw=true)


#### - Docker-compose là gì:
- Chức năng: là một file .yml dùng để chỉ thị việc tạo ra các images từ một hoặc nhiều file Dockerfile, sau dó nó sẽ kết nối các container tạo từ các image trên với nhau. Việc tạo image và chạy build container được gọi là một service.
```
services:
    webserver:
        .
        .
        .
    mysql:
        image: mysql:5.7 
        container_name: mysql
        restart: always
        environment:
          MYSQL_ROOT_PASSWORD: root
        volumes:
          - docker/database:/var/lib/mysql

```


## Môi trường & hệ sinh thái(tools):
- Docker hub
	- Docker hub là nơi lưu giữ và chia sẻ các file images này (hiện có khoảng 300.000 images)
	- Có thể tưởng tượng nó như github là nơi để lưu trữ source code và quản lý version, Docker hub cho phép lưu trữ nhưng image được build từ máy local, sau đó push lên docker hub để lưu trữ. 

- Docker swarm
- Docker Kubernetes

## Example & Demo:
- Show demo.

## Vấn đề còn bất cập:
- Chậm ở môi trường dev (window and Mac )
- Lý do : Docker cần một Linux kernel để chạy được. Chính vì điều đó mà Mac và Window phải cần một lớp trung gian ở giữa Mac kernel hoặc Window. Điều đó dẫn đến việc chạy docker sẽ chậm ở hai môi trường trên.
- Refs: https://stackoverflow.com/questions/55951014/docker-in-macos-is-very-slow
