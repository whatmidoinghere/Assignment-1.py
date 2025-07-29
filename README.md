# Assignment-1.py
Python assignment 1
import random

def ask_questions():
    questions = {
        "name": "What's your name? ",
        "age": "How old are you? ",
        "color": "What's your favorite color? ",
        "food": "What's your favorite food? ",
        "city": "Which city do you live in? ",
        "shs": "Which SHS did you attend? ",
        "team": "What's your favourite soccer team? "
    }

    keys = list(questions.keys())
    random.shuffle(keys)

    answers = {}
    for key in keys:
        answers[key] = input(questions[key])
    
    return answers

def display_summary(data):
    print(f"\nHello, {data['name']}!")
    print(f"You are {data['age']} years old, love the color {data['color']}, and enjoy eating {data['food']}.")
    print(f"Life must be awesome in {data['city']}!")
    print(f"You attended {data['shs']} and support {data['team']}!\n")

def save_to_file(data, rating):
    filename = f"{data['name']}.txt"
    with open(filename, "w") as file:
        file.write("---- User Summary ----\n")
        for key, value in data.items():
            file.write(f"{key.capitalize()}: {value}\n")
        file.write(f"Rating: {rating} stars\n")
    print(f"Summary saved to {filename}!")

def main():
    while True:
        answers = ask_questions()
        display_summary(answers)

        save = input("Would you like to save this summary to a file? (yes/no): ").strip().lower()
        if save == "yes":
            rating = input("Rate this assistant (1-5 stars): ")
            save_to_file(answers, rating)

        again = input("Do you want to restart the process? (yes/no): ").strip().lower()
        if again != "yes":
            print("Thanks for using the assistant. Goodbye!")
            break

if __name__ == "__main__":
    main()
