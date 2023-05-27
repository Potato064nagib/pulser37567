from PyQt5.QtCore import Qt, QTimer, QTime, QLocale
from PyQt5.QtWidgets import QApplication, QWidget, QLabel, QPushButton, QVBoxLayout, QHBoxLayout, QLineEdit

from instr import *
from final_win import *

class Experiment():
    def __init__(self, age, test1, test2, test3):
        self.age = age
        self.t1 = test1
        self.t2 = test2
        self.t3 = test3

class SecondWin(QWidget):
    def __init__(self):
        super().__init()
        self.set_appear()
        self.initUI()
        self.connects()
        self.show()

    def next_click(self):
        self.hide()
        self.exp = Experiments(int(self.line_age.text()), self.line_test1.text(), self.line_test3.text())
        self.sn = SecondWin(self.exp)

    def set_appear(self):
        self.setWindowTitle(txt_title)
        self.resize(win_width, win_height)
        self.move(win_x, win_y)

    def connects(self):
        self.button_next.clicked.connect(self.next_click)

    def initUI(self):
        self.button_next = QPushButton(txt_sendresults, self)
        self.button_test1 = QPushButton(txt_sendresults1, self)
        self.button_test2 = QPushButton(txt_sendresults2, self)
        self.button_test3 = QPushButton(txt_sendresults3, self)

        self.text_name = QLabel(txt_name)
        self.text_age = QLabel(txt_age)
        self.test1 = QLabel(txt_text)
        self.text2 = QLabel(txt_test)
        self.test3 = QLabel(txt_timer)

        self.line_name = QLineEdit(txt_hintname)
        self.line_age = QLineEdit(txt_hintage)
        self.line_test1 = QLineEdit(txt_hintage1)
        self.line_test2 = QLineEdit(txt_hintage2)
        self.line_test3 = QLineEdit(txt_hintage3)

        self.l_line = QVBoxLayout()
        self.r_line = QVBoxLayout()
        self.h_line = QVBoxLayout()
        self.r_line.addWidget(self.text_timer, alignment = Qt.AlignCenter)
        self.l_line.addWidget(self.text_name, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.line_name, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.text_age, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.line_age, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.text_test1, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.button_test1, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.line_test1, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.text_test2, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.button_test2, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.text_test3, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.button_test3, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.line_test2, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.line_test3, alignment = Qt.AlignLeft)
        self.l_line.addWidget(self.button_next, alignment = Qt.AlignLeft)

    def timer_test(self):
        global time
        time = QTime(0,0,15)
        self.timer = QTimer()
        self.timer.timeout.connect(self.timerEvent)
        self.timer.start(1000)

    def timer_sist(self):
        global time
        time = QTime(0,0,30)
        self.timer = QTimer()
        self.timer.timeout.connect(self.timer2Event)
        self.timer.start(1500)

    def timer_final(self):
        global time
        self.timer = QTimer()
        self.timer.timeout.connect(self.timer3Event)
        self.timer.start(1000)

    def timer1Event(self):
        global time
        time = time.addSecs(-1)
        self.text_timer.setText(time.toString('hh:mm:ss'))
        self.text_timer.setFont(QFont('Times', 36, QFont.Bold))
        self.text_timer.setStyleSheet('color: rgb(0,0,0)')
        if time.toString('hh:mm:ss') == '00:00:00':
            self.timer.stop()

    def timer2Event(self):
        global time
        time = time.addSecs(-1)
        self.text_timer.setText(time.toString('hh:mm:ss')[6:8])
        self.text_timer.setFont(QFont('Times', 36, QFont.Bold))
        self.text_timer.setStyleSheet('color: rgb(0,0,0)')
        if time.toString('hh:mm:ss') == '00:00:00':
            self.timer.stop()

    def timer3Event(self):
        global time
        time = time.addSecs(-1)
        self.text_timer.setText(time.toString('hh:mm:ss'))
        if int(time.toString('hh:mm:ss')[6:8]) >= 45:
            self/text_timer.setStyleSheet('color: rgb(0,255,0')
        elif int(time.toString('hh:mm:ss')[6:8]) <= 15:
            self.text_timer.setStyleSheet('color: rgb(0,255,0')
        else:
            self.text_timer.setStyleSheet('color: rgb(0,0,0)')
        self.text_timer.setFont(QFont('Times', 36, QFont.Bold))
        if time.toString('hh:mm:ss' == "00:00:00"):
            self.timer.stop()


    def connects(self):
        self.button.clicked.connect(self.next_click)
        self.button_test1.clicked.connect(self.timer_test)
        self.button_test2.clicked.connect(self.timer_sits)
        self.button_test3.clicked.connect(self.timer_final)

    def next_click(self):
        self.hide()
        self.fw = FinalWin()

    def set_appear(self):
        self.setWindowTitle(txt_title)
        self.resize(win_width, win_height)
        self.move(win_x, win_y)

app = QApplication([])
sn = SecondWin()
app.exec_()
