# Glowing-flower
import turtle
import math
import random

# Create the screen
screen = turtle.Screen()
screen.title("Glowing Flower Animation")
screen.bgcolor("black")
screen.setup(width=900, height=650)
screen.tracer(0)

# Create a turtle
t = turtle.Turtle()
t.hideturtle()
t.speed(0)
turtle.colormode(255)


# Function to draw a glowing effect
def draw_glow(x, y, radius, color):
    t.penup()
    t.goto(x, y - radius)
    t.pendown()
    t.color(color)
    t.begin_fill()
    t.circle(radius)
    t.end_fill()


# Function to draw a flower petal
def draw_petal(x, y, angle, length, color):
    t.penup()
    t.goto(x, y)
    t.setheading(angle)
    t.pendown()
    t.color(color)
    t.pensize(2)
    t.forward(length)
    t.backward(length)


# Function to draw leaves
def draw_leaf(x, y, angle, length, color):
    t.penup()
    t.goto(x, y)
    t.setheading(angle)
    t.pendown()
    t.color(color)
    t.pensize(3)

    t.circle(length, 60)
    t.left(120)
    t.circle(length, 60)


# Function to draw a flower
def draw_flower(x, y, size):
    # Draw the stem
    t.penup()
    t.goto(x, y - 150)
    t.setheading(90)
    t.pendown()
    t.pensize(3)
    t.color("#5b2817")
    t.forward(150)

    # Draw leaves on the stem
    for i in range(3):
        leaf_y = y - 120 + i * 35

        draw_leaf(
            x, leaf_y, 150, size * 0.55, "#71351e"
        )

        draw_leaf(
            x, leaf_y + 5, 30, size * 0.55, "#71351e"
        )

    # Draw glowing flower petals
    for layer in range(3):
        petal_size = size - layer * 5

        for angle in range(0, 360, 45):
            t.penup()
            t.goto(x, y)
            t.setheading(angle)
            t.forward(petal_size / 2)
            t.pendown()

            t.dot(petal_size, "#ff6620")

    # Add a bright center
    t.penup()
    t.goto(x, y)
    t.dot(size * 0.35, "#fff27a")


# Draw multiple flowers
flowers = [
    (-250, -30, 45),
    (-100, 60, 30),
    (0, 100, 55),
    (130, 40, 35),
    (260, -10, 25)
]

for x, y, size in flowers:
    draw_flower(x, y, size)

# Update the screen
screen.update()

# Keep the window open
turtle.done()
