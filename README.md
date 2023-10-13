# Picture4Video

### 环境安装
+ Docker安装
  - 安装docker 的Windows版本,下载网址：https://www.docker.com/
+ Milvus安装
  - 采用Milvus版本2.2.9即code/milvus下的docker-compose.yml
  - Milvus可视化管理工具 Attu: https://github.com/zilliztech/attu/blob/main/doc/zh-CN/attu_install-docker.md
+ 项目环境配置
  安装annconda，后创建python版本为3.8的虚拟环境，之后在该虚拟环境内安装以下包
  - 安装tensorflow-gpu==2.2.0
  - 安装opencv，pip install opencv-python==4.8.0.76
  - 安装av， pip install av==8.0.3
  - 安装pymilvus，版本要符合跟Milvus版本的对于关系，pip install pymilvus==2.2.9 
  - 安装PyMySQL，pip install PyMySQL==1.1.0  

### 项目结构
+ code/model存放模型权重
+ code/milvus/docker-compose.yml存放Milvus信息
+ code/Crawer_Video存放待提取关键帧的视频
+ code/pics存放待检索的的图片
+ code/utils包存放使用到的工具类
+ code/Frames 存放所有视频的关键帧（该文件夹会自动生成）
+ code/Add.py 调用add_videos2milvus方法增量更新视频，将增量视频的关键帧特征向量存储至Milvus数据库中。
+ code/Add2Milvus.py 提取视频关键帧，并将其保存在Frames文件夹中。读取视频关键帧并将其转换成特征向量，传入Milvus数据库中存储。
+ code/Search.py 调用SearchVideoByOnePic方法进行以1张图片搜视频。
+ code/Delete.py 调用delete_frame_by_v_id方法根据视频id列表删除Milvus数据库中相应的视频的关键帧的特征向量。


  



  

