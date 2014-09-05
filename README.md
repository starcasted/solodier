solodier
========

solodier v1.1


#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

int main()
{
    bool tutorial=1,gameEnd=0,story1=1,monsterEncounter,death=0;
    int maxHealth=100,health=maxHealth,lvl=1,expReq=lvl*15+lvl*lvl/lvl*3,exp=0,expPercentage,attack=15/*,defend=5,defendTurn=0,critical=5,accuracy=100*/,input,monsterType,monsterAttack,monsterHealth,monMaxHealth,monHealthPercentage,healthPercentage,countBar=10,runChance=0;
    int monster[]={/*1*/20,5,15,/*2*/25,10,25,/*3*/30,15,40,/*4*/100,15,70,/*5*/45,25,65,/*6*/55,30,80};
    while(gameEnd==0){
    if(tutorial==1){
        printf("Years ago, there was a planet named Darth.\n\n\n");
        printf("However,an experimental mistake in planet Mystique caused Darth to be demolished...\n\n\n");
        printf("The Darths have nowhere to go, and thus invaded Mystique in anger.\n\n");
        printf("Mystique was not able to defend herself, and soon, Darth took over.\n\n\n\nENTER TO CONTINUE...\n\n");
        getchar();
        printf("All the Mystiquz died, except for one...");
        printf("\n\n\n\n\n\n\n\n\n\n\n\t\t\t\tSOLODIER\n\n\n\n\n\n\n\n\n\n\n\n");
        tutorial=0;
    }
    if(story1==1){
        printf("ENTER TO CONTINUE...");
        getchar();
        getchar();
        printf("You woke up, finding yourself in a land completely wrecked,\n\n\tand covered with debris all around.\n\n");
        printf("Soon, you hear loud roar.\n\n\tBefore you could react, it was too late...\n\n\t");
        printf("Quickly, you picked up a nearby stick to defend yourself...\n");
        monsterType=1;
        monsterEncounter=1;
        story1=0;
    }
    if(monsterEncounter==1){
        monsterHealth=monster[monsterType*3-3];
        monsterAttack=monster[monsterType*3-2];
        monMaxHealth=monsterHealth;
        printf("ENTER TO CONTINUE...\n\n");
        getchar();
        getchar();
        while(monsterHealth>0&&death!=1){
        monHealthPercentage=monsterHealth*10/monMaxHealth;
        printf("Monster Health left -- <");
        while(monHealthPercentage!=0){
            printf("-");
            monHealthPercentage--;
        }
        monHealthPercentage=monsterHealth*10/monMaxHealth;
        while(countBar-monHealthPercentage!=0){
            printf(" ");
            countBar--;
        }
        printf(">  %d / %d\nYour Health left -- <",monsterHealth,monMaxHealth);
        countBar=10;
        healthPercentage=health*10/maxHealth;
        while(healthPercentage!=0){
            printf("-");
            healthPercentage--;
        }
        healthPercentage=health*10/maxHealth;
        while(countBar-healthPercentage!=0){
            printf(" ");
            countBar--;
        }
        printf(">   %d / %d",health,maxHealth);
        countBar=10;
        printf("\n\n<1>Attack!\n<2>Defend!/*Not available*/\n<3>Skill Attack!/*Not available*/\n<4>Run!\n\n\n");
        scanf("%d",&input);
        if(input==1){
            monsterHealth-=attack;
            printf("You attacked the monster, dealing %d damage!!\n\n",attack);
        }
        else if(input==2||3){
            printf("Blah blah\n\n");
        }
        else if(input==4&&runChance==0){
            printf("You cant run!\n\n");
        }
        else{
            printf("You fumbled.\n\n");
        }
        printf("The monster attacked you, dealing %d damage!!\n\n",monsterAttack);
        health-=monsterAttack;
        if(health<=0){
            printf("You died!\n");
            death=1;
        }
        if(monsterHealth<=0){
            printf("You defeated the monster, gaining %d exp!",monster[monsterType*3-1]);
            exp+=monster[monsterType*3-1];
            if(exp>=expReq){
                exp-=expReq;
                lvl++;
                printf("You've became stronger!!\n");
                attack+=2;
                maxHealth+=5;
                expReq=(lvl*15)+(lvl*lvl)/(lvl*3);
            }
        printf("\n\nYour exp  -- <");
        expPercentage=exp*10/expReq;
        while(expPercentage!=0){
            printf("-");
            expPercentage--;
        }
        expPercentage=exp*10/expReq;
        while(countBar-expPercentage!=0){
            printf(" ");
            countBar--;
        }
        printf(">  %d / %d\n\n",exp,expReq);
        countBar=10;
        }
        }
        monsterEncounter=0;
        if(death==1){
            printf("You woke up, lucky to have survived.\n\nQuickly,you took a rest and regained health.\n\n\t\tHealth --> %d",maxHealth);
        }
        health=maxHealth;
        printf("<1>Easy Dungeon!\n<2>Cave...\n<3>Fire Dungeon...\n<4>Derp Derp!!\n<5>Hibernate~~(Exit Game)");
        scanf("%d",&input);
        if(input==1){
            monsterEncounter=1;
            monsterType=1;
        }
        else if(input==2){
            monsterEncounter=1;
            monsterType=2;
        }
        else if(input==3){
            monsterEncounter=1;
            monsterType=4;
        }
        else if(input==4){
            printf("Lol.\n");
        }
        else if(input==5){
            gameEnd=1;
            printf("Are you sure? Type 1 for yes.");
            scanf("%d",&input);
            if(input!=1){
                gameEnd=0;
            }
        }
        else printf("Blah Blah Blah.");
        getchar();
    }
    }
    return 0;
}
