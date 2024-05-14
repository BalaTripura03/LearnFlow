# LearnFlow
Python Tasks
Task 1 : Quiz Game
Problem Statement:
Create a quiz game that quizzes users on a chosen topic. The game should keep track of scores,
provide feedback on correct and incorrect answers, and allow users to select difficulty levels
for an engaging learning experience.



import random

class Question:
    def __init__(self, text, choices, correct_answer):
        self.text = text
        self.choices = choices
        self.correct_answer = correct_answer

class Quiz:
    def __init__(self, questions):
        self.questions = questions
        self.score = 0

    def display_question(self, question):
        print(question.text)
        for choice in question.choices:
            print(choice)
        print()

    def check_answer(self, question, user_answer):
        if user_answer.lower() == question.correct_answer.lower():
            print("Correct!")
            self.score += 1
        else:
            print("Incorrect! The correct answer is:", question.correct_answer)

    def run_quiz(self):
        print("Welcome to the Quiz Game!")
        print("Select difficulty level:")
        print("1. Easy")
        print("2. Medium")
        print("3. Hard")
        difficulty = int(input("Enter your choice (1/2/3): "))

        # Adjust number of questions based on difficulty
        if difficulty == 1:
            num_questions = 3
        elif difficulty == 2:
            num_questions = 5
        else:
            num_questions = 7

        random.shuffle(self.questions)
        for i in range(num_questions):
            self.display_question(self.questions[i])
            user_answer = input("Your answer: ")
            self.check_answer(self.questions[i], user_answer)
            print()
        
        print("Quiz completed!")
        print("Your score:", self.score, "/", num_questions)

# Example usage
questions = [
    Question("What is the capital of France?", ["A. London", "B. Paris", "C. Rome", "D. Madrid"], "B"),
    Question("What is the largest planet in the solar system?", ["A. Earth", "B. Jupiter", "C. Mars", "D. Saturn"], "B"),
    Question("What is the chemical symbol for water?", ["A. Wo", "B. W", "C. H2O", "D. Wa"], "C"),
    Question("Which country is known as the Land of the Rising Sun?", ["A. China", "B. Japan", "C. India", "D. South Korea"], "B"),
    Question("What is the powerhouse of the cell?", ["A. Mitochondria", "B. Nucleus", "C. Ribosome", "D. Golgi Apparatus"], "A"),
    Question("Who wrote 'Romeo and Juliet'?", ["A. William Shakespeare", "B. Charles Dickens", "C. Jane Austen", "D. Mark Twain"], "A"),
    Question("What is the chemical symbol for gold?", ["A. Au", "B. Ag", "C. Fe", "D. Cu"], "A")
]

quiz = Quiz(questions)
quiz.run_quiz()
