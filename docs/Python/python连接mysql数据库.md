# 使用Python操作MySQL数据库
MySQL是一种关系型数据库管理系统，它可以用来存储和管理大量的数据。之前介绍了大部分主流数据库，今天将介绍如何使用Python来操作MySQL数据库。
## 安装MySQL
首先，我们需要安装MySQL服务器，可以从MySQL官网下载安装包，也可以使用系统自带的包管理器安装。
## 安装MySQL驱动
接下来，我们需要安装MySQL的驱动，可以使用pip安装：
```
pip install mysql-connector-python
```
## 连接MySQL
接下来，我们需要连接MySQL服务器，可以使用MySQL Connector/Python模块中的connect()函数：
```
import mysql.connector
# 连接MySQL服务器
conn = mysql.connector.connect(
    host="localhost",
    user="root",
    passwd="123456"
)
```
## mysql 指令
| MySQL 指令 | 用法                                                         | 作用             |
| ---------- | ------------------------------------------------------------ | ---------------- |
| SELECT     | SELECT * FROM table_name                                     | 从表中检索数据   |
| INSERT     | INSERT INTO table_name VALUES (value1, value2,...)           | 向表中插入新记录 |
| UPDATE     | UPDATE table_name SET column1=value1, column2=value2,...     | 更新表中的记录   |
| DELETE     | DELETE FROM table_name WHERE condition                       | 从表中删除记录   |
| CREATE     | CREATE TABLE table_name (column1 datatype, column2 datatype,...) | 创建新表         |
| ALTER      | ALTER TABLE table_name ADD column_name datatype              | 向表中添加新列   |
| DROP       | DROP TABLE table_name                                        | 删除表           |
## 创建数据库
接下来，我们可以使用MySQL Connector/Python模块中的cursor()函数创建一个游标，然后使用execute()方法来执行SQL语句：
```
# 创建数据库
cursor = conn.cursor()
cursor.execute("CREATE DATABASE mydb")
```
## 创建表
接下来，我们可以使用MySQL Connector/Python模块中的execute()方法来创建表：
```
# 创建表
cursor.execute("CREATE TABLE users (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255), age INT)")
```
## 插入数据
接下来，我们可以使用MySQL Connector/Python模块中的execute()方法来插入数据：
```
# 插入数据
cursor.execute("INSERT INTO users (name, age) VALUES ('John', 20)")
cursor.execute("INSERT INTO users (name, age) VALUES ('Bob', 25)")
```
## 查询数据
接下来，我们可以使用MySQL Connector/Python模块中的execute()方法来查询数据：
```
# 查询数据
cursor.execute("SELECT * FROM users")
# 获取查询结果
result = cursor.fetchall()
# 打印结果
for row in result:
    print(row)
```
## 更新数据
接下来，我们可以使用MySQL Connector/Python模块中的execute()方法来更新数据：
```
# 更新数据
cursor.execute("UPDATE users SET age = 30 WHERE name = 'John'")
```
## 删除数据
最后，我们可以使用MySQL Connector/Python模块中的execute()方法来删除数据：
```
# 删除数据
cursor.execute("DELETE FROM users WHERE name = 'Bob'")
```
## 结束连接
最后，我们需要使用MySQL Connector/Python模块中的close()方法来结束连接：
```
# 结束连接
conn.close()
```
## 学生管理系统demo
```python
# 导入MySQL驱动
import mysql.connector
# 连接数据库
conn = mysql.connector.connect(host='localhost', user='root', password='123456', database='student_management')
cursor = conn.cursor()
# 管理员登录
def admin_login():
    username = input('请输入管理员账号：')
    password = input('请输入管理员密码：')
    sql = 'select * from admin where username=%!s(MISSING) and password=%!s(MISSING)'
    cursor.execute(sql, (username, password))
    result = cursor.fetchone()
    if result:
        print('登录成功！')
        return True
    else:
        print('登录失败！')
        return False
# 添加学生信息
def add_student():
    stu_no = input('请输入学号：')
    stu_name = input('请输入姓名：')
    stu_age = input('请输入年龄：')
    sql = 'insert into student (stu_no, stu_name, stu_age) values (%!s(MISSING), %!s(MISSING), %!s(MISSING))'
    cursor.execute(sql, (stu_no, stu_name, stu_age))
    conn.commit()
    print('添加学生信息成功！')
# 删除学生信息
def delete_student():
    stu_no = input('请输入要删除的学号：')
    sql = 'delete from student where stu_no=%!s(MISSING)'
    cursor.execute(sql, (stu_no,))
    conn.commit()
    print('删除学生信息成功！')
# 修改学生信息
def update_student():
    stu_no = input('请输入要修改的学号：')
    stu_name = input('请输入新的姓名：')
    stu_age = input('请输入新的年龄：')
    sql = 'update student set stu_name=%!s(MISSING), stu_age=%!s(MISSING) where stu_no=%!s(MISSING)'
    cursor.execute(sql, (stu_name, stu_age, stu_no))
    conn.commit()
    print('修改学生信息成功！')
# 查询学生信息
def query_student():
    stu_no = input('请输入要查询的学号：')
    sql = 'select * from student where stu_no=%!s(MISSING)'
    cursor.execute(sql, (stu_no,))
    result = cursor.fetchone()
    if result:
        print('学号：%!s(MISSING)，姓名：%!s(MISSING)，年龄：%!s(MISSING)' %!((MISSING)result[0], result[1], result[2]))
    else:
        print('查无此人！')
# 主函数
def main():
    if admin_login():
        while True:
            print('1. 添加学生信息')
            print('2. 删除学生信息')
            print('3. 修改学生信息')
            print('4. 查询学生信息')
            print('5. 退出系统')
            choice = input('请输入您的选择：')
            if choice == '1':
                add_student()
            elif choice == '2':
                delete_student()
            elif choice == '3':
                update_student()
            elif choice == '4':
                query_student()
            elif choice == '5':
                break
            else:
                print('输入错误，请重新输入！')
if __name__ == '__main__':
    main()
```
## 结论
本文介绍了如何使用Python来操作MySQL数据库，包括安装MySQL服务器、安装MySQL驱动、连接MySQL、创建数据库、创建表、插入数据、查询数据、更新数据和删除数据等操作。