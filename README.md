#pong game
#using turtle library
#done by balashobika and madhumathi




# Import required library

import turtle

# Create screen

sc = turtle.Screen()

sc.title("Pong game")

sc.bgcolor("white")

sc.setup(width=1000, height=600)

# Left paddle

left_pad = turtle.Turtle()

left_pad.speed(0)

left_pad.shape("square")

left_pad.color("black")

left_pad.shapesize(stretch_wid=6, stretch_len=2)
left_pad.penup()

left_pad.goto(-400, 0)

# Right paddle

right_pad = turtle.Turtle()

right_pad.speed(0)

right_pad.shape("square")

right_pad.color("black")

right_pad.shapesize(stretch_wid=6, stretch_len=2)
right_pad.penup()

right_pad.goto(400, 0)

# up paddle

up_pad = turtle.Turtle()

up_pad.speed(0)

up_pad.shape("square")

up_pad.color("black")

up_pad.shapesize(stretch_wid=2, stretch_len=6)

up_pad.goto(0,280)

# down paddle

down_pad = turtle.Turtle()

down_pad.speed(0)

down_pad.shape("square")

down_pad.color("black")

down_pad.shapesize(stretch_wid=2, stretch_len=6)

down_pad.goto(0,-280)


# Ball of circle shape

hit_ball = turtle.Turtle()

hit_ball.speed(40)

hit_ball.shape("circle")

hit_ball.color("blue")
hit_ball.penup()

hit_ball.goto(0, 0)

hit_ball.dx = 5

# Initialize the score

left_player = 0

right_player = 0

# Displays the score

sketch = turtle.Turtle()

sketch.speed(0)

sketch.color("blue")
sketch.penup()
sketch.hideturtle()

sketch.goto(0, 260)

sketch.write("Left_player : 0 Right_player: 0",

             align="center", font=("Courier", 24, "normal"))


# Functions to move paddle vertically

def paddleaup():
    y = left_pad.ycor()

    y += 20

    left_pad.sety(y)


def paddleadown():
    y = left_pad.ycor()

    y -= 20

    left_pad.sety(y)


def paddlebup():
    y = right_pad.ycor()

    y += 20

    right_pad.sety(y)


def paddlebdown():
    y = right_pad.ycor()

    y -= 20

    right_pad.sety(y)

def paddlecleft():
    w = up_pad.xcor()

    w -= 40

    up_pad.setx(w)

def paddlecright():
    w = up_pad.xcor()

    w += 40

    up_pad.setx(w)

def paddledleft():
    z = down_pad.xcor()

    z -= 40

    down_pad.setx(z)

def paddledright():
    z = down_pad.xcor()

    z += 40

    down_pad.setx(z)


# Keyboard bindings
sc.listen()

sc.onkeypress(paddleaup, "2")

sc.onkeypress(paddleadown, "9")

sc.onkeypress(paddlebup, "Up")

sc.onkeypress(paddlebdown, "Down")

sc.onkeypress(paddlecleft, "3")

sc.onkeypress(paddlecright, "4")

sc.onkeypress(paddledleft, "1")

sc.onkeypress(paddledright, "0")

# from here it is important to make the game work

while True:

 sc.update()

 hit_ball.setx(hit_ball.xcor() + hit_ball.dx)

 hit_ball.sety(hit_ball.ycor() + hit_ball.dx)

 hit_ball.setx(hit_ball.xcor() + hit_ball.dx)

 hit_ball.sety(hit_ball.ycor() + hit_ball.dx)

# Checking borders

 if hit_ball.ycor() > 280:
    hit_ball.sety(280)

    hit_ball.dx *= -1

 if hit_ball.ycor() < -280:
    hit_ball.sety(-280)

 if hit_ball.ycor() > 280:
        hit_ball.sety(280)

        hit_ball.dx *= -1

 if hit_ball.ycor() < -280:
        hit_ball.sety(-280)



 if hit_ball.xcor() > 500:
    hit_ball.goto(0, 0)

    hit_ball.dx *= -1

    left_player += 1

    sketch.clear()

    sketch.write("Left_player : {} Right_player: {}".format(

        left_player, right_player), align="center",

        font=("Courier", 24, "normal"))

 if hit_ball.xcor() < -500:
    hit_ball.goto(0, 0)

    hit_ball.dx *= -1

    right_player += 1

    sketch.clear()

    sketch.write("Left_player : {} Right_player: {}".format(

        left_player, right_player), align="center",

        font=("Courier", 24, "normal"))

# Paddle ball collision

 if ((hit_ball.xcor() > 360 and

            hit_ball.xcor() < 370) and

           (hit_ball.ycor() < right_pad.ycor() + 40 and

           hit_ball.ycor() > right_pad.ycor() - 40)):

  hit_ball.setx(360)

  hit_ball.dx *= -1

 if ((hit_ball.xcor() < -360 and

        hit_ball.xcor() > -370) and

        (hit_ball.ycor() < left_pad.ycor() + 40 and

         hit_ball.ycor() > left_pad.ycor() - 40)):

  hit_ball.setx(-360)

  hit_ball.dx *= -1

  if ((hit_ball.xcor() < -270 and

       hit_ball.xcor() > -280) and

          (hit_ball.ycor() < up_pad.ycor() + 40 and

           hit_ball.ycor() > up_pad.ycor() - 40)):
      hit_ball.setx(-360)

      hit_ball.dx *= -1

  if ((hit_ball.xcor() < -270 and

       hit_ball.xcor() > -280) and

          (hit_ball.ycor() < down_pad.ycor() + 40 and

           hit_ball.ycor() > down_pad.ycor() - 40)):
      hit_ball.setx(-360)

      hit_ball.dx *= -1
