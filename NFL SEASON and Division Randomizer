import random

# List of all 32 NFL teams
teams = [
    "Arizona Cardinals", "Atlanta Falcons", "Baltimore Ravens", "Buffalo Bills",
    "Carolina Panthers", "Chicago Bears", "Cincinnati Bengals", "Cleveland Browns",
    "Dallas Cowboys", "Denver Broncos", "Detroit Lions", "Green Bay Packers",
    "Houston Texans", "Indianapolis Colts", "Jacksonville Jaguars", "Kansas City Chiefs",
    "Las Vegas Raiders", "Los Angeles Chargers", "Los Angeles Rams", "Miami Dolphins",
    "Minnesota Vikings", "New England Patriots", "New Orleans Saints", "New York Giants",
    "New York Jets", "Philadelphia Eagles", "Pittsburgh Steelers", "San Francisco 49ers",
    "Seattle Seahawks", "Tampa Bay Buccaneers", "Tennessee Titans", "Washington Commanders"
]

def create_random_divisions(teams):
    random.shuffle(teams)
    divisions = {
        "North": teams[:8],
        "South": teams[8:16],
        "East": teams[16:24],
        "West": teams[24:]
    }
    return divisions

def generate_random_schedule(teams, games_per_team=3):
    random.shuffle(teams)
    schedule = []
    used_pairs = set()
    
    for team in teams:
        matchups = []
        available = [t for t in teams if t != team and (team, t) not in used_pairs and (t, team) not in used_pairs]
        
        while len(matchups) < games_per_team and available:
            opponent = random.choice(available)
            used_pairs.add((team, opponent))
            matchups.append(f"{team} vs {opponent}")
            available.remove(opponent)
        
        schedule.append({team: matchups})
    
    return schedule

def display_divisions(divisions):
    for division, teams in divisions.items():
        print(f"\n{division} Division:")
        for team in teams:
            print(f"  - {team}")

def display_schedule(schedule):
    for team_schedule in schedule:
        for team, matchups in team_schedule.items():
            print(f"\n{team}'s Games:")
            for matchup in matchups:
                print(matchup)

if __name__ == "__main__":
    divisions = create_random_divisions(teams)
    schedule = generate_random_schedule(teams)
    
    display_divisions(divisions)
    display_schedule(schedule)
