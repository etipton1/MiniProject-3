# MiniProject-3
Mini Project 3 - Final - "Toll Roads"


/******************************************************************************
Elijah Tipton
December 15, 2020
ELET 1102-001
Project#3 Toll Roads
This code calculates the toll amount for travel along a toll road or toll lane. 
The toll amount is based on the time of time, day of the week, 
(and number of persons in the vehicle + 5 Bonus points.  For 3 or more people 
in the card, the driver will receive a $0.50 discount of the total price). 
*******************************************************************************/
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main()
{
    int MilitaryTime;
    int StandardTime;
    double StartExit;
    double EndExit;
    double VehicleCapacity;
    double ExitTotal;
    double InitialAmount = 33.33;
    double TotalCharge;
    double RemainingAmount;
    double Weekday;
    double Weekend_Holiday;
    char Day[5];
    
    printf("Your Carolinas Quick Pass has $%lf in it.\n", InitialAmount); //Initail Amount of Money in your Quick Pass//
    printf("Is it a holiday or a weekend?(Yes Or No): "); //Simple Yes or No Because Holiday and Weekend Varies//
    scanf("%s", Day);
    
    printf("What time did you start driving? (Please enter Military Time as HHMM): "); //Start Time in Military Time//
    scanf("%d", &MilitaryTime);
    
    printf("What exit number did you merge onto the Toll Road from?(1-25) "); //Starting Exit//
    scanf("%lf", &StartExit);
    printf("What exit number did you take off the Toll Road?(1-25) "); //Ending Exit//
    scanf("%lf", &EndExit);
    ExitTotal = ((abs(EndExit - StartExit)) * .10); //Total Amount of Exits Traveled//
    
    printf("How many people are in the vehicle? ");
    scanf("%lf", &VehicleCapacity);
    if(VehicleCapacity >= 3) //A What if to determine if there is a $0.50 dicount//
    {
        VehicleCapacity = .50;
        printf("\n\nCongrats you get a $.50 discount off your total price");
    }
    else
    {
        VehicleCapacity = 0;
    }
    if(strcmp(Day, "No") == 0) //Varoius Total Charge outcomes when traveling on a weekday//
    {
        if(MilitaryTime >= 0000 && MilitaryTime <= 559)
        {
            Weekday = 1.55;
        }
        else if(MilitaryTime >= 600 && MilitaryTime <= 959)
        {
            Weekday = 2.65;
        }
        else if(MilitaryTime >= 1000 && MilitaryTime <= 1759)
        {
            Weekday = 2.35;
        }
        else if(MilitaryTime >= 1800 && MilitaryTime <= 2459)
        {
            Weekday = 1.25;
        }
        
        RemainingAmount = InitialAmount - ((Weekday + ExitTotal) - VehicleCapacity);
        TotalCharge = Weekday + ExitTotal;
    }
    else if(strcmp(Day, "Yes") == 0) //Varoius Total Charge outcomes when traveling on a weekend or holiday//
    {
        if(MilitaryTime >= 0000 && MilitaryTime <= 759)
        {
            Weekend_Holiday = 1;
        }
        else if(MilitaryTime >= 800 && MilitaryTime <= 959)
        {
            Weekend_Holiday = 2.05;
        }
        else if(MilitaryTime >= 1200 && MilitaryTime <= 1559)
        {
            Weekend_Holiday = 2.45;
        }
        else if(MilitaryTime >= 1600 && MilitaryTime <= 1859)
        {
            Weekend_Holiday = 2.60;
        }
        else if(MilitaryTime >= 1900 && MilitaryTime <= 2159)
        {
            Weekend_Holiday = 2.05;
        }
        else if(MilitaryTime >= 2200 && MilitaryTime <= 2459)
        {
            Weekend_Holiday = .55;
        }
        
        RemainingAmount = InitialAmount - ((Weekend_Holiday + ExitTotal) - VehicleCapacity);
        TotalCharge = Weekend_Holiday + ExitTotal;
    }
    
    printf("\nThe total amount charged is: $%lf\n", TotalCharge); //Total Charge//
    printf("You have $%lf remaining in your Carolinas Quick Pass\n", RemainingAmount); //Remaing Amount left in quick pass//
    
    if(MilitaryTime >= 1300)
    {
        StandardTime = MilitaryTime - 1200;
    }
    else
    {
        StandardTime = MilitaryTime;
    }
    printf("Your Standard Time: %d\n", StandardTime); //The Standard Time//
    
    return 0;
}
