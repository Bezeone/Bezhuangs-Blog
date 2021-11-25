---
title: 使用Python程序画画
date: 2021-06-01
updated: 2021-06-01
tags: [Python]
categories: 编程与开发
references:
  - title: Posts from Ankur Gajurel
    url: https://copyassignment.com/author/ankur/
---

> turtle 库是 Python 的标准库之一，属于入门级的图形绘制函数库，其原理是让一只海龟在画布上游走，走过的轨迹形成了绘制的图形，海龟由程序控制，可以自由改变颜色、方向宽度等。我们也可以依赖这个库完成一些简单的画画，以下为一些经典图像的代码实现笔记，可供参考。

<!--more-->

### turtle 简介

```python
import turtle
# 设置窗体大小
turtle.setup(width,height,startx,starty)    #后两个参数非必选参数
#turtle的移动
turtle.goto(x,y)
#画圆
turtle.circle(r,angle)
#当前距离后退
turtle.bk(d)
#当前距离前进
turtle.fd(d)    #turtle.forward(d)
#改变海龟行进方向，angle为绝对角度
turtle.seth(angle)    #只改变呢方向不行进
#向左右前进
turtle.right(angle)
turtle.left(angle)
#抬起画笔
turtle.pu()    #turtle.penup()
#画笔落下
turtle.pd()    #turtle.pendown()
#画笔宽度
turtle.width(width)    #turtle.pensize(width)
#画笔颜色
turtle.pencolor(color):color
```

### 画笑脸

```python
import turtle as fucksisu
def eye(col, rad):
	fucksisu.down()
	fucksisu.fillcolor(col)
	fucksisu.begin_fill()
	fucksisu.circle(rad)
	fucksisu.end_fill()
	fucksisu.up()
fucksisu.fillcolor('yellow')
fucksisu.begin_fill()
fucksisu.circle(100)
fucksisu.end_fill()
fucksisu.up()
fucksisu.goto(-40, 120)
eye('white', 15)
fucksisu.goto(-37, 125)
eye('black', 5)
fucksisu.goto(40, 120)
eye('white', 15)
fucksisu.goto(40, 125)
eye('black', 5)
fucksisu.goto(0, 75)
eye('black', 8)
fucksisu.goto(-40, 85)
fucksisu.down()
fucksisu.right(90)
fucksisu.circle(40, 180)
fucksisu.up()
fucksisu.goto(-10, 45)
fucksisu.down()
fucksisu.right(180)
fucksisu.fillcolor('red')
fucksisu.begin_fill()
fucksisu.circle(10, 180)
fucksisu.end_fill()
fucksisu.hideturtle()
```

### 画柱状图

```python
import turtle
turtle.title("柱状图名称")
heights = [834, 620,460,260,105]
def main():
    t = turtle.Turtle()
    t.hideturtle()
    for i in range(5):
        drawFilledRectangle(t,-200+(76*i),0,76,heights[i]/4,"black","light blue")
    displayText(t)
def drawFilledRectangle(t,x,y,w,h,colorP="black",colorF="white"):
    t.pencolor(colorP)
    t.fillcolor(colorF)
    t.up()
    t.goto(x,y)
    t.down()
    t.begin_fill()
    t.goto(x+w,y)
    t.goto(x+w,y+h)
    t.goto(x,y+h)
    t.goto(x,y)
    t.end_fill()
def displayText(t):
    languages = ["柱状图1", "柱状图2", "柱状图3", "柱状图4", "柱状图5"]
    t.pencolor("blue")
    t.up()
    for i in range(5):
        t.goto((-162+76*i),heights[i] / 4)
        t.write(str(heights[i]),align="center",font=("Arial",10,"normal"))
        t.goto((-162+76*i),10)
        t.write(languages[i],align="center",font=("Arial",10,"normal"))
        t.goto(-200,-25)
        t.write("柱状图1名称",font=("Arial",10,"normal"))
        t.goto(-200,-45)
        t.write('(柱状图1注解)',font=("Arial",10,"normal"))
main()
```

### 画皮卡丘

