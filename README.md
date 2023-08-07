# booking
movie ticket booking
#include<stdio.h>
#include<stdlib.h>
#include<strings.h>
//int changeprize(int);
void reservation(int *,int,int );
int choice1();
void cancel(int *);        
void ticket1(int choice,char name[10],int id2,int price);
void ticket2(int choice,char name[10],int id2,int price);
void ticket3(int choice,char name[10],int id2,int price);
int cmovie();
int movie();

struct moviedetails
{
	char name[25];
	char phone[15];
	int seat;
	int id;
};

struct moviedetails person[300];
int count=0;
int id2=1000;
int main()
{
	int **seat,choice,price=500,slection,i;
	seat=(int **)calloc(3,sizeof(int *));
	for (i=0;i<3;i++)
		*(seat+i)=(int *)calloc(101,sizeof(int));
	int x = 0;
	while(x!=3)
	{
		choice=choice1();
		switch(choice)
		{
			
		
			case 1:	
				slection=movie();
				reservation(seat[slection-1],price,slection);	
				count++;
				break;
			case 2:
				slection=cmovie();	
				cancel(seat[slection-1]);	
				break;
			case 3:
				x=3;
				break;
			default: 
				printf("Choice not available\n");
				break;	
		}
	}
}

void reservation(int *array,int price,int slection)
{          
		int i,j;
		printf("\n                                SCREEN\n\n\n");
		for (i=1;i<=100;i++)
		{
			if (array[i]==0)
				printf("%d\t",i);
			else 
				printf("*\t",i);	
			if(i%10==0)
				printf("\n\n");
		}
		printf("Please enter your name: ");
		scanf(" %19[^\n]%*[^\n]",&person[count].name);
		printf("Please enter your phone number: ");
		scanf("%u",&person[count].phone);
		printf("Which seat number you want? ");
		scanf("%d",&j);
		if (j>100||j<1)
			{
				printf("seat1 number is unavailable in this theater\n");
				printf("Please re-enter seat number: ");
				scanf("%d",&j);
			}
		if (array[j]==1)
			{
				printf("Sorry, this ticket is already booked! Please choose another seat.\n");
				scanf("%d",&j);
			}
		else			
			array[j]=1;
		person[count].seat=j;
		if (slection==1)
			ticket1(j,person[count].name,id2,price);
		else if (slection==2) 	
			ticket2(j,person[count].name,id2,price);
		else 
			ticket3(j,person[count].name,id2,price);			
		id2++;	
}
int choice1()
{
	int choice;
	printf("                 Simple Movie Ticket Booking System\n");
	printf(" ==================================================================\n");
	printf("||             1- To puchase ticket:                              ||\n");
	printf("||             2- To cancel the seat:                             ||\n");
	printf("||             3- Exit system:                                    ||\n");
	printf("||================================================================||\n");
	printf("  Enter your choice: ");
	scanf("%d",&choice);
	return choice;
}
void cancel(int *array)
{
      int Cseat,i,stop;
	  printf("Please enter ID number of ticket: ");
	  scanf("%d",&Cseat);
	  for (i=0;i<100;i++)
	  {
	  		if(Cseat==person[i].id)
	  		{
					 stop=5;
					 printf("%s your seat is %d cancelled",person[i].name,person[i].seat);
					 array[person[i].seat]=0;
					 i=100;
	  		}
	  }
	  if (stop!=5)	
	  		printf("Ticket ID number is incorrect please enter right one to cancel ticket: \n");
}
void ticket1(int choice,char name[10],int id2,int price)
{
		system("cls");
		printf("\n\n");
        printf("\t-----------------THEATER BOOKING TICKET----------------\n");
        printf("\t============================================================\n");
        printf("\t Booking ID : %d \t\t\tShow Name : Avengers: EndGame\n",id2);
        printf("\t Customer  : %s\n",name);
        printf("\t\t\t                              Date      : 29-04-2023\n");
        printf("\t                                              Time      : 08:00pm\n");
        printf("\t                                              Hall      : 02\n");
        printf("\t                                              seats No. : %d  \n",choice);
        printf("\t                                              price . : %d  \n\n",price);
		person[count].id=id2;
        printf("\t============================================================\n");
        return;
}

int movie()
{
	int i;
	printf("\t\t\twhich movie you want to see?\n");
	printf("\t\t\t----------------------------\n\n");
	printf("\t\t\tpress 1 for Avengers: EndGame\n\n");
	printf("\t\t\tpress 2 for Captain Marvel\n\n");
	printf("\t\t\tpress 3 for Spider-Man: Far From Home\n");
	scanf("%d",&i);
	return i;
}
void ticket2(int choice,char name[10],int id2,int price)
{
		system("cls");
		printf("\n\n");
        printf("\t-----------------THEATER BOOKING TICKET----------------\n");
        printf("\t============================================================\n");
        printf("\t Booking ID : %d \t\t\tShow Name : Captain Marvel\n",id2);
        printf("\t Customer  : %s\n",name);
        printf("\t\t\t                              Date      : 15-04-2019\n");
        printf("\t                                              Time      : 09:00pm\n");
        printf("\t                                              Hall      : 03\n");
        printf("\t                                              seats No. : %d  \n",choice);
        printf("\t                                              price . : %d  \n\n",price);
        person[count].id=id2;
        printf("\t============================================================\n");
        return;
}
int cmovie()
{
	int i;
	printf("\t\t\twhich movie ticket you want to cancel\n");
	printf("\t\t\t-------------------------------------\n");
	printf("\t\t\tpress 1 for Avengers: EndGame\n\n");
	printf("\t\t\tpress 2 for Captain Marvel\n\n");
	printf("\t\t\tpress 3 for Spider-Man: Far From Home\n");
	scanf("%d",&i);
	return i;		
}
void ticket3(int choice,char name[10],int id2,int price)
{
		system("cls");
		printf("\n\n");
        printf("\t-----------------THEATER BOOKING TICKET----------------\n");
        printf("\t============================================================\n");
        printf("\t Booking ID : %d \t\t\tShow Name : Spider-Man: Far From Home \n",id2);
        printf("\t Customer  : %s\n",name);
        printf("\t\t\t                              Date      : 5-07-2019\n");
        printf("\t                                              Time      : 10:00pm\n");
        printf("\t                                              Hall      : 04\n");
        printf("\t                                              seats No. : %d  \n",choice);
        printf("\t                                              price . : %d  \n\n",price);
        person[count].id=id2;
        printf("\t============================================================\n");
        return;
}

