## API_ML_AI
## 产品需求文档

发布日期 | 2018/11
---|---
Epic | 卡路里助手
文件现状|未完成
文件主人 |孙思盼
领头设计者 |孙思盼
领头开发者 |孙思盼
领头测试者|孙思盼

####  Goals: 目标


1. 拍摄图片获取食物的相关卡路里和营养信息。


# 第一部分：需求概述
#### 背景概述
&emsp;&emsp;近几年，出现大量智能手机app为核心的记录饮食产品，用户通过app来记录每天的摄入，但是研究发现，目前市面上存在的该类型app，用户需要记录该食物是哪一天吃的，哪一餐吃的，吃的是什么食物，吃了多少。繁琐的操作使得用户需要花费一定的时间去对每天摄入的食物进行记录，久而久之会选择放弃。


#### 产品介绍
这是一款可以自动记录食物热量和营养信息的小程序。产品减少用户在记录每天饮食摄入时需要进行的一些繁琐操作，用户通过智能手机拍摄食物的图片上传，系统将会通过深度学习的算法，结合视觉分析和图像识别技术，反馈给用户相关的食物信息，包括热量和具体的营养成分，从而更好的做到为用户分析日常饮食的健康指标，拟定出个人定制化的减肥计划。

####  用户痛点、需求
食物繁琐的输入，花费了用户一定的时间；
比如：（场景）在只有30分钟的用餐时间，用户需要花一定时间在记录饮食上，甚至还要细致到每一种食物的具体重量，这样不仅耗时耗力，产生的结果也仅仅只是参考的作用。

####  用户群体

用户 | 场景需求| 量级
---|---|---
职场女性 |吃饭时间，快速记录当天食物的信息| 重要
在校大学生|建立完整的饮食档案，避免繁琐的输入| 重要
家庭妇女|繁杂的家务结束后，享用吃饭时间，同时想记录自己的饮食档案| 重要
...|.....|...

#### 用户收获
在任何场合，用户都可以快速通过拍摄图片来获取食物的相关卡路里和营养信息，不需要繁琐的输入操作。




#### 这如何和我的产品整体策略发生关联？
&emsp;&emsp;产品的目标策略提出，解决了繁琐的输入操作，为用户带来全新的操作体验。同时产品以小程序的形式进行设定，也是基于目前市面上大量同质化app占据了一定的市场比例，但是能在这场战役中真正脱颖而出的app却是少之又少，因此小程序的推广可能能更好的让用户产生愿意尝试一下的心理。



# 第二部分 产品规划
#### 假设（Assumptions:） 

1. 用户拍摄图片，主要是在使用移动智能手机的情境下；
2. 图片中食物的能量获取调用有关的食物卡路里api，支持低分辨率的图片；
3. 技术：深度学习的算法，结合视觉分析和图像识别；
4. 需要依靠有强大的数据库来判断获取食物的热量信息。

#### 需求 requirements:
| | title| 用户案例 |重要程度|笔记 |
| ------ | ------ | ------ |------ |------ |
| 1| 拍摄功能|  用户给食物拍照，系统自动计算热量|重要：免去了繁琐的输入|------ |
| 2 | 搜索功能|用户通过输入、扫描条形码查找食物|次重要|

#### 预期输入-输出：
问题（question）| 结果（outcome）
---|---
 输入食物照片|输出食物相关的热量和营养含量|




#### 百度AI菜品识别-图片输入输出/可行性分析（前期尝试）
- api:调用百度菜品识别api

案例1：
- 输入：牛肉河粉
- 输出：牛肉粉，置信度为0.866
- 判断：正确
- 检测时间：约3秒
![](https://github.com/sunsipan/API_ML_AI/blob/master/images/2.png)

案例2
- 输入：多种食物
- 输出：非菜
- 判断：无法识别
- 时间：小于2秒
![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/1.png)

##### 代码测试
![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/python.jpg)

结果：代码测试，出现了110错误，accent token无效；目前还没有解决。

#### 总结：
百度菜色API，只能识别单一的菜色，对于多食物的照片无法识别；提供食物的热量信息，并没有提供更为具体的营养含量。
思考：怎么解决多菜色的照片，同时提供更为具体的营养信息。

##### [代码测试（第二次）](https://github.com/sunsipan/API_ML_AI/blob/master/API-test.ipynb)
![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/API-test.JPG)


#### API的二次尝试
- https://world.openfoodfacts.org/data

（待续）




# 第三部分 产品设计

### 产品信息结构图（初期）：
![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/ISD.png)

### 产品功能结构图（初期）：
![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/PFD.png)

### 原型-部分功能说明（初期）
##### 1. 弹窗-授权微信登陆

![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/wetchat.png)




##### 2.关于卡路里小程序相关信息
![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/about.png)



##### 3.拍照页面-核心
![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/photo.png)


##### 4.卡路里用户数据页面-用于分享
![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/userdata.png)


##### 5.图片扫描后输出的结果
![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/outcome.png)


##### 6.搜索页面
![image](https://github.com/sunsipan/API_ML_AI/blob/master/images/search.png)

#### Not doing

- 语音识别：用户直接通过语音询问得到食物在百科上的相关回答；

- 高级版：通过注册后，用户可以根据个人需求考虑是否升级，升级后可以体验到更多附加功能。群体目标，比如国家运动员、私人教练







