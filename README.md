# senla1
Task1
import random

def draw_hangman(lives):
    stages = [
        """
           ------
           |    |
           |    O
           |   /|\\
           |   / \\
           |
        """,
        """
           ------
           |    |
           |    O
           |   /|\\
           |   /
           |
        """,
        """
           ------
           |    |
           |    O
           |   /|
           |
           |
        """,
        """
           ------
           |    |
           |    O
           |    |
           |
           |
        """,
        """
           ------
           |    |
           |    O
           |
           |
           |
        """,
        """
           ------
           |    |
           |
           |
           |
           |
        """,
        """
           ------
           |
           |
           |
           |
           |
        """,
    ]
    return stages[lives]

def play_hangman():
    words = ['python', 'hangman', 'challenge', 'programming', 'developer']
    word = random.choice(words)
    guessed = ['_'] * len(word)
    lives = 6
    guessed_letters = set()

    print("Добро пожаловать в игру 'Виселица'!")
    
    while lives > 0 and '_' in guessed:
        print(draw_hangman(lives))
        print(" ".join(guessed))
        print(f"Жизни: {lives}")
        
        guess = input("Введите букву: ").lower()
        
        if guess in guessed_letters:
            print("Вы уже угадали эту букву.")
            continue
        
        guessed_letters.add(guess)

        if guess in word:
            for idx, letter in enumerate(word):
                if letter == guess:
                    guessed[idx] = letter
        else:
            lives -= 1
            print(f"Буквы '{guess}' нет в слове.")

    if '_' not in guessed:
        print("Поздравляем! Вы угадали слово:", word)
    else:
        print(draw_hangman(lives))
        print("Вы проиграли! Загаданное слово:", word)

if __name__ == "__main__":
    play_hangman()
