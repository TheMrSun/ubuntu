```
java jdk 环境安装
sudo apt install openjdk-8-jdk

elasticsearch 

1.下载

wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.16.0-amd64.deb 
sudo dpkg -i elasticsearch-7.16.0-amd64.deb

wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.16.0-amd64.deb.sha512 
shasum -a 512 -c elasticsearch-7.16.0-amd64.deb.sha512  

2. 设置开机自启:
sudo /bin/systemctl daemon-reload 
sudo /bin/systemctl enable elasticsearch.service
启动service:
sudo systemctl start elasticsearch.service
验证：
curl -X GET "localhost:9200/"

3. 配置elasticsearch 
sudo gedit /etc/elasticsearch/elasticsearch.yml


#配置es的集群名称，默认是elasticsearch，es会自动发现在同一网段下的es，如果在同一网段下有多个集群，就可以用这个属性来区分不同的集群。
cluster.name: elasticsearch
#节点名称
node.name: hadoop
#设置索引数据的存储路径
path.data: /home/xx/Soft/elasticsearch/data
#设置日志的存储路径
path.logs: /home/xx/Soft/elasticsearch/data
#设置当前的ip地址,通过指定相同网段的其他节点会加入该集群中
network.host: 0.0.0.0
#设置对外服务的http端口
http.port: 9200
cluster.initial_master_nodes: ["node-1"]

4. 权限配置(操作所有文件和文件夹 )
sudo chown -R 用户名:组名称 /etc/elasticsearch/
sudo chown -R 用户名:组名称 /usr/share/elasticsearch/
sudo chown -R 用户名:组名称 /etc/default/elasticsearch
sudo chown -R 用户名:组名称 /var/log/elasticsearch

sudo chown -R 用户名 /home/elasticsearch
./elasticsearch -d
//查看进程
ps aux|grep elasticsearch







```