# Team-B
#pragma config(Motor,  port2,           baseLeft,      tmotorVex393_MC29, openLoop, reversed)
#pragma config(Motor,  port3,           baseRight,     tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port4,           claw,          tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port5,           swingBar,      tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port6,           mobileLeft,    tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port7,           mobileRight,   tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port8,           liftLeft,      tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port9,           liftRight,     tmotorVex393_MC29, openLoop)
//*!!Code automatically generated by 'ROBOTC' configuration wizard               !!*//

/*---------------------------------------------------------------------------*/
/*                                                                           */
/*        Description: Competition template for VEX EDR                      */
/*                                                                           */
/*---------------------------------------------------------------------------*/

// This code is for the VEX cortex platform
#pragma platform(VEX2)

// Select Download method as "competition"
#pragma competitionControl(Competition)

//Main competition background code...do not modify!
#include "Vex_Competition_Includes.c"

/*---------------------------------------------------------------------------*/
/*                          Pre-Autonomous Functions                         */
/*                                                                           */
/*  You may want to perform some actions before the competition starts.      */
/*  Do them in the following function.  You must return from this function   */
/*  or the autonomous and usercontrol tasks will not be started.  This       */
/*  function is only called once after the cortex has been powered on and    */
/*  not every time that the robot is disabled.                               */
/*---------------------------------------------------------------------------*/

void pre_auton()
{
	// Set bStopTasksBetweenModes to false if you want to keep user created tasks
	// running between Autonomous and Driver controlled modes. You will need to
	// manage all user created tasks if set to false.
	bStopTasksBetweenModes = true;

	// Set bDisplayCompetitionStatusOnLcd to false if you don't want the LCD
	// used by the competition include file, for example, you might want
	// to display your team name on the LCD in this function.
	// bDisplayCompetitionStatusOnLcd = false;

	// All activities that occur before the competition starts
	// Example: clearing encoders, setting servo positions, ...
}

/*---------------------------------------------------------------------------*/
/*                                                                           */
/*                              Autonomous Task                              */
/*                                                                           */
/*  This task is used to control your robot during the autonomous phase of   */
/*  a VEX Competition.                                                       */
/*                                                                           */
/*  You must modify the code to add your own robot specific commands here.   */
/*---------------------------------------------------------------------------*/

task autonomous()
{

//SensorValue(sensorLift) = 0;
	//int valTime1;//, valTime10, valTime100;  // create three integers to read the value of the timer

//valTime1 = time1[T1];      //Gets the value of Timer T1 in 1ms increments and stores it in a variable
//valTime10 = time10[T1];    //Gets the value of Timer T1 in 10ms increments and stores it in a variable
//valTime100 = time100[T1];  //Gets the value of Timer T1 in 100ms increments and stores it in a variable

//drives forward to the mobile goal
  	motor[baseLeft] = -110;
    motor[baseRight] = 110;
    delay(500);
//goes down
  	motor[liftLeft] = 127 ;
 		motor[liftRight] = 127;
 		delay(500);
//drive forward
    motor[baseLeft] = -110;
    motor[baseRight] = 110;
    delay(500);
 //lift up
	  motor[liftRight] = 127;
	  motor[liftLeft] = 127;
	  delay(500);
 //turn around
		motor[baseLeft] = -120;
		motor[baseRight] = 120;
		delay(500);
		// drive to scoring zone
   	  motor[baseLeft] = -110;
    	motor[baseRight] = 110;
    	delay(500);
}

/*---------------------------------------------------------------------------*/
/*                                                                           */
/*                              User Control Task                            */
/*                                                                           */
/*  This task is used to control your robot during the user control phase of */
/*  a VEX Competition.                                                       */
/*                                                                           */
/*  You must modify the code to add your own robot specific commands here.   */
/*---------------------------------------------------------------------------*/

task usercontrol()
{
	// User control code here, inside the loop

	while (true)
	{
		motor[baseLeft] = vexRT[Ch2];
		motor[baseRight]= vexRT [Ch3];

		if(vexRT[Btn5U] == 1)
		{

			motor[liftLeft] = 100;
			motor[liftRight] = -100;
		}
		else if(vexRT[Btn6U] == 1)
		{
			motor[liftLeft] = -100;
			motor[liftRight] = 100;
		}
		else
		{
			motor[liftLeft] = 0;
			motor[liftRight] = 0;
		}

		if(vexRT[Btn5D] == 1)
		{
			motor[mobileLeft] = 127;
			motor[mobileRight] = -127;
		}
		else if(vexRT[Btn6D] == 1)
		{
			motor[mobileLeft]= -127;
			motor[mobileRight]= 127;
		}
		else
		{
			motor[mobileLeft]=0;
			motor[mobileRight]=0;
		}
		if(vexRT[Btn8U] ==1)
		{
			motor[swingBar] = 127;
		}
		else if(vexRT[Btn8D] == 1)
		{
			motor[swingBar] = -127;
		}
		else
		{
			motor[swingBar] = 0;
		}
		if(vexRT[Btn7U] == 1)
		{
			motor[claw] = 127;
		}
		else if(vexRT[Btn7D] == 1)
		{
			motor[claw] = -127;
		}
		else
		{
			motor[claw] = 0;
		}

	}

}
