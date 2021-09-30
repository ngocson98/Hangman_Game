# Hangman_Game
## Hangman Game in Python – Simple Game Project for Beginners
Rather than playing games developed by others, let’s develop a game in python. Work on python hangman game and master the most popular programming language on the planet
#### Source: https://data-flair.training/blogs/hangman-game-python-code/
![simple-hangman-game-python-1024x536](https://user-images.githubusercontent.com/87347502/135490741-843b72a5-0c72-44b0-9bfd-0e8c0d8bab64.jpg)
## Vietnamese
Mục tiêu project này là lập trình game Hangman bằng Python. Bài toán không yêu cầu bất kỳ module cụ thể nào ngoài ***random()*** và ***time()***. Các vòng lặp loop() và hàm function() trong Python là đủ để xây dựng trò chơi này.
## Các bước để xây dựng chương trình:
- Import các module: ***random, time***
- Xây dựng hàm 
- Tạo vòng lặp
- Chuyển hàm để run chương trình.
### Bước 1: Import
     import random
     import time

     # Initial Steps to invite in the game:
     print("\nWelcome to Hangman game by DataFlair\n")
     name = input("Enter your name: ")
     print("Hello " + name + "! Best of Luck!")
     time.sleep(2)
     print("The game is about to start!\n Let's play Hangman!")
     time.sleep(3)
#### Giải thích:
- ***random***: Dùng để chọn ngẫu nhiên một mục (item) từ list[] hoặc chuỗi.
- ***time***: Nhập thời gian thực từ máy tính để sử dụng trong chương trình.
- ***time.sleep()***: Dùng để tạm dừng thực thi chương trình trong vài giây. 
### Bước 2: Tạo hàm
    def main():
        global count
        global display
        global word
        global already_guessed
        global length
        global play_game
        words_to_guess = ["january","border","image","film","promise","kids","lungs","doll","rhyme","damage","plants"]
        word = random.choice(words_to_guess)
        length = len(word)
        count = 0
        display = '_' * length
        already_guessed = []
        play_game = ""
 #### Giải thích:
- Khởi tạo:*global count, global display, global word, global already_guessed, global length* và *global play_game*. 
- *Words_to_guess*: List chứa các từ mà người chơi cần phải đoán ra trong game.
- *Word*: từ được random trong list[].
- *Length*: len(word) chiều dài chuỗi.
- *Count*: biến đếm bắt đầu từ 0.
- *Display*: mỗi gạch _ tượng trưng cho 1 ký tự của word
- *Already_guessed*: chỉ số chuỗi của từu được đoán đúng.
### Bước 3: Vòng lặp
    def play_loop():
        global play_game
        play_game = input("Do You want to play again? y = yes, n = no \n")
        while play_game not in ["y", "n","Y","N"]:
            play_game = input("Do You want to play again? y = yes, n = no \n")
       if play_game == "y":
            main()
       elif play_game == "n":
            print("Thanks For Playing! We expect you back again!")
            exit()
 #### Giải thích:
- *Play_loop*: nhận đối số của *play_game*.
- *Play_game*: Đối số được dùng để xác định chơi tiếp hay dừng game. Câu hỏi Yes/No (Y/N?)
### Bước 4: Khời tạo điều kiện chơi
# Initializing all the conditions required for the game:
    def hangman():
        global count
        global display
        global word
        global already_guessed
        global play_game
        limit = 5
        guess = input("This is the Hangman Word: " + display + " Enter your guess: \n")
        guess = guess.strip()
        if len(guess.strip()) == 0 or len(guess.strip()) >= 2 or guess <= "9":
            print("Invalid Input, Try a letter\n")
            hangman()
#### Giải thích:
- ***Limit***: Số chữ cái tối đa cung cấp cho người chơi để đoán một từ cụ thể.
- ***Guess***: Lấy đầu vào từ người chơi cho chữ cái được đoán. ***Guess.strip()*** xoá chữ cái khỏi từ đã cho - *word*.
- Nếu vòng lặp kiểm tra không có đầu vào nào được đưa ra hoặc hai chữ cái được đưa ra cùng một lúc hoặc một số được nhập làm đầu vào, nó sẽ cho người chơi biết về đầu vào không hợp lệ và thực thi lại hangman.
### Bước 5: Phần còn lại (tiếp tục từ *if*)
