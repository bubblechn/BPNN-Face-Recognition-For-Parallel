# 基于并行BP神经网络的人脸识别系统

此为 **并行版** 的人脸识别系统

并行版请戳：[Github . PAC-P2P/BPNN-Face-Recognition-For-Parallel](https://github.com/PAC-P2P/BPNN-Face-Recognition-For-Parallel)

串行版请戳：[Github . PAC-P2P/BPNN-Face-Recognition](https://github.com/PAC-P2P/BPNN-Face-Recognition)

Qt 版请戳：[Github . PAC-P2P/BPNN-Face-Recognition-For-Qt](https://github.com/PAC-P2P/BPNN-Face-Recognition-For-Qt)

## 安装依赖

### 安装 MPI

	# CentOS
	yum -y install openmpi openmpi-devel
	
	# 添加路径
	export PATH=$PATH:/usr/lib64/openmpi/bin/

### 安装 libcstl 库


	git clone https://github.com/activesys/libcstl.git
	
	cd libcstl
	
	# 配置环境，[指定安装路径]
	./configure [--prefix=newpath] 
	
	# 编译
	make
	
	# 安装
	make install
	
	# 检查
	make check
	
## 编译运行

	git clone https://github.com/PAC-P2P/BPNN-Face-Recognition-For-Parallel.git
	
	cd BPNN-Face-Recognition-For-Parallel
	
	# 解压训练集
	unzip data.zip
	
	cd src
	
	## 编译
	make
	
	# 运行，指定进程数为4
	mpirun -np 4 ./BPNN
	
	# 输入训练次数为100次
	100
	
## 目录结构

	.
	├── README.md
	├── data.zip				# 训练集的图片
	└── src
    	├── Makefile			# Makefile文件
    	├── all_test.list		# 测试集图片路径1
    	├── all_test2.list		# 测试集图片路径2
    	├── all_train.list		# 训练集图片路径
    	├── backprop.c			# 神经网络模块，支持三层全连接前馈神经网络，使用 BP 算法来调整权值
    	├── backprop.h
    	├── config.h			# 人脸识别系统的配置信息
    	├── evaluate.c			# 评估图片集的表现及匹配情况
    	├── evaluate.h
    	├── imagenet.c			# 图片网络模块，用于装载图片到网络的输入单元，和设置训练的目标向量的接口程序
    	├── imagenet.h
    	├── main.c			# 主函数，调用其他模块实现BP神经网络人脸识别整个流程
    	├── parallelModule.c		# 并行模块，使用 MPI 做并行通讯
    	├── parallelModule.h
    	├── pgmimage.c			# 图片处理模块，支持读写 PGM 文件和像素的存取/赋值
    	├── pgmimage.h
    	├── printNet.c			# 打印网络
    	├── printNet.h
    	├── train.c			# 训练模块，BP神经网络的并行训练
    	└── train.h


## 数据集

[Neural Networks for Face Recognition](http://www.cs.cmu.edu/afs/cs.cmu.edu/user/mitchell/ftp/faces.html)
	