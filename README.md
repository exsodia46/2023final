#include<iostream>
#include<Windows.h>
using namespace std;

void BattleSystem();
int MonsterGen();
int insanity = 0;

string inventory[10] = { "flashlight", " ", " ", " ", " ", " ", " ", " ", " ", " "};


void itemDropper();

int main() {
    srand(time(NULL));
    int room = 1;
    char input = 'a';
 
    //this sets each slot of inventory to " "
    //for (int i = 0; i < 10; i++) 
        //inventory[i] = " ";

    cout << "you were walking down the near by river before falling through a ditch in the ground." << endl;
    
    
   

    while (input != 'q' && insanity >= 0) {

        cout << "your inventory:" << endl;
        for (int i = 0; i < 5; i++)
            cout << inventory[i] << " ";
        cout << endl;

        switch (room) {
        case 1:system("color C0");
            cout << "you begin in a concrete dome with only one caged window , you can go (W)est" << endl;
            cout << "don't forget to (s)earch every room" << endl;
            if (inventory[1] != "key")
                cout << "you see a shiny (k)ey on the ground." << endl;
            cin >> input;

            if (input == 'w')
                room = 2;
            if (input == 'k') {
                cout << "you got a shiny key!" << endl;
                inventory[1] = "key";
            }
      
            break;
        case 2:system("color C0");
            cout << "theres is a locked door in your path. you can go (w)est or (e)ast" << endl;
            cin >> input;
            if (input == 'w')
                if (inventory[1] == "key") {
                    room = 3;
                    cout << "the door is unlocked" << endl;
                }
            else 
                cout << "door is locked. you suck martin" << endl;
                  
        
            
            if (input == 'e')
                room = 1;
               

            
          
                
            break;
        case 3:system("color C0");
            BattleSystem();
            cout << " you walk through the door before it shuts behind you. the only direction is forwerd. you can go (w)est" << endl;
            cin >> input;
            if (input == 'w')
                room = 4;
            
            break;
        case 4:system("color C0");
             
            cout << "you enter a room that has three doors, (r)ed, (b)lue, and (y)llow door" << endl;
            cin >> input;
            if (input == 'r')
                room = 5;
            if (input == 'b')
                room = 6;
            if (input == 'y')
                room = 7;

            break;
        case 5: system("color 0B");
            cout << "you enter the red room. the room is dark filled with mysteries. the red door shuts locking you inside. (n)orth is the only way now" << endl;
            cin >> input;
            if (input == 'n')
                room = 8;

            break;
        case 6:
            cout << "you you enter the blue door" << endl;
            cout << "its the bucther room, theres meat and rotton flesh on the walls and ground." << endl;
            cout << "there is a bundle of flesh tied together making a door. you can go (s)outh or go through the (f)lesh." << endl;
            cin >> input;
            if (input == 's')
                room = 9;
            if (input == 'f')
                room = 7;

            break;
        case 7:system("color AB");
            cout << "you enter a light room with grass and roots growing from the walls crack, a gecko climbs on your shoulder." << endl;
            cout << "you can(p)et." << endl;
            cout << " you can(e)ast or go through the(f)lesh room" << endl;
            cin >> input;
            if (input == 'p')
                cout << "the gecko enjoys the pet" << endl;
            if (input == 'e')
                room = 10;
            if (input == 'f')
                room = 6;
            if (input )
            break;
        case 8:
            system("color 0B");
            cout << "you pull out your flash light and point it at a wall. there's writing on the wall and it spells out: subject 087 is coming." << endl;
            cout << "you notice a trail of blood leading to a large door made of what it seems to be made titanium" << endl;
            cout << "you can go (n)orth" << endl;
            cin >> input;
            if (input == 'n')
                room = 11;
            if (input == 's')
                cout << "you find a journal with the title: Daves sightings" << endl;
                cout << "the journal is missing pages but there is one" << endl;
                cout << "page one: the boss started talking to some rich guy about a new projects called: unknown soliders." << endl;
                cout << "kim has been voted to feed the mutated allgators afters being caught taking one of the mutated capybaryas" << endl;
                cout << "this lab has been experimenting on poor animles, soon it will be us like those aliens they have been hiding from us" << endl; 
            if (input == 's') {
                cout << "you got the fisrt pages" << endl;
                inventory[2] = "page1";
            }
            break;

        case 9: 
            cout << "the smell of death and suffering fills your noise" << endl;
            cout << "you should leave before the maggets get you. you can go (s)outh" << endl;
            cin >> input;
            if (input == 's')
                room = 12;


        case 10:
            cout << "the gecko has now joined your group." << endl; 
            cout << "you and the gecko walk through the life filled hallway before hearing a yell from the other side" << endl;
            cin >> input; 
            if (input == 's')
                room = 13;
        }
    }
}


void BattleSystem() {
    int MonsterType = MonsterGen();
    int MonsterHealth = 20;
    int MonsterDmg = 0;
    int PlayerDmg = 0;

    //reset monster health and dmg based on the monster generated
    if (MonsterType == 1) {
        MonsterHealth = 30;
    }
    if (MonsterType == 2) {
        MonsterHealth = 7;
    }

    if (MonsterType == 1) {
        MonsterDmg = rand() % 20 + 1;
    }

    if (MonsterType == 2) {
        MonsterDmg = rand() % 7 + 10;
    }

    if (MonsterType == 3) {
        MonsterDmg = rand() % 6 + 5;
    }


  
        insanity += MonsterDmg;
        system("pause");
        cout << "your inanity is now " << insanity << endl;
        system("pause");

        if (insanity < 100)
            cout << "the dave leaves you but not for long" << endl;
        else {
            cout << "the dave kills you" << endl;
            //daveExists = true;
        }

}



int MonsterGen() {
    int num = rand() % 100;
    if (num < 100) {
        cout << "" << endl;
        cout << "       _" << endl;
        cout << "      | |" << endl;
        cout << "    __| | __ ___   _____" << endl;
        cout << "A  / _` |/ _`\\ \\ / / _ \\"  << endl;
        cout << "  | (_| | (_||\\ V /  __/ " << endl;
        cout << "   \\__,_|\\__,_|\\_/ \\___|  appeared   " << endl;
        return 1;
    }
}
