# basicquizgame

class Quiz:
    def __init__(self, questions):
        self.questions = questions
        self.score = 0

    def display_question(self, question):
        print(question['question'])
        for idx, option in enumerate(question['options'], start=1):
            print(f"{idx}. {option}")
        user_answer = input("Enter your answer (1, 2, 3, or 4): ")
        return user_answer

    def check_answer(self, question, user_answer):
        correct_answer = question['correct_answer']
        if user_answer.lower() == correct_answer.lower():
            print("Correct!")
            self.score += 1
        else:
            print(f"Incorrect. The correct answer is: {correct_answer}")

    def run_quiz(self):
        for question in self.questions:
            user_answer = self.display_question(question)
            self.check_answer(question, user_answer)
            print()  # Add a newline for better readability

        print(f"Quiz complete! Your final score is {self.score}/{len(self.questions)}.")


def main():
    # Define your quiz questions and options
    questions = [
        {
            'question': "What is the capital of France?",
            'options': ["Paris", "London", "Berlin", "Madrid"],
            'correct_answer': "Paris"
        },
        {
            'question': "Which planet is known as the Red Planet?",
            'options': ["Earth", "Mars", "Jupiter", "Saturn"],
            'correct_answer': "Mars"
        },
        {
            'question': "Who wrote 'Romeo and Juliet'?",
            'options': ["Charles Dickens", "Jane Austen", "William Shakespeare", "Mark Twain"],
            'correct_answer': "William Shakespeare"
        }
    ]

    # Create a Quiz object and start the quiz
    quiz = Quiz(questions)
    quiz.run_quiz()


if __name__ == "__main__":
    main()
