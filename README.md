print('Welcome to Tic Tac Toe!')

# turn = '' # needs to be an empty string because we're storing the result of go_first(), a string, inside

while True: # loop forever
    game_board = [' ']*10 # clear board 
    player1_marker , player2_marker = assign_marker() # assign players to marker
    turn = go_first() # randomly choose who goes first
    print(f"{turn}, you're up first!")
    play_game = input("Ready? Enter Yes or No.")
    
    if play_game.lower()[0] == 'y': 
        game_on = True
        print("LET'S PLAY!")
    else:
        game_on = False

while game_on: # initiates the start of the game
    if turn == 'Player 1': # if player 1 is first

        display_board(game_board) # display board
        position = player_choice(game_board) # ask for position from player
        place_marker(game_board, player1_marker, position) # place marker at the position

        if check_winner(game_board, player1_marker): # if there are no more moves
            display_board(game_board) # display board
            print(f"{turn} wins!")
            game_on = False
        else: # if there's no winner
            if is_board_full(game_board): # check to see if the board is full
                # if board is full but there's no winner, it's a draw
                display_board(game_board) # display board
                print("It's a draw!")
                break
            else: # if the board is NOT full ...
                turn = 'Player 2' #move on to player 2; THIS IS HOW TO ALTERNATE TURNS

    else: # Player 2's turn
        display_board(game_board)
        position = player_choice(game_board) # ask for position from player
        place_marker(game_board, player2_marker, position) # place marker at the position

        if check_winner(game_board, player2_marker):
            display_board(game_board) # display board
            print(f"{turn} wins!")
            game_on = False
        else: # if there's no winner
            if is_board_full(game_board): # check to see if the board is full
                # if board is full but there's no winner, it's a draw
                display_board(game_board) # display board
                print("It's a draw!")
                break

            else: # if the board is NOT full ...
                turn = 'Player 1' #move on to player 1; THIS IS HOW TO ALTERNATE TURNS

if not replay():
    break
