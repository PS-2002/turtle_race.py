# turtle_race.py
from turtle import Turtle, Screen
import random

screen = Screen()
screen.setup(500, 400)
is_race_on = False
user_bet = screen.textinput(prompt="Which turtle will win the race?", title="Make your bet")
colors = ["red", "orange", "yellow", "green", "blue", "purple"]
y_positions = [-100, -50, 0, 50, 100, 150]
all_turtles = []
for index_positions in range(0, 6):
    new_turtle = Turtle(shape="turtle")
    new_turtle.color(colors[index_positions])
    new_turtle.penup()
    new_turtle.goto(x=-230, y=y_positions[index_positions])
    all_turtles.append(new_turtle)

if user_bet:
    is_race_on = True

while is_race_on:
    for turtle in all_turtles:
        if turtle.xcor() > 230:
            is_race_on = False
            winning_color = turtle.pencolor()
            if winning_color == user_bet:
                print(f"You've won! The {winning_color} turtle is winner. ")
            else:
                print(f"You've lost! The {winning_color} turtle is winner. ")

        rand_dist = random.randint(0, 10)
        turtle.forward(rand_dist)
screen.exitonclick()
