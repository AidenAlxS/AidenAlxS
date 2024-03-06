import random

class Hero:
    def __init__(self, name, quirk, hp, attack):
        self.name = name
        self.quirk = quirk
        self.hp = hp
        self.attack = attack

    def attack_villain(self, villain):
        damage = random.randint(1, self.attack)
        villain.hp -= damage
        print(f"{self.name} attacks {villain.name} with {self.quirk} for {damage} damage!")

class Villain:
    def __init__(self, name, hp, attack):
        self.name = name
        self.hp = hp
        self.attack = attack

    def attack_hero(self, hero):
        damage = random.randint(1, self.attack)
        hero.hp -= damage
        print(f"{self.name} attacks {hero.name} for {damage} damage!")

def main():
    print("Welcome to Hero Academia Battle Simulator!")
    hero_name = input("Enter your hero's name: ")
    hero_quirk = input("Enter your hero's quirk: ")
    hero_hp = 100
    hero_attack = 20
    hero = Hero(hero_name, hero_quirk, hero_hp, hero_attack)

    villain = Villain("Villain", 50, 10)

    print(f"A wild {villain.name} appears!")

    while hero.hp > 0 and villain.hp > 0:
        print(f"\n{hero.name}'s HP: {hero.hp}")
        print(f"{villain.name}'s HP: {villain.hp}")

        action = input("\nEnter 'a' to attack the villain or 'r' to run: ")

        if action == 'a':
            hero.attack_villain(villain)
            if villain.hp <= 0:
                print(f"{villain.name} has been defeated!")
                break
            villain.attack_hero(hero)
            if hero.hp <= 0:
                print(f"{hero.name} has been defeated! Game Over!")
                break
        elif action == 'r':
            print("You ran away from the battle. Game Over!")
            break
        else:
            print("Invalid input. Try again!")

if __name__ == "__main__":
    main()
