# 实验一：业务流程建模
|学号|班级|姓名|照片|
|:-------:|:-------------: | :----------:|:---:|
|201510414318|软件(本)15-3|吴江涛|![](./zhourunfa.jpg '描述')

## 1.图书管理系统的用例关系图
### 1.1用例图PlantUML源码如下：
    @startuml
    left to right direction
    Class 借阅者{
    姓名
    性别
    电话
    借书卡号
    身份证号
    图书限额
    已借图书数目
    信誉额度
    queryBook()
    borrowBook()
    returnBook()
    reserveBook()
    renewBook()
    }
    Class 图书管理员{
    姓名
    职工号
    agreeBorrowBook()
    agreeReturnBook()
    fine()
    }
    Class 系统管理员{
    姓名
    职工号
    addBook()
    deleteBook()
    updateBook()
    queryBook()
    addUser()
    deleteUser()
    updateUser()
    queryUser()
    }
    Class 借书记录{
    借书日期
    应还日期
    归还日期
    }
    Class 逾期记录{
    逾期天数
    count()
    }
    Class 罚款细则{
    罚款金额
    fine()
    }
    Class 预订记录{
    借书卡号
    ISBN
    预订日期
    }
    Class 图书书目{
    作者
    ISBN编号
    出版社
    出版日期
    }
    Class 馆藏资源{
    资源名称
    国际出版号
    价格
    简介
    馆藏数量
    可借数量
    }
    Class 资源项{
    馆藏流水号
    状态
    }
    Class 数据存储类{
    query()
    update()
    }
    借阅者 -- 借书记录
    图书管理员 "1" -- "*"借书记录 :登记
    借书记录"1" -- "0..1"逾期记录
    逾期记录"*" -- "0..1"罚款细则:使用
    借书记录 "*" -- "1"数据存储类
    预订记录"*" -- "1"借阅者
    预订记录 "*" -- "1" 数据存储类
    馆藏资源"1" -- "*"预订记录 :被预订
    图书书目 --|> 馆藏资源
    借书记录 -- 资源项
    馆藏资源"1" *-- "*"资源项
    数据存储类 -- 系统管理员
    @enduml
### 1.2 类图如下:
![](./classDraw.png '描述')

## 1.3 类图说明：
### 1.3.1 借阅者
借阅者 类属性有很多，包括姓名、性别、电话、借书卡号、身份证号、图书限额、已借的图书数目、信誉额度等。其主要操作有借书、还书、预约图书等。
### 1.3.2 图书管理员
图书管理员属性有姓名和职工号，其主要操作为对借书、还书进行操作，以及罚款操作。
### 1.3.3 系统管理员
系统管理员属性有姓名和职工号，其主要操作是对图书、借阅者信息进行增删查改操作。
### 1.3.4 图书书目
图书数目是记录书目信息的类，包括作者、ISBN编号、出版社、出版日期等。
### 1.3.5 借书记录
借书记录是某本书的借阅信息类，包括借书日期、应还日期、归还日期。
### 1.3.6 预定记录
预订记录是借阅者对某本书的预订信息类，包括借书卡号、ISBN、预订日期。
### 1.3.7 数据存储类
数据存储类是书籍永久的存储类，在数据库中的存储数据，其它对与书籍有关的活动都要经过其存储类。

## 2.图书管理系统的对象图
### 2.1 借阅者类的对象图源码如下：
    @startuml
    object 借阅者{
        姓名=吴江涛
        性别=男
        电话=139****9575
        借书卡号=201510414318
        身份证号=500235********5573
        图书限额=6
        已借图书=5
        信誉额度=100
    }
    @enduml
#### 2.1.1 对象图如下：
![](./user.png '描述')

## 2.2 图书管理员类的对象图源码如下：
    @startuml
    object 图书管理员{
        姓名=阿来
        职工号=W10151213
    }
    @enduml
#### 2.2.1 对象图如下：
![](./adminObject.png '描述')

### 2.3 系统管理员类的对象图源码如下：
    @startuml
    object 系统管理员{
        姓名:吴涛
        职工号:S12345678
    }
    @enduml
#### 2.3.1 对象图如下：
![](./sysAdmin.png '描述')


### 2.4 图书书目类的对象图源码如下：
    @startuml
    object 图书书目{
        作者=风吹儿
        ISBN=654-7-01-345687-8
        出版社=人民教育出版社
        出版日期=2018
    }
    @enduml
#### 2.4.1 对象图如下：
![](./book.png '描述')


### 2.5 借书记录类的对象图源码如下：
    @startuml
    object 借书记录{
        借书日期=2018-03-15
        应还日期=2018-06-15
        还书日期=2018-04-15
    }
    @enduml
### 2.5.1对象图如下：
![](./borrow.png '描述')

### 2.6 预订记录类的对象图源码如下：
       @startuml
       object 预订记录{
           借书卡号=201510414318
           ISBN=654-7-01-345687-8
           预订日期:2018-04-15
       }
       @enduml
### 2.6.1 对象图如下：
![](./reserve.png '描述')