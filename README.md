# 0001_Qt_InStruction
关于Qt使用常见的问题及知识点汇总

Git仓库地址：
https://github.com/CodingManPP/0001_Qt_BasicUnderstanding
【常用代码】
greaterThan(QT_MAJOR_VERSION,4):QT += widgets


Qt
1.静态编译、动态编译，
2.QApplication 对象的作用？
管理应用程序的资源，任何一个QtWidgets程序都要有一个QApplication对象。
3.写出使用hellodialog.ui生成对应头文件的命令

4.前置声明的作用：加快编译速度，避免在头文件中随意包含其他头文件而产生错误

5.使用多继承出现的问题

6.常见的基类：QMainWindow、QWidget、QDialog

7.模态对话框、非模态对话框。分别写出模态对话框实现的两种方式。
//【1】定义模态对话框，定义方式1,开始显示Dialog，不显示MyWidget；关闭Dialog之后，才显示MyWidget
    QDialog dialog3(this);
    dialog3.exec();

 //【2】定义模态对话框，定义方式2，Dialog和MyWidget一起显示，开始只能操作Dialog，不能操作MyWidget；只有关闭Dialog之后，才可以操作MyWidget
    QDialog *dialog3 = new QDialog(this);
    dialog3->setModal(true);
    dialog3->show();  

//【3】setWindowModality(Qt::WindowModal)（阻塞父窗口及所有的祖先窗口和他们的子窗口）
    QDialog *dialog5 = new QDialog(this);
    dialog5->setWindowModality(Qt::WindowModal);
    dialog5->show();

//【4】setWindowModality(Qt::ApplicationModal)（阻塞所有窗口）
    QDialog *dialog5 = new QDialog(this);
    dialog5->setWindowModality(Qt::ApplicationModal);
    dialog5->show();

8.分裂器QSplitter与QBoxLayout的区别？
答：【相同点】分裂器QSplitter与QBoxLayout类似，可以完成布局管理器的工。
【不同点】
【1】包含在里面的控件默认是可以随着分裂器的大小变化而变化。
【2】分裂器QSplitter继承自QWidget类，而QBoxLayout继承自QFrame类。



8.写出两种关联信号和槽的方法。
【方法1】直接在设计器中进行关联。
【方法2】在设计器中直接进入到相关信号的槽，用的是自动关联，在.h文件中会自动添加该槽的声明，只需要更改代码即可。

================
【常见bug】
【bug1】--没有处理！！！
H:\002_QT\003_Qt\0001_Qt_BasicUnderstanding\_005_HelloWorld_c++\HelloWorld\hellodialog.cpp:20: 
error: undefined reference to `vtable for HelloDialog'
【原因】使用 Q_OBJECT 有问题
【参考】使用Qt5.7.1 之后没有修改什么问题，然后就可以运行了。