```python
import turtle
def sisuisrubbishl(x, y):
    turtle.setx(x)
    turtle.sety(y)
    print(x, y)
class Cartoon:
    def __init__(self):
        self.t = turtle.Turtle()
        t = self.t
        t.pensize(3)
        t.speed(9)
        t.ondrag(sisuisrubbishl)
    def meme(self, x, y):
        self.t.penup()
        self.t.goto(x, y)
        self.t.pendown()
    def ihatesisu1(self, x, y):
        self.meme(x, y)
        t = self.t
        t.seth(0)
        t.fillcolor('#333333')
        t.begin_fill()
        t.circle(22)
        t.end_fill()
        self.meme(x, y + 10)
        t.fillcolor('#000000')
        t.begin_fill()
        t.circle(10)
        t.end_fill()
        self.meme(x + 6, y + 22)
        t.fillcolor('#ffffff')
        t.begin_fill()
        t.circle(10)
        t.end_fill()
    def ihatesisu2(self, x, y):
        self.meme(x, y)
        t = self.t
        t.seth(0)
        t.fillcolor('#333333')
        t.begin_fill()
        t.circle(22)
        t.end_fill()
        self.meme(x, y + 10)
        t.fillcolor('#000000')
        t.begin_fill()
        t.circle(10)
        t.end_fill()
        self.meme(x - 6, y + 22)
        t.fillcolor('#ffffff')
        t.begin_fill()
        t.circle(10)
        t.end_fill()
    def fucksisu(self, x, y):
        self.meme(x, y)
        t = self.t
        t.fillcolor('#88141D')
        t.begin_fill()
        l1 = []
        l2 = []
        t.seth(190)
        a = 0.7
        for i in range(28):
            a += 0.1
            t.right(3)
            t.fd(a)
            l1.append(t.position())
        self.meme(x, y)
        t.seth(10)
        a = 0.7
        for i in range(28):
            a += 0.1
            t.left(3)
            t.fd(a)
            l2.append(t.position())
        t.seth(10)
        t.circle(50, 15)
        t.left(180)
        t.circle(-50, 15)
        t.circle(-50, 40)
        t.seth(233)
        t.circle(-50, 55)
        t.left(180)
        t.circle(50, 12.1)
        t.end_fill()
        self.meme(17, 54)
        t.fillcolor('#DD716F')
        t.begin_fill()
        t.seth(145)
        t.circle(40, 86)
        t.penup()
        for pos in reversed(l1[:20]):
            t.goto(pos[0], pos[1] + 1.5)
        for pos in l2[:20]:
            t.goto(pos[0], pos[1] + 1.5)
        t.pendown()
        t.end_fill()
        self.meme(-17, 94)
        t.seth(8)
        t.fd(4)
        t.back(8)
    def fucksisu4(self, x, y):
        turtle.tracer(False)
        t = self.t
        self.meme(x, y)
        t.seth(300)
        t.fillcolor('#DD4D28')
        t.begin_fill()
        a = 2.3
        for i in range(120):
            if 0 <= i < 30 or 60 <= i < 90:
                a -= 0.05
                t.lt(3)
                t.fd(a)
            else:
                a += 0.05
                t.lt(3)
                t.fd(a)
        t.end_fill()
        turtle.tracer(True)
    def fucksisu5(self, x, y):
        t = self.t
        turtle.tracer(False)
        self.meme(x, y)
        t.seth(60)
        t.fillcolor('#DD4D28')
        t.begin_fill()
        a = 2.3
        for i in range(120):
            if 0 <= i < 30 or 60 <= i < 90:
                a -= 0.05
                t.lt(3)
                t.fd(a)
            else:
                a += 0.05
                t.lt(3)
                t.fd(a)
        t.end_fill()
        turtle.tracer(True)
    def fucksisu6(self, x, y):
        t = self.t
        self.meme(x, y)
        t.fillcolor('#000000')
        t.begin_fill()
        t.seth(330)
        t.circle(100, 35)
        t.seth(219)
        t.circle(-300, 19)
        t.seth(110)
        t.circle(-30, 50)
        t.circle(-300, 10)
        t.end_fill()
    def fucksisu7(self, x, y):
        t = self.t
        self.meme(x, y)
        t.fillcolor('#000000')
        t.begin_fill()
        t.seth(300)
        t.circle(-100, 30)
        t.seth(35)
        t.circle(300, 15)
        t.circle(30, 50)
        t.seth(190)
        t.circle(300, 17)
        t.end_fill()
    def fucksisu8(self):
        t = self.t
        t.fillcolor('#F6D02F')
        t.begin_fill()
        t.penup()
        t.circle(130, 40)
        t.pendown()
        t.circle(100, 105)
        t.left(180)
        t.circle(-100, 5)
        t.seth(20)
        t.circle(300, 30)
        t.circle(30, 50)
        t.seth(190)
        t.circle(300, 36)
        t.seth(150)
        t.circle(150, 70)
        t.seth(200)
        t.circle(300, 40)
        t.circle(30, 50)
        t.seth(20)
        t.circle(300, 35) 
        t.seth(240)
        t.circle(105, 95)
        t.left(180)
        t.circle(-105, 5)
        t.seth(210)
        t.circle(500, 18)
        t.seth(200)
        t.fd(10)
        t.seth(280)
        t.fd(7)
        t.seth(210)
        t.fd(10)
        t.seth(300)
        t.circle(10, 80)
        t.seth(220)
        t.fd(10)
        t.seth(300)
        t.circle(10, 80)
        t.seth(240)
        t.fd(12)
        t.seth(0)
        t.fd(13)
        t.seth(240)
        t.circle(10, 70)
        t.seth(10)
        t.circle(10, 70)
        t.seth(10)
        t.circle(300, 18)
        t.seth(75)
        t.circle(500, 8)
        t.left(180)
        t.circle(-500, 15)
        t.seth(250)
        t.circle(100, 65)
        t.seth(320)
        t.circle(100, 5)
        t.left(180)
        t.circle(-100, 5)
        t.seth(220)
        t.circle(200, 20)
        t.circle(20, 70)
        t.seth(60)
        t.circle(-100, 20)
        t.left(180)
        t.circle(100, 20)
        t.seth(300)
        t.circle(10, 70)
        t.seth(60)
        t.circle(-100, 20)
        t.left(180)
        t.circle(100, 20)
        t.seth(10)
        t.circle(100, 60)
        t.seth(180)
        t.circle(-100, 10)
        t.left(180)
        t.circle(100, 10)
        t.seth(5)
        t.circle(100, 10)
        t.circle(-100, 40)
        t.circle(100, 35)
        t.left(180)
        t.circle(-100, 10)
        t.seth(290)
        t.circle(100, 55)
        t.circle(10, 50)
        t.seth(120)
        t.circle(100, 20)
        t.left(180)
        t.circle(-100, 20)
        t.seth(0)
        t.circle(10, 50)
        t.seth(110)
        t.circle(100, 20)
        t.left(180)
        t.circle(-100, 20)
        t.seth(30)
        t.circle(20, 50)
        t.seth(100)
        t.circle(100, 40)
        t.seth(200)
        t.circle(-100, 5)
        t.left(180)
        t.circle(100, 5)
        t.left(30)
        t.circle(100, 75)
        t.right(15)
        t.circle(-300, 21)
        t.left(180)
        t.circle(300, 3)
        t.seth(43)
        t.circle(200, 60)
        t.right(10)
        t.fd(10)
        t.circle(5, 160)
        t.seth(90)
        t.circle(5, 160)
        t.seth(90)
        t.fd(10)
        t.seth(90)
        t.circle(5, 180)
        t.fd(10)
        t.left(180)
        t.left(20)
        t.fd(10)
        t.circle(5, 170)
        t.fd(10)
        t.seth(240)
        t.circle(50, 30)
        t.end_fill()
        self.meme(130, 125)
        t.seth(-20)
        t.fd(5)
        t.circle(-5, 160)
        t.fd(5)
        self.meme(166, 130)
        t.seth(-90)
        t.fd(3)
        t.circle(-4, 180)
        t.fd(3)
        t.seth(-90)
        t.fd(3)
        t.circle(-4, 180)
        t.fd(3)
        self.meme(168, 134)
        t.fillcolor('#F6D02F')
        t.begin_fill()
        t.seth(40)
        t.fd(200)
        t.seth(-80)
        t.fd(150)
        t.seth(210)
        t.fd(150)
        t.left(90)
        t.fd(100)
        t.right(95)
        t.fd(100)
        t.left(110)
        t.fd(70)
        t.right(110)
        t.fd(80)
        t.left(110)
        t.fd(30)
        t.right(110)
        t.fd(32)
        t.right(106)
        t.circle(100, 25)
        t.right(15)
        t.circle(-300, 2)
        ############## 
        t.seth(30)
        t.fd(40)
        t.left(100)
        t.fd(70)
        t.right(100)
        t.fd(80)
        t.left(100)
        t.fd(46)
        t.seth(66)
        t.circle(200, 38)
        t.right(10)
        t.fd(10)
        t.end_fill()
        t.fillcolor('#923E24')
        self.meme(126.82, -156.84)
        t.begin_fill()
        t.seth(30)
        t.fd(40)
        t.left(100)
        t.fd(40)
        t.pencolor('#923e24')
        t.seth(-30)
        t.fd(30)
        t.left(140)
        t.fd(20)
        t.right(150)
        t.fd(20)
        t.left(150)
        t.fd(20)
        t.right(150)
        t.fd(20)
        t.left(130)
        t.fd(18)
        t.pencolor('#000000')
        t.seth(-45)
        t.fd(67)
        t.right(110)
        t.fd(80)
        t.left(110)
        t.fd(30)
        t.right(110)
        t.fd(32)
        t.right(106)
        t.circle(100, 25)
        t.right(15)
        t.circle(-300, 2)
        t.end_fill()
        self.fucksisu9(-134.07, 147.81)
        self.fucksisu(-5, 25)
        self.fucksisu4(-126, 32)
        self.fucksisu5(107, 63)
        self.fucksisu6(-250, 100)
        self.fucksisu7(140, 270)
        self.ihatesisu1(-85, 90)
        self.ihatesisu2(50, 110)
        t.hideturtle()
    def fucksisu9(self, x, y):
        self.meme(x, y)
        t = self.t
        t.fillcolor('#CD0000')
        t.begin_fill()
        t.seth(200)
        t.circle(400, 7)
        t.left(180)
        t.circle(-400, 30)
        t.circle(30, 60)
        t.fd(50)
        t.circle(30, 45)
        t.fd(60)
        t.left(5)
        t.circle(30, 70)
        t.right(20)
        t.circle(200, 70)
        t.circle(30, 60)
        t.fd(70) 
        t.right(35)
        t.fd(50)
        t.circle(8, 100)
        t.end_fill()
        self.meme(-168.47, 185.52)
        t.seth(36)
        t.circle(-270, 54)
        t.left(180)
        t.circle(270, 27)
        t.circle(-80, 98)
        t.fillcolor('#444444')
        t.begin_fill()
        t.left(180)
        t.circle(80, 197)
        t.left(58)
        t.circle(200, 45)
        t.end_fill()
        self.meme(-58, 270)
        t.pencolor('#228B22')
        t.dot(35)
        self.meme(-30, 280)
        t.fillcolor('#228B22')
        t.begin_fill()
        t.seth(100)
        t.circle(30, 180)
        t.seth(190)
        t.fd(15)
        t.seth(100)
        t.circle(-45, 180)
        t.right(90)
        t.fd(15)
        t.end_fill()
        t.pencolor('#000000')
    def start(self):
        self.fucksisu8()
def main():
    turtle.screensize(800, 600)
    turtle.title('皮卡丘')
    cartoon = Cartoon()
    cartoon.start()
    turtle.mainloop()
if __name__ == '__main__':
    main()
```

