# Project-synopsis-cl-11-sec-k
# Simple Cricket Game Simulation
import random

# Function to simulate batting
def bat():
    # Possible outcomes on a ball
    outcomes = [0, 1, 2, 3, 4, 6, 'W']
    return random.choice(outcomes)

# Function for a single innings
def play_innings(team_name, players):
    print(f"\n{team_name} is batting now!")
    total_score = 0
    wickets = 0
    for player in players:
        print(f"{player} is batting...")
        player_score = 0
        while True:
            outcome = bat()
            if outcome == 'W':
                print(f"Out! {player} scored {player_score} runs.")
                wickets += 1
                break
            else:
                player_score += outcome
                total_score += outcome
                print(f"{player} scores {outcome} runs! Total: {total_score}/{wickets}")
            
            if wickets == len(players):
                break

        if wickets == len(players):
            break

    print(f"Innings Over! {team_name} scored {total_score}/{wickets}.")
    return total_score

# Main function to simulate the match
def cricket_match():
    print("Welcome to the Cricket Match Simulation!")
    
    team1 = input("Enter the name of Team 1: ")
    team2 = input("Enter the name of Team 2: ")
    
    num_players = int(input("Enter the number of players in each team: "))
    players_team1 = [f"{team1}_Player{i+1}" for i in range(num_players)]
    players_team2 = [f"{team2}_Player{i+1}" for i in range(num_players)]
    
    # Team 1 bats first
    score_team1 = play_innings(team1, players_team1)
    
    # Team 2 bats second
    score_team2 = play_innings(team2, players_team2)
    
    # Deciding the winner
    print("\nMatch Over!")
    if score_team1 > score_team2:
        print(f"{team1} wins by {score_team1 - score_team2} runs!")
    elif score_team2 > score_team1:
        print(f"{team2} wins by {num_players - (score_team2 - score_team1)} wickets!")
    else:
        print("It's a Tie!")

# Run the cricket match simulation
cricket_match()
