## 男女语音识别

小组成员：陆佳豪王琦周传卓

指导老师：王一刚

班级：电信182

学院：信息学院

## 实现男女语音识别计划

在开始语音识别之前，有时需要把首尾端的静音切除，降低对后续步骤造成的干扰，这个静音切除的操作一般称为VAD，需要用到信号处理的一些技术。要对声音进行分析，需要对声音分帧，也就是把声音切开成一小段一小段，每一小段为一帧，分帧操作一般使用移动窗函数来实现，分帧后，语音就变成了很多小段，但波形在时域上几乎没有描述能力，因此必须将波形做变换。常见的一种变化方法是提取MFCC特征，根据人耳的生理特性，把每一帧波形变成一个多维向量，可以简单的理解为这个向量包含了这帧语音的内容信息。这个过程叫做声学特征提取。
## 代码进程  *随时更新中*
```
# -*- coding: utf-8 -*-

# Form implementation generated from reading ui file 'tool.ui'
#
# Created by: PyQt5 UI code generator 5.13.0
#
# WARNING! All changes made in this file will be lost!


from PyQt5 import QtCore, QtGui, QtWidgets
import sys

class Ui_tool(object):
    def setupUi(self, tool):
        tool.setObjectName("tool")
        tool.resize(800, 600)
        self.centralwidget = QtWidgets.QWidget(tool)
        self.centralwidget.setObjectName("centralwidget")
        self.pushButton = QtWidgets.QPushButton(self.centralwidget)
        self.pushButton.setGeometry(QtCore.QRect(290, 380, 131, 41))
        self.pushButton.setObjectName("pushButton")
        self.toolButton = QtWidgets.QToolButton(self.centralwidget)
        self.toolButton.setGeometry(QtCore.QRect(230, 40, 291, 61))
        self.toolButton.setIconSize(QtCore.QSize(30, 30))
        self.toolButton.setObjectName("toolButton")
        self.pushButton_2 = QtWidgets.QPushButton(self.centralwidget)
        self.pushButton_2.setGeometry(QtCore.QRect(490, 190, 91, 31))
        self.pushButton_2.setObjectName("pushButton_2")
        self.listWidget = QtWidgets.QListWidget(self.centralwidget)
        self.listWidget.setGeometry(QtCore.QRect(180, 190, 311, 31))
        self.listWidget.setObjectName("listWidget")
        self.pushButton_3 = QtWidgets.QPushButton(self.centralwidget)
        self.pushButton_3.setGeometry(QtCore.QRect(450, 380, 131, 41))
        self.pushButton_3.setObjectName("pushButton_3")
        self.listWidget_2 = QtWidgets.QListWidget(self.centralwidget)
        self.listWidget_2.setGeometry(QtCore.QRect(180, 260, 411, 91))
        self.listWidget_2.setObjectName("listWidget_2")
        tool.setCentralWidget(self.centralwidget)
        self.menubar = QtWidgets.QMenuBar(tool)
        self.menubar.setGeometry(QtCore.QRect(0, 0, 800, 26))
        self.menubar.setObjectName("menubar")
        tool.setMenuBar(self.menubar)
        self.statusbar = QtWidgets.QStatusBar(tool)
        self.statusbar.setObjectName("statusbar")
        tool.setStatusBar(self.statusbar)

        self.retranslateUi(tool)
        QtCore.QMetaObject.connectSlotsByName(tool)

    def retranslateUi(self, tool):
        _translate = QtCore.QCoreApplication.translate
        tool.setWindowTitle(_translate("tool", "MainWindow"))
        self.pushButton.setText(_translate("tool", "识别"))
        self.toolButton.setText(_translate("tool", "男女声音识别"))
        self.pushButton_2.setText(_translate("tool", "浏览"))
        self.pushButton_3.setText(_translate("tool", "重置"))
    


if __name__ == "__main__":    
    app = QtWidgets.QApplication(sys.argv)  # 创建一个QApplication，也就是你要开发的软件app    
    MainWindow = QtWidgets.QMainWindow()    # 创建一个QMainWindow，用来装载你需要的各种组件、控件    
    ui = Ui_tool()                          # ui是你创建的ui类的实例化对象    
    ui.setupUi(MainWindow)                  # 执行类中的setupUi方法，方法的参数是第二步中创建的QMainWindow    
    MainWindow.show()                       # 执行QMainWindow的show()方法，显示这个QMainWindow    
    sys.exit(app.exec_())  
```