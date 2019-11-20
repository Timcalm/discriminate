# 男女语音识别

## 小组信息
小组成员：陆佳豪王琦周传卓

指导老师：王一刚

班级：电信182

学院：信息学院

## 实现男女语音识别计划

在开始语音识别之前，有时需要把首尾端的静音切除，降低对后续步骤造成的干扰，这个静音切除的操作一般称为VAD，需要用到信号处理的一些技术。要对声音进行分析，需要对声音分帧，也就是把声音切开成一小段一小段，每一小段为一帧，分帧操作一般使用移动窗函数来实现，分帧后，语音就变成了很多小段，但波形在时域上几乎没有描述能力，因此必须将波形做变换。常见的一种变化方法是提取MFCC特征，根据人耳的生理特性，把每一帧波形变成一个多维向量，可以简单的理解为这个向量包含了这帧语音的内容信息。这个过程叫做声学特征提取。
## 代码进程    *（随时更新中）*
```
import numpy as np
from scipy.io import wavfile
import matplotlib.pyplot as plt

sampling_freq, audio = wavfile.read(r"C:\Users\Administrator\Desktop\新建文件夹\01-江山此夜.wav")   # 读取文件

audio = audio / np.max(audio)   # 归一化，标准化

# 应用傅里叶变换
fft_signal = np.fft.fft(audio)
print(fft_signal)
fft_signal = abs(fft_signal)
print(fft_signal)
# 建立时间轴
Freq = np.arange(0, len(fft_signal))
# 绘制语音信号的
plt.figure()
plt.plot(Freq, fft_signal, color='blue')
plt.xlabel('Freq (in kHz)')
plt.ylabel('Amplitude')
plt.show()
```
```
from PyQt5 import QtCore, QtGui, QtWidgets
import sys
import tkinter as tk
from tkinter import filedialog

class Ui_tool(object):
    def setupUi(self, tool):
        tool.setObjectName("tool")
        tool.resize(800, 600)
        self.centralwidget = QtWidgets.QWidget(tool)
        self.centralwidget.setObjectName("centralwidget")
        self.pushButton = QtWidgets.QPushButton(self.centralwidget)
        self.pushButton.setGeometry(QtCore.QRect(290, 380, 131, 41))
        self.pushButton.setObjectName("pushButton")
        self.toolButton = QtWidgets.QToolButton(self.centralwidget)
        self.toolButton.setGeometry(QtCore.QRect(230, 40, 291, 61))
        self.toolButton.setIconSize(QtCore.QSize(30, 30))
        self.toolButton.setObjectName("toolButton")
        self.pushButton_2 = QtWidgets.QPushButton(self.centralwidget)
        self.pushButton_2.setGeometry(QtCore.QRect(490, 190, 91, 31))
        self.pushButton_2.setObjectName("pushButton_2")
        self.listWidget = QtWidgets.QListWidget(self.centralwidget)
        self.listWidget.setGeometry(QtCore.QRect(180, 190, 311, 31))
        self.listWidget.setObjectName("listWidget")
        self.pushButton_3 = QtWidgets.QPushButton(self.centralwidget)
        self.pushButton_3.setGeometry(QtCore.QRect(450, 380, 131, 41))
        self.pushButton_3.setObjectName("pushButton_3")
        self.listWidget_2 = QtWidgets.QListWidget(self.centralwidget)
        self.listWidget_2.setGeometry(QtCore.QRect(180, 260, 411, 91))
        self.listWidget_2.setObjectName("listWidget_2")
        tool.setCentralWidget(self.centralwidget)
        self.menubar = QtWidgets.QMenuBar(tool)
        self.menubar.setGeometry(QtCore.QRect(0, 0, 800, 26))
        self.menubar.setObjectName("menubar")
        tool.setMenuBar(self.menubar)
        self.statusbar = QtWidgets.QStatusBar(tool)
        self.statusbar.setObjectName("statusbar")     
        tool.setStatusBar(self.statusbar)
        self.retranslateUi(tool)
        QtCore.QMetaObject.connectSlotsByName(tool)

    def retranslateUi(self, tool):
        _translate = QtCore.QCoreApplication.translate
        tool.setWindowTitle(_translate("tool", "MainWindow"))
        self.pushButton.setText(_translate("tool", "识别"))
        self.toolButton.setText(_translate("tool", "男女声音识别"))
        self.pushButton_2.setText(_translate("tool", "浏览"))
        self.pushButton_3.setText(_translate("tool", "重置"))
        #self.pushButton.clicked.connect(self.on_pushButton_clicked)
        self.pushButton_2.clicked.connect(self.on_pushButton_2_clicked)
        #self.pushButton_3.clicked.connect(self.on_pushButton_3_clicked)

    #def on_pushButton_clicked(self):
    
    
    
    
    
    def on_pushButton_2_clicked(self):
        root = tk.Tk()
        root.withdraw()
        file_path = filedialog.askopenfilename()     

    #def on_pushButton_3_clicked(self):

if __name__ == "__main__":    
    app = QtWidgets.QApplication(sys.argv)  # 创建一个QApplication，也就是你要开发的软件app    
    MainWindow = QtWidgets.QMainWindow()    # 创建一个QMainWindow，用来装载你需要的各种组件、控件    
    ui = Ui_tool()                          # ui是你创建的ui类的实例化对象    
    ui.setupUi(MainWindow)                  # 执行类中的setupUi方法，方法的参数是第二步中创建的QMainWindow    
    MainWindow.show()                       # 执行QMainWindow的show()方法，显示这个QMainWindow    
    sys.exit(app.exec_())  
```

## 遇到的困难
**1.**在使用PyQt5建立窗口时在按钮响应方面出现问题 *（已解决）*
**2.**在使用git与github相连时存在问题，以及在上传时存在更新不了的情况 *（已解决）*
**3.**还未找到有效的男女声音的资开源库
**4.**对声音的采样与利用还在起步过程中
**5.**对声音处理中的杂音还没有进行系统的讨论
**6.**窗口建立的途中图片显示的是连接而不是直接显示

## 窗口图片以及音频导出图片展示
！[窗口](https://raw.githubusercontent.com/Timcalm/discriminate/master/%E7%AA%97%E5%8F%A3.png)
！[傅里叶变换图片](https://raw.githubusercontent.com/Timcalm/discriminate/master/%E5%82%85%E9%87%8C%E5%8F%B6%E5%8F%98%E5%8C%96%E5%9B%BE%E7%89%87.png)

