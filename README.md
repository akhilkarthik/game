# game
my basic python game
char_spdaf = 1
char_spdbf = 0.6



import turtle
wn = turtle.Screen()
wn.title("welcome to karthik's game")
wn.bgcolor("black")
wn.setup(width=800, height=600)
wn.tracer(0)

# Paddle A
paddle_a = turtle.Turtle()
paddle_a.speed(0)
paddle_a.shape("square")
paddle_a.color("green")
paddle_a.shapesize(stretch_wid=5,stretch_len=1)

paddle_a.penup()
paddle_a.goto(-350,0)


# Paddle B
paddle_b = turtle.Turtle()
paddle_b.speed(0)
paddle_b.shape("square")
paddle_b.color("green")
paddle_b.shapesize(stretch_wid=5,stretch_len=1)
paddle_b.penup()
paddle_b.goto(+350,0)

# Ball
ball = turtle.Turtle()
ball.speed(0)
ball.shape("square")
ball.color("red")

ball.penup()
ball.goto(0,0)
ball.dx = char_spdbf
ball.dy = -char_spdbf

# Function
def  paddle_a_up():
    y = paddle_a.ycor()
    y += 20
    paddle_a.sety(y)

def  paddle_a_down():
    y = paddle_a.ycor()
    y -= 20
    paddle_a.sety(y)




def  paddle_b_up():
    y = paddle_b.ycor()
    y += 20
    paddle_b.sety(y)

def  paddle_b_down():
    y = paddle_b.ycor()
    y -= 20
    paddle_b.sety(y)

# keyboard bindings
wn.listen()
wn.onkeypress(paddle_a_up,"w")
wn.onkeypress(paddle_a_down,"z")

wn.onkeypress(paddle_b_up,"8")
wn.onkeypress(paddle_b_down,"2")







# main game loop

while True:
    wn.update()

    # move the ball
    ball.setx(ball.xcor() + ball.dx)
    ball.sety(ball.ycor() + ball.dy)


# border
    if ball.ycor() > 290:
        ball.sety(290)
        ball.dy *= -char_spdaf

    if ball.ycor() < -290:
        ball.sety(-290)
        ball.dy *= -char_spdaf



    if ball.xcor() > 390:
        ball.goto(0,0)
        ball.dx *= -1

    if ball.xcor() < -390:
        ball.goto(0,0)
        ball.dx *= -1


# ball  and paddle

    if (ball.xcor() > 340 and ball.xcor() < 350) and (ball.ycor() < paddle_b.ycor() + 40 and ball.ycor() > paddle_b.ycor() -40):
        ball.setx(340)
        ball.dx *= -1
    if (ball.xcor() < -340 and ball.xcor() > -350) and (ball.ycor() < paddle_a.ycor() + 40 and ball.ycor() > paddle_b.ycor() -40):
        ball.setx(-340)
        ball.dx *= -1



