### 画哆啦A梦

```python
import turtle
from turtle import *
turtle.title("哆啦A梦")
def fucksisu1(x, y):
    penup()
    goto(x, y)
    pendown()
def fucksisu2():
    fillcolor("#ffffff")
    begin_fill()
    tracer(False)
    a = 2.5
    for i in range(120):
        if 0 <= i < 30 or 60 <= i < 90:
            a -= 0.05
            lt(3)
            fd(a)
        else:
            a += 0.05
            lt(3)
            fd(a)
    tracer(True)
    end_fill()
def fucksisu3():
    fucksisu1(-32, 135)
    seth(165)
    fd(60)
    fucksisu1(-32, 125)
    seth(180)
    fd(60)
    fucksisu1(-32, 115)
    seth(193)
    fd(60)
    fucksisu1(37, 135)
    seth(15)
    fd(60)
    fucksisu1(37, 125)
    seth(0)
    fd(60)
    fucksisu1(37, 115)
    seth(-13)
    fd(60)
def fucksisu4():
    fucksisu1(5, 148)
    seth(270)
    fd(100)
    seth(0)
    circle(120, 50)
    seth(230)
    circle(-120, 100)
def fucksisu5():
    fillcolor('#e70010')
    begin_fill()
    seth(0)
    fd(200)
    circle(-5, 90)
    fd(10)
    circle(-5, 90)
    fd(207)
    circle(-5, 90)
    fd(10)
    circle(-5, 90)
    end_fill()
def fucksisu6():
    fucksisu1(-10, 158)
    seth(315)
    fillcolor('#e70010')
    begin_fill()
    circle(20)
    end_fill()
def black_fucksisu2():
    seth(0)
    fucksisu1(-20, 195)
    fillcolor('#000000')
    begin_fill()
    circle(13)
    end_fill()
    pensize(6)
    fucksisu1(20, 205)
    seth(75)
    circle(-10, 150)
    pensize(3)
    fucksisu1(-17, 200)
    seth(0)
    fillcolor('#ffffff')
    begin_fill()
    circle(5)
    end_fill()
    fucksisu1(0, 0)
def face():
    fd(183)
    lt(45)
    fillcolor('#ffffff')
    begin_fill()
    circle(120, 100)
    seth(180)
    fd(121)
    pendown()
    seth(215)
    circle(120, 100)
    end_fill()
    fucksisu1(63.56, 218.24)
    seth(90)
    fucksisu2()
    seth(180)
    penup()
    fd(60)
    pendown()
    seth(90)
    fucksisu2()
    penup()
    seth(180)
    fd(64)
def fucksisu7():
    penup()
    circle(150, 40)
    pendown()
    fillcolor('#00a0de')
    begin_fill()
    circle(150, 280)
    end_fill()
def fucksisu8():
    fucksisu7()
    fucksisu5()
    face()
    fucksisu6()
    fucksisu4()
    fucksisu3()
    fucksisu1(0, 0)
    seth(0)
    penup()
    circle(150, 50)
    pendown()
    seth(30)
    fd(40)
    seth(70)
    circle(-30, 270)
    fillcolor('#00a0de')
    begin_fill()
    seth(230)
    fd(80)
    seth(90)
    circle(1000, 1)
    seth(-89)
    circle(-1000, 10)
    seth(180)
    fd(70)
    seth(90)
    circle(30, 180)
    seth(180)
    fd(70)
    seth(100)
    circle(-1000, 9)
    seth(-86)
    circle(1000, 2)
    seth(230)
    fd(40)
    circle(-30, 230)
    seth(45)
    fd(81)
    seth(0)
    fd(203)
    circle(5, 90)
    fd(10)
    circle(5, 90)
    fd(7)
    seth(40)
    circle(150, 10)
    seth(30)
    fd(40)
    end_fill()
    seth(70)
    fillcolor('#ffffff')
    begin_fill()
    circle(-30)
    end_fill()
    fucksisu1(103.74, -182.59)
    seth(0)
    fillcolor('#ffffff')
    begin_fill()
    fd(15)
    circle(-15, 180)
    fd(90)
    circle(-15, 180)
    fd(10)
    end_fill()
    fucksisu1(-96.26, -182.59)
    seth(180)
    fillcolor('#ffffff')
    begin_fill()
    fd(15)
    circle(15, 180)
    fd(90)
    circle(15, 180)
    fd(10)
    end_fill()
    fucksisu1(-133.97, -91.81)
    seth(50)
    fillcolor('#ffffff')
    begin_fill()
    circle(30)
    end_fill()
    fucksisu1(-103.42, 15.09)
    seth(0)
    fd(38)
    seth(230)
    begin_fill()
    circle(90, 260)
    end_fill()
    fucksisu1(5, -40)
    seth(0)
    fd(70)
    seth(-90)
    circle(-70, 180)
    seth(0)
    fd(70)
    fucksisu1(-103.42, 15.09)
    fd(90)
    seth(70)
    fillcolor('#ffd200')
    begin_fill()
    circle(-20)
    end_fill()
    seth(170)
    fillcolor('#ffd200')
    begin_fill()
    circle(-2, 180)
    seth(10)
    circle(-100, 22)
    circle(-2, 180)
    seth(180 - 10)
    circle(100, 22)
    end_fill()
    goto(-13.42, 15.09)
    seth(250)
    circle(20, 110)
    seth(90)
    fd(15)
    dot(10)
    fucksisu1(0, -150)
    black_fucksisu2()
if __name__ == '__main__':
    screensize(800, 600, "#f0f0f0")
    pensize(3)
    speed(9)
    fucksisu8()
    mainloop()
```

