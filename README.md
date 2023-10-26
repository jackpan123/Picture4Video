# Picture4Video

### 环境安装
+ Docker安装
  - 安装docker 的Windows版本,下载网址：https://www.docker.com/
+ Milvus安装
  - 采用Milvus版本2.2.9即code/milvus下的docker-compose.yml
  - Milvus可视化管理工具 Attu: https://github.com/zilliztech/attu/blob/main/doc/zh-CN/attu_install-docker.md
+ 项目环境配置
  安装annconda, 后创建python版本为3.8的虚拟环境，之后在该虚拟环境内安装以下包
  - tensorflow-gpu安装及验证
    - conda install cudatoolkit=10.1 cudnn=7.6.5
    - pip install tensorflow-gpu==2.2.0 -i https://pypi.tuna.tsinghua.edu.cn/simple
    - pip install protobuf==3.20.3 -i https://pypi.tuna.tsinghua.edu.cn/simple
    - pip install numpy==1.20.3 -i https://pypi.tuna.tsinghua.edu.cn/simple
    - 验证tensorflow-gpu是否安装成功
      - python
      - import tensorflow as tf
      - tf.config.experimental.list_physical_devices('GPU')
      ![image](安装成功.png)
  - 安装opencv，pip install opencv-python==4.8.0.76 -i https://pypi.tuna.tsinghua.edu.cn/simple
  - 安装av, pip install av==8.0.3 -i https://pypi.tuna.tsinghua.edu.cn/simple
  - 安装pymilvus, 版本要符合跟Milvus版本的对于关系，pip install pymilvus==2.2.9 -i https://pypi.tuna.tsinghua.edu.cn/simple 
  - 安装PyMySQL, pip install PyMySQL==1.1.0 -i https://pypi.tuna.tsinghua.edu.cn/simple

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

### 参考资料
+ [企业级的以图搜图实战——milvus+minio+gradio+resnet(知乎帖子)](https://zhuanlan.zhihu.com/p/591672698)
  - [项目地址](https://github.com/wp931120/picSearch)
+ [milvus官方文档](https://milvus.io/docs)
  - [连接Milvus](https://milvus.io/docs/manage_connection.md)
  - [数据库管理](https://milvus.io/docs/manage_databases.md)
  - [表管理](https://milvus.io/docs/create_collection.md)
  - [数据管理](https://milvus.io/docs/insert_data.md)
  - [创建索引](https://milvus.io/docs/build_index.md)
  - [向量搜索](https://milvus.io/docs/search.md)
+ [视频流编码方法-H264(博客)](https://blog.csdn.net/hello_1995/article/details/122091747)
+ [提取视频关键帧算法：基于H264视频流编码](https://pyav.org/docs/8.0.1/cookbook/basics.html#saving-keyframes)（pyav库）
+ [Python连接MySQL数据库方法介绍(知乎帖子)](https://zhuanlan.zhihu.com/p/79021906)
+ [视频在库检索-哈希编码(博客)](https://blog.csdn.net/weixin_50153843/article/details/131027348)  



  
