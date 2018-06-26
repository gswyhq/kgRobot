# kgRobot
## 基于知识图谱的智能问答机器人

## 数据库准备

解压 env/apache jena.rar

gswyhq@gswyhq-PC:~/docker/jena-fuseki$ ls

jena-fuseki_bin  readme.txt  tdb  tdb_drug_new

gswyhq@gswyhq-PC:~/docker/jena-fuseki$ docker run --name jena_3030_tdb_drug_new -p 3030:3030 -e ADMIN_PASSWORD=123456 -it -d -v $PWD:/jena-fuseki/data stain/jena-fuseki:3.6.0 /jena-fuseki/fuseki-server --loc=data/tdb_drug_new /tdb_drug_new

## 启动程序：
gswyhq@gswyhq-PC:~/github_projects/kgRobot/code/KGQA$ docker run -i -t --detach --name=kg_robot_18000 -p 18000:8000 --volume=$PWD:/kg_robot --workdir=/kg_robot -v /etc/localtime:/etc/localtime ubuntu /bin/bash

gswyhq@gswyhq-PC:/$ docker cp /usr/share/zoneinfo/Asia kg_robot_18000:/usr/share/zoneinfo/Asia

gswyhq@gswyhq-PC:/$ docker cp /usr/share/zoneinfo/PRC kg_robot_18000:/usr/share/zoneinfo/Asia/Shanghai

gswyhq@gswyhq-PC:~/github_projects/kgRobot/code/KGQA$ docker exec -it kg_robot_18000 /bin/bash

root@89318fb9634b:/kg_robot# pip3 install -r requirements.txt -i https://pypi.douban.com/simple

root@89318fb9634b:/kg_robot# python3 manage.py runserver 0.0.0.0:8000

## 测试
浏览器打开 http://127.0.0.1:18000/kgqa

### 其他

Jena数据库设置在： code/KGQA/KGQA_Based_On_medicine/settings.py