### 钢铁侠

```python
import turtle
fucksisu1 = [[(-40, 120), (-70, 260), (-130, 230), (-170, 200), (-170, 100), (-160, 40), (-170, 10), (-150, -10), (-140, 10),
           (-40, -20), (0, -20)],
          [(0, -20), (40, -20), (140, 10), (150, -10), (170, 10), (160, 40), (170, 100), (170, 200), (130, 230), (70, 260),
           (40, 120), (0, 120)]]
fucksisu2 = [[(-40, -30), (-50, -40), (-100, -46), (-130, -40), (-176, 0), (-186, -30), (-186, -40), (-120, -170), (-110, -210),
           (-80, -230), (-64, -210), (0, -210)],
          [(0, -210), (64, -210), (80, -230), (110, -210), (120, -170), (186, -40), (186, -30), (176, 0), (130, -40),
           (100, -46), (50, -40), (40, -30), (0, -30)]]
fucksisu3 = [[(-60, -220), (-80, -240), (-110, -220), (-120, -250), (-90, -280), (-60, -260), (-30, -260), (-20, -250),
           (0, -250)],
          [(0, -250), (20, -250), (30, -260), (60, -260), (90, -280), (120, -250), (110, -220), (80, -240), (60, -220),
           (0, -220)]]
turtle.hideturtle()
turtle.bgcolor('#ba161e')  # Dark Red
turtle.setup(500, 600)
turtle.title("钢铁侠")
fucksisu1Goto = (0, 120)
fucksisu2Goto = (0, -30)
fucksisu3Goto = (0, -220)
turtle.speed(2)
def logo(a, b):
    turtle.penup()
    turtle.goto(b)
    turtle.pendown()
    turtle.color('#fab104')  # Light Yellow
    turtle.begin_fill()
    for i in range(len(a[0])):
        x, y = a[0][i]
        turtle.goto(x, y)
    for i in range(len(a[1])):
        x, y = a[1][i]
        turtle.goto(x, y)
    turtle.end_fill()
logo(fucksisu1, fucksisu1Goto)
logo(fucksisu2, fucksisu2Goto)
logo(fucksisu3, fucksisu3Goto)
turtle.hideturtle()
turtle.done()
```

