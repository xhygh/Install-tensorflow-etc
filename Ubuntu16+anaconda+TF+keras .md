# 1. 安装ubuntu16.04系统
	目录 |建议大小             |格式
  -----|--------------------|------
	/  	 |20G不够用，最好30G	 |ext4逻辑分区
	/boot|200M不够用，给1G		  |ext4
	/tmp |5G					        |ext4
	swap |内存的2倍			       |swap交换分区
	/home|存的文件都在这里	    |ext4
	
	安装启动引导器的设备选择和/boot的盘符，例如/dev/sda7
	
	时区：上海
  
	键盘：英语（美国）
	
	开机黑屏问题error:file /grub/i386-pc/normal.mod not found
  
	http://blog.sina.com.cn/s/blog_7deb436e0101nzkq.html
	
-------------------------
# 2. 安装openssh
	sudo apt-get install openssh-server
------------------------------------------
# 3. sudo apt-get install gdebi  //用于安装deb程序

  使用方法：
  
    [sudo] gdebi xxxx.deb
    
# 4. 安装teamviewer（打到目录下）
	sudo gdebi team......
-----------------------------
# 5. 安装anoconda2.7（打到目录下）

	bash Anaconda2-4.2.0-Linux-x86_64.sh
  
	在询问是否把anaconda的bin目录添加到PATH变量时，选择yes. 
  然后让配置文件重新生效：
	$source ~/.bashrc
	
  
	如果没来得及选yes
	终端输入gedit /home/主机名/.bashrc，在最后一行贴上 export……就是人家提示的那个，不要$
	$source ~/.bashrc
	
	打开python看看是不是anaconda
-----------------------------------------
# 6. 使用anoconda安装tensorflow，keras
	```
  //anaconda创建虚拟环境
  # Python 2.7
	$ conda create -n tensorflow python=2.7
  
	//启动虚拟环境
	$ source activate tensorflow
	(tensorflow)$  # Your prompt should change
	//使用conda安装cpu版本tensorflow
	# Linux/Mac OS X, Python 2.7/3.4/3.5, CPU only:
	(tensorflow)$ conda install -c conda-forge tensorflow
	```
	
	## 使用pip安装TF cpu版本
  ```
	# Ubuntu/Linux 64-bit, CPU only, Python 2.7(建议到官网找最新版)
	(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.12.0rc1-cp27-none-linux_x86_64.whl

	# Ubuntu/Linux 64-bit, GPU enabled, Python 2.7
	# Requires CUDA toolkit 8.0 and CuDNN v5. For other versions, see "Installing from sources" below.
	(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-0.12.0rc1-cp27-none-linux_x86_64.whl

	++++++++++++++++++++++++++++++++++++++++++++++++++
	# Ubuntu/Linux 64-bit, CPU only, Python 3.4
	(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.12.0rc1-cp34-cp34m-linux_x86_64.whl

	# Ubuntu/Linux 64-bit, GPU enabled, Python 3.4
	# Requires CUDA toolkit 8.0 and CuDNN v5. For other versions, see "Installing from sources" below.
	(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-0.12.0rc1-cp34-cp34m-linux_x86_64.whl

	+++++++++++++++++++++++++++++++++++++++++++++++++++
	# Ubuntu/Linux 64-bit, CPU only, Python 3.5
	(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.12.0rc1-cp35-cp35m-linux_x86_64.whl

	# Ubuntu/Linux 64-bit, GPU enabled, Python 3.5
	# Requires CUDA toolkit 8.0 and CuDNN v5. For other versions, see "Installing from sources" below.
	(tensorflow)$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-0.12.0rc1-cp35-cp35m-linux_x86_64.whl
  ```
  ```
	# Python 2 (更新tf版本也是这么做，先export TF_BINARY_URL，在如下操作)
	(tensorflow)$ pip install --ignore-installed --upgrade $TF_BINARY_URL

	# Python 3
	(tensorflow)$ pip3 install --ignore-installed --upgrade $TF_BINARY_URL
	```
-------------------------------------------
# 7.安装keras等库
  ```
	(tensorflow)$pip install keras matplotlib h5py
 	(tensorflow)$pip install -U scikit-learn
  ```
----------------------------------------------	
# 注意：退出虚拟环境
  ```
	(tensorflow)$ source deactivate  //安装虚拟环境的包需要在虚拟环境下，运行程序也是
	```
	
	
/*****************************************************************************************************/
# 安装virtualenv,创建虚拟环境
```
pip install virtualenv
```

创建虚拟环境：
  ```
	virtualenv [虚拟环境名字]
	例如：virtualenv env-py27
  ```
	
删除虚拟环境只需要删除它的文件夹：
  ```
	rm -rf env-py27
	```
启动虚拟环境：
	进入到虚拟环境文件夹下cd env-py27
  ```
	source bin/activate
	或者source env-py27/bin/activate
  ```
退出虚拟环境：
  ```
	deactivate
  ```
