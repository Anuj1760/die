#include<iostream.h> 
#include<conio.h>
#include<stdlib.h>
void dice_cpy(char x[5][7],char y[5][7])
{  for (int i=0;i<5;i++)
      for (int j=0;j<7;j++)
         x[i][j]=y[i][j];
}
void main()
{  clrscr();
   char one[5][7]={{"ÚÄÄÄÄÄ¿"},
                   {"³     ³"},
                   {"³  ù  ³"},
                   {"³     ³"},
                   {"ÀÄÄÄÄÄÙ"}};
   char two[5][7]={{"ÚÄÄÄÄÄ¿"},
                   {"³ù    ³"},
                   {"³     ³"},
                   {"³    ù³"},
                   {"ÀÄÄÄÄÄÙ"}};
   char three[5][7]={{"ÚÄÄÄÄÄ¿"},
                     {"³ù    ³"},
                     {"³  ù  ³"},
                     {"³    ù³"},
                     {"ÀÄÄÄÄÄÙ"}};
   char four[5][7]={{"ÚÄÄÄÄÄ¿"},
                    {"³ù   ù³"},
                    {"³     ³"},
                    {"³ù   ù³"},
                    {"ÀÄÄÄÄÄÙ"}};
   char five[5][7]={{"ÚÄÄÄÄÄ¿"},
                    {"³ù   ù³"},
                    {"³  ù  ³"},
                    {"³ù   ù³"},
                    {"ÀÄÄÄÄÄÙ"}};
   char six[5][7]={{"ÚÄÄÄÄÄ¿"},
                   {"³ù   ù³"},
                   {"³ù   ù³"},
                   {"³ù   ù³"},
                   {"ÀÄÄÄÄÄÙ"}};
   long money=20000,bet;
   int dc1,dc2,d1,d2;
   char dice[5][15],dice1[5][7],dice2[5][7],ch;
   //FOR ASSIGNING THE SEPERATION PART B/W 2 DICES IN NEW ARRAY
   for (int i=0;i<5;i++)
      dice[i][7]=' ';
   do {
   start:
   clrscr();
   cout<<" Total money = $ "<<money<<endl;
   cout<<" Bet Amount = $ ";
   cin>>bet;
   if (bet<=money)
   {  clrscr();
      cout<<" Bet Amount = $ "<<bet<<endl;
      money=money-bet;
      cout<<" Choice for dice 1 (1,2,3,4,5,6) = ";
      cin>>dc1;
      cout<<" Choice for dice 2 (1,2,3,4,5,6) = ";
      cin>>dc2;
      cout<<endl<<" Press any key to Roll the DICE"<<endl<<endl;
      getch();
      randomize();
      d1=random(6)+1;
      d2=random(6)+1;
      switch (d1)
      {  case 1: dice_cpy(dice1,one);
                 break;
         case 2: dice_cpy(dice1,two);
                 break;
         case 3: dice_cpy(dice1,three);
                 break;
         case 4: dice_cpy(dice1,four);
                 break;
         case 5: dice_cpy(dice1,five);
                 break;
         case 6: dice_cpy(dice1,six);
      }
      switch (d2)
      {  case 1: dice_cpy(dice2,one);
                 break;
         case 2: dice_cpy(dice2,two);
                 break;
         case 3: dice_cpy(dice2,three);
                 break;
         case 4: dice_cpy(dice2,four);
                 break;
         case 5: dice_cpy(dice2,five);
                 break;
         case 6: dice_cpy(dice2,six);
      }
      //FOR ASSIGNING DICE ARRAY IN NEW ARRAY[5][15]
      for (int i=0;i<5;i++)
      {  for (int j=0;j<7;j++)
         {  dice[i][j]=dice1[i][j];
            dice[i][j+8]=dice2[i][j];
         }
      }
      for (int i=0;i<5;i++)
      {  for (int j=0;j<15;j++)
         {  cout<<dice[i][j];
         }
         cout<<endl;
      }
      //Checking for win
      if ((d1==dc1 && d2==dc2) || (d1==dc2 && d2==dc1))
      {  cout<<endl<<" You WIN $ "<<bet;
         money=money+(2*bet);
         cout<<endl<<" Total Money = $ "<<money<<endl;
      }
      else
      {  cout<<endl<<" You LOSE $ "<<bet;
         cout<<endl<<" Total Money = $ "<<money<<endl;
      }
      cout<<endl<<" Do you want to play again (Y/N) : ";
      cin>>ch;
   }
   else
   {  cout<<endl<<" Bet can not be more than total money"<<endl;
      cout<<" Press any key to continue...";
      getch();
      goto start;
   }
   } while (ch=='y' || ch=='Y');
}