### 蝙蝠侠

```python
import turtle
import math
turtle.title("蝙蝠侠")
fucksisu1 = turtle.Turtle()
fucksisu1.speed(500)
window = turtle.Screen()
window.bgcolor("#000000")
fucksisu1.color("yellow")
fucksisu2 = 20
fucksisu1.left(90)
fucksisu1.penup()
fucksisu1.goto(-7 * fucksisu2, 0)
fucksisu1.pendown()
for a in range(-7 * fucksisu2, -3 * fucksisu2, 1):
    x = a / fucksisu2
    rel = math.fabs(x)
    y = 1.5 * math.sqrt((-math.fabs(rel - 1)) * math.fabs(3 - rel) / ((rel - 1) * (3 - rel))) * (
                1 + math.fabs(rel - 3) / (rel - 3)) * math.sqrt(1 - (x / 7) ** 2) + (
                    4.5 + 0.75 * (math.fabs(x - 0.5) + math.fabs(x + 0.5)) - 2.75 * (
                        math.fabs(x - 0.75) + math.fabs(x + 0.75))) * (1 + math.fabs(1 - rel) / (1 - rel))
    fucksisu1.goto(a, y * fucksisu2)
for a in range(-3 * fucksisu2, -1 * fucksisu2 - 1, 1):
    x = a / fucksisu2
    rel = math.fabs(x)
    y = (2.71052 + 1.5 - 0.5 * rel - 1.35526 * math.sqrt(4 - (rel - 1) ** 2)) * math.sqrt(
        math.fabs(rel - 1) / (rel - 1))
    fucksisu1.goto(a, y * fucksisu2)
fucksisu1.goto(-1 * fucksisu2, 3 * fucksisu2)
fucksisu1.goto(int(-0.5 * fucksisu2), int(2.2 * fucksisu2))
fucksisu1.goto(int(0.5 * fucksisu2), int(2.2 * fucksisu2))
fucksisu1.goto(1 * fucksisu2, 3 * fucksisu2)
for a in range(1 * fucksisu2 + 1, 3 * fucksisu2 + 1, 1):
    x = a / fucksisu2
    rel = math.fabs(x)
    y = (2.71052 + 1.5 - 0.5 * rel - 1.35526 * math.sqrt(4 - (rel - 1) ** 2)) * math.sqrt(
        math.fabs(rel - 1) / (rel - 1))
    fucksisu1.goto(a, y * fucksisu2)
for a in range(3 * fucksisu2 + 1, 7 * fucksisu2 + 1, 1):
    x = a / fucksisu2
    rel = math.fabs(x)
    y = 1.5 * math.sqrt((-math.fabs(rel - 1)) * math.fabs(3 - rel) / ((rel - 1) * (3 - rel))) * (
                1 + math.fabs(rel - 3) / (rel - 3)) * math.sqrt(1 - (x / 7) ** 2) + (
                    4.5 + 0.75 * (math.fabs(x - 0.5) + math.fabs(x + 0.5)) - 2.75 * (
                        math.fabs(x - 0.75) + math.fabs(x + 0.75))) * (1 + math.fabs(1 - rel) / (1 - rel))
    fucksisu1.goto(a, y * fucksisu2)
for a in range(7 * fucksisu2, 4 * fucksisu2, -1):
    x = a / fucksisu2
    rel = math.fabs(x)
    y = (-3) * math.sqrt(1 - (x / 7) ** 2) * math.sqrt(math.fabs(rel - 4) / (rel - 4))
    fucksisu1.goto(a, y * fucksisu2)
for a in range(4 * fucksisu2, -4 * fucksisu2, -1):
    x = a / fucksisu2
    rel = math.fabs(x)
    y = math.fabs(x / 2) - 0.0913722 * x ** 2 - 3 + math.sqrt(1 - (math.fabs(rel - 2) - 1) ** 2)
    fucksisu1.goto(a, y * fucksisu2)
for a in range(-4 * fucksisu2 - 1, -7 * fucksisu2 - 1, -1):
    x = a / fucksisu2
    rel = math.fabs(x)
    y = (-3) * math.sqrt(1 - (x / 7) ** 2) * math.sqrt(math.fabs(rel - 4) / (rel - 4))
    fucksisu1.goto(a, y * fucksisu2)
fucksisu1.penup()
fucksisu1.goto(300, 300)
turtle.done()
```

