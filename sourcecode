#include<stdio.h>
#include<stdlib.h>
#include<GL/glut.h>
#include<math.h>
#include<time.h>
int flag = 0;//Used to control what items to be displayed on the screen.
int select = 0;//Indicates the direction bomb.
float j = 0;//For translating the bomb.(x)
float k = 0;//For translating the bomb.(y)
int cselect;//This is used for monster movement and it is selected randomly by the system.
int count = 0;//Used to restrict the number of shoots to 6.
int supercount = 0;//For controlling player 1 and player 2 conditions.
GLint goalscored1 = 0;//Displays goalscored by player 1
float g1 = 0;//To display player 1  results at last
float g2 = 0;//To display player 2  results at last
GLint goalscored2 = 0;//Displays goalscored by player 2
char p1[5] = { 0,0,0,0,0 };//displaying player 1 score on to scoreboard
char p2[5] = { 0,0,0,0,0 };//displaying player 1 score on to scoreboard
char p3[5] = { 0,0,0,0,0 };//Shoot number
char n1[5] = { 0,0,0,0,0 };
char n2[5] = { 0,0,0,0,0 };
int l = 1;//indicates level
void display();
void myinit()
{
	glMatrixMode(GL_PROJECTION);
	glLoadIdentity();
	gluOrtho2D(0, 500, 0, 500);
	glMatrixMode(GL_MODELVIEW);
}
void print(const char *a, float x, float y)//For displaying text on the screen at required position.
{
	glRasterPos2f(x, y);//It is used to position pixel and bitmap write operations. 
	for (int i = 0; a[i] != '\0'; i++)
	{
		glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24, a[i]);//
	}
	//glutBitmapCharacter renders the character in the named bitmap font. 
	//A bitmap is a rectangular array of Os and Is that serves as a drawing mask for a rectangular portion of the window.
}
void monster()//For displaying the monster.
{
	float x, y; float r=0,g=0,b=0;
	if (l == 1)
		r = 0.7;
	else
	{
		b = 0;
		g = 0.3;
		r = 0.4;
	}
	glColor3f(1, 0, 0);
	//monster's leg
	glBegin(GL_POLYGON);
	glVertex2f(230, 255);
	glVertex2f(235, 255);
	glVertex2f(250, 310);
	glEnd();
	glBegin(GL_POLYGON);
	glVertex2f(265, 255);
	glVertex2f(270, 255);
	glVertex2f(250, 310);
	glEnd();
	//monster's horn
	glBegin(GL_POLYGON);
	glVertex2f(245, 360);
	glVertex2f(233, 385);
	glVertex2f(240, 350);
	glEnd();
	glBegin(GL_POLYGON);
	glVertex2f(245, 360);
	glVertex2f(250, 400);
	glVertex2f(255, 360);
	glEnd();
	glBegin(GL_POLYGON);
	glVertex2f(253, 355);
	glVertex2f(268, 385);
	glVertex2f(260, 350);
	glEnd();
	glBegin(GL_POLYGON);
	glVertex2f(260, 348);
	glVertex2f(280, 345);
	glVertex2f(260, 332);
	glEnd();
	glBegin(GL_POLYGON);
	glVertex2f(240, 348);
	glVertex2f(220, 345);
	glVertex2f(240, 332);
	glEnd();
	glColor3f(r, g, b);//monster's head
	glBegin(GL_TRIANGLE_FAN);
	for (float i = 0; i <= 20; i++)
	{

		x = cos(i * 2 * 3.142 / 20) * 15;
		y = sin(i * 2 * 3.142 / 20) * 25;
		glVertex2f(x + 250, y + 340);

	}
	glEnd();
	glColor3f(r, g, b);//body
	glBegin(GL_TRIANGLE_FAN);
	for (float i = 0; i <= 20; i++)
	{

		x = cos(i * 2 * 3.142 / 20) * 20;
		y = sin(i * 2 * 3.142 / 20) * 40;
		glVertex2f(x + 250, y + 300);

	}
	glEnd();


	glColor3f(1, .5, 0);
	glBegin(GL_TRIANGLE_FAN);//eye
	for (float i = 0; i <= 360; i++)
	{

		x = cos(i * 2 * 3.142 / 20) * 6;
		y = sin(i * 2 * 3.142 / 20) * 9;
		glVertex2f(x + 250, y + 345);

	}
	glEnd();
	glColor3f(0, 0, 0);
	glBegin(GL_TRIANGLE_FAN);//eye pupil
	for (float i = 0; i <= 360; i++)
	{

		x = cos(i * 2 * 3.142 / 20) * 2;
		y = sin(i * 2 * 3.142 / 20) * 6;
		glVertex2f(x + 250, y + 345);

	}
	glEnd();

}
void firstdisp()//Welcome text
{
	glBegin(GL_POLYGON);
	glColor3f(0.8, 0.5, 0);
	glVertex2f(0, 0);
	glColor3f(0, 0.5, 0.5);
	glVertex2f(0, 500);
	glColor3f(0, 0.5, 0.5);
	glVertex2f(500, 500);
	glColor3f(0.8, 0.5, 0);
	glVertex2f(500, 0);
	glEnd();

	glColor3f(0,0,0);
	print("RNS INSTITUTE OF TECHNOLOGY,BANGALORE", 140, 450);
	print("COMPUTER GRAPHICS AND VISUALIZATION MINI PROJECT", 120, 430);
	glColor3f(1, 1, 1);
	print("***THE MONSTER SHOOTOUT***", 180, 380);
	glLineWidth(2);
	glBegin(GL_LINES);
	{
		glVertex2f(170, 377);
		glVertex2f(328, 377);
	}
	glEnd();
	print("ABOUT THE GAME", 80, 330);
	print("-->The monster is roaming inside the city and causing lot of chaos.", 80, 300);
	print("-->The old magician living in the hilltop castle of the city has designed the bomb to shoot monster.", 80, 280);
	print("-->Monster moves randomly. Player will be the shooter and gets to decide the direction of bomb.", 80, 260);
	print("-->There will be two levels.Level 2 will have penalty.", 80, 240);
	print("-->Each player in each level has 6 chances.", 80, 220);
	print("-->If the bomb hits monster,player scores.", 80, 200);
	print("-->The one who shoots more, will be declared the winner.", 80, 180);
	print("--Press Enter Key to start the game.--", 180, 160);
	glColor3f(0, 0, 0);
	print("Project by", 300, 90);
	print("Ramya Ganesh Bhat (1RN15CS086)", 280, 60);
}
void boundary()//To display the boundaries of the ground.
{

	glColor3f(0.196078, 0.6, 0.8);
	glBegin(GL_POLYGON);//sky
	glVertex2f(0, 352);
	glVertex2f(500, 352);
	glVertex2f(500, 500);
	glVertex2f(0, 500);
	glEnd();

	glColor3f(0.32, 0.32, 0.32);//road
	glBegin(GL_POLYGON);
	glVertex2f(0, 0);
	glVertex2f(200, 352);
	glVertex2f(300, 352);
	glVertex2f(500, 0);
	glEnd();

	glColor3f(1, 1, 1);
	glLineWidth(10);
	glColor3f(0.1, 0.4, 0.2);
	glBegin(GL_POLYGON);//building1
	glColor3f(0.1, 0.4, 0.2);
	glVertex2f(0, 352);
	glColor3f(0.1, 0.4, 0.2);
	glVertex2f(0, 482);
	glColor3f(0.3, 0.6, 0.0);
	glVertex2f(90, 482);
	glColor3f(0.3, 0.6, 0.0);
	glVertex2f(90, 352);
	glEnd();
	glLineWidth(20);
	glColor3f(1, 1, 1);
	glBegin(GL_LINES);//inner D
	glColor3f(1, 1, 0);
	glVertex2f(50, 362);
	glColor3f(1, 1, 1);
	glVertex2f(70, 362);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(50, 462);
	glColor3f(1, 1, 1);
	glVertex2f(70, 462);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(20, 402);
	glColor3f(1, 1, 1);
	glVertex2f(40, 402);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(50, 402);
	glColor3f(1, 1, 1);
	glVertex2f(70, 402);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(20, 462);
	glColor3f(1, 1, 1);
	glVertex2f(40, 462);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(20, 362);
	glColor3f(1, 1, 1);
	glVertex2f(40, 362);
	glEnd();


	glBegin(GL_POLYGON);//building2
	glColor3f(0.7, 0.2, 0.4);
	glVertex2f(190, 352);
	glColor3f(0.7, 0.2, 0.4);
	glVertex2f(190, 452);
	glColor3f(0.9, 0.2, 0.2);
	glVertex2f(120, 452);
	glColor3f(0.9, 0.2, 0.2);
	glVertex2f(120, 352);
	glEnd();
	glLineWidth(20);
	glColor3f(1, 1, 1);
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(130, 442);
	glColor3f(1, 1, 1);
	glVertex2f(150, 442);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(160, 402);
	glColor3f(1, 1, 1);
	glVertex2f(180, 402);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(130, 382);
	glColor3f(1, 1, 1);
	glVertex2f(150, 382);
	glEnd();


	glBegin(GL_POLYGON);//building3
	glColor3f(0.5, 0.1, 0.4);
	glVertex2f(310, 352);
	glColor3f(0.5, 0.1, 0.4);
	glVertex2f(310, 452);
	glColor3f(0.8, 0.5, 0.9);
	glVertex2f(370, 452);
	glColor3f(0.8, 0.5, 0.9);
	glVertex2f(370, 352);
	glEnd();
	glLineWidth(20);
	glColor3f(1, 1, 1);
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(330, 432);
	glColor3f(1, 1, 1);
	glVertex2f(350, 432);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(330, 402);
	glColor3f(1, 1, 1);
	glVertex2f(350, 402);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(330, 372);
	glColor3f(1, 1, 1);
	glVertex2f(350, 372);
	glEnd();


	glBegin(GL_POLYGON);//Building4
	glColor3f(1, 0.75, 0.2);
	glVertex2f(500, 352);
	glColor3f(1, 0.75, 0.2);
	glVertex2f(500, 482);
	glColor3f(0.75, 0.5, 0.0);
	glVertex2f(410, 482);
	glColor3f(0.75, 0.5, 0.0);
	glVertex2f(410, 352);
	glEnd();
	glLineWidth(20);
	glColor3f(1, 1, 1);
	glBegin(GL_LINES);//inner D
	glColor3f(1, 1, 0);
	glVertex2f(450, 362);
	glColor3f(1, 1, 1);
	glVertex2f(470, 362);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(450, 462);
	glColor3f(1, 1, 1);
	glVertex2f(470, 462);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(480, 402);
	glColor3f(1, 1, 1);
	glVertex2f(490, 402);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(450, 402);
	glColor3f(1, 1, 1);
	glVertex2f(470, 402);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(480, 462);
	glColor3f(1, 1, 1);
	glVertex2f(490, 462);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(480, 362);
	glColor3f(1, 1, 1);
	glVertex2f(490, 362);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(420, 402);
	glColor3f(1, 1, 1);
	glVertex2f(440, 402);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(420, 462);
	glColor3f(1, 1, 1);
	glVertex2f(440, 462);
	glEnd();
	glBegin(GL_LINES);
	glColor3f(1, 1, 0);
	glVertex2f(420, 362);
	glColor3f(1, 1, 1);
	glVertex2f(440, 362);
	glEnd();

	glLineWidth(10);
	glColor3f(1, 1, 1);//road lines
	glBegin(GL_LINES);
	glVertex2f(250, 320);
	glVertex2f(250, 290);
	glEnd();
	glLineWidth(13);
	glBegin(GL_LINES);
	glVertex2f(250, 200);
	glVertex2f(250, 250);
	glEnd();
	glLineWidth(16);
	glBegin(GL_LINES);
	glVertex2f(250, 100);
	glVertex2f(250, 160);
	glEnd();
	glLineWidth(22);
	glBegin(GL_LINES);
	glVertex2f(250, 30);
	glVertex2f(250, 0);
	glEnd();
	glColor3f(0, 0, 0);
}
void loader()//bomb loader
{

	glBegin(GL_POLYGON);//base
	glColor3f(0.623529, 0.623529, 0.372549);
	glVertex2f(190, 0);
	glColor3f(0.556863, 0.419608, 0.137255);
	glVertex2f(210, 30);
	glVertex2f(290, 30);
	glVertex2f(310, 0);
	glEnd();
	glBegin(GL_POLYGON);//gun
	glColor3f(0.623529, 0.623529, 0.372549);
	glVertex2f(230, 30);
	glColor3f(0.556863, 0.419608, 0.137255);
	glVertex2f(270, 30);
	glVertex2f(270, 45);
	glVertex2f(230, 45);
	glEnd();
}
void bomb()//To display the bomb on the screen.
{
	float x, y;

	glPushMatrix();
	glColor3f(1, .5, 0);
	glBegin(GL_LINES);//fire
	glVertex2f(256, 79);
	glVertex2f(260, 85);
	glEnd();
	glColor3f(0, 0, 0);
	glBegin(GL_POLYGON);
	glVertex2f(250, 74);
	glVertex2f(254, 81);
	glVertex2f(260, 78);
	glVertex2f(258, 71);
	glEnd();
	glColor3f(0, 0, 0);
	glBegin(GL_TRIANGLE_FAN);//Basic structure
	for (float i = 0; i <= 20; i++)
	{

		x = cos(i * 2 * 3.142 / 20) * 13.5;
		y = sin(i * 2 * 3.142 / 20) * 13.5;
		glVertex2f(x + 250, y + 60);

	}
	glEnd();
	glColor3f(0, 0, 0);
	for (float i = 0; i <= 360; i++)//Outline of bomb
	{
		glColor3f(0, 0, 0);
		glPointSize(1);
		glBegin(GL_POINTS);
		x = cos(i) * 13.5;
		y = sin(i) * 13.5;
		glVertex2f(x + 250, y + 60);
		glEnd();

	}


	glPopMatrix();

}
void scoreboard()
{
	glColor3f(0.6, 0.6, 0.8);
	glBegin(GL_POLYGON);//scoreboard
	glVertex2f(490, 200);
	glVertex2f(400, 200);
	glVertex2f(400, 280);
	glVertex2f(490, 280);
	glEnd();
	glColor3f(0, 0, 0);
	glLineWidth(5);
	glBegin(GL_LINES);//lines inside scoreboard
	glVertex2f(490, 240);
	glVertex2f(400, 240);
	glEnd();
	glLineWidth(5);
	glBegin(GL_LINE_LOOP);//outline of scoreboard
	glVertex2f(490, 200);
	glVertex2f(400, 200);
	glVertex2f(400, 280);
	glVertex2f(490, 280);
	glEnd();
	glColor3f(0.6, 0.6, 0.8);
	glBegin(GL_POLYGON);//scoreboard
	glVertex2f(10, 200);
	glVertex2f(100, 200);
	glVertex2f(100, 280);
	glVertex2f(10, 280);
	glEnd();
	glColor3f(0, 0, 0);
	glBegin(GL_LINES);//lines inside scoreboard
	glVertex2f(100, 240);
	glVertex2f(10, 240);
	glEnd();
	glLineWidth(5);
	glBegin(GL_LINE_LOOP);//outline of scoreboard
	glVertex2f(10, 200);
	glVertex2f(100, 200);
	glVertex2f(100, 280);
	glVertex2f(10, 280);
	glEnd();
	glPointSize(5);
}
void idle()//Idle function used for the movement of the ball.
{
	if (flag == 3)
	{
		if (select == 1)
		{
			j -= 0.55;
			k += 1.9;
			if (j <= 230 && k >= 230)
			{

				j = 0; k = 0; flag = 2;
				for (long int i = 0; i < 10000000; i++);
				glutPostRedisplay();


			}
			else
			{
				glutIdleFunc(idle);
				for (int i = 0; i < 60000; i++);
				glutPostRedisplay();
			}

		}
		if (select == 2)
		{

			k += 1.9;
			if (k >= 230)
			{

				j = 0; k = 0; flag = 2;
				for (long int i = 0; i < 10000000; i++);
				glutPostRedisplay();

			}
			else
			{
				glutIdleFunc(idle);
				for (int i = 0; i < 60000; i++);
				glutPostRedisplay();
			}
		}
		if (select == 3)
		{
			j += 0.55;
			k += 1.9;
			if (j <= 230 && k >= 230)
			{

				j = 0; k = 0; flag = 2;
				for (long int i = 0; i < 10000000; i++);
				glutPostRedisplay();
			}
			else
			{
				glutIdleFunc(idle);
				for (int i = 0; i < 60000; i++);
				glutPostRedisplay();
			}
		}
	}
}
void redisp()//It has all basic items to be displayed again on the screen and the instructions for shooting.
{
	glClearColor(0.0, 0.8, 0.1, 8);
	glClear(GL_COLOR_BUFFER_BIT);
	boundary();
	
	if(count>0)
	{
		glColor3f(0, 0, 0);
		_itoa_s(floor(count), p3, 10);
		print(p3, 275, 440);
		print("SHOT NO:", 220, 440);
		if (count == 6)
		{
			glColor3f(0, 0, 0);
			print("--PRESS ANY ARROW KEY TO CONTINUE--", 160, 180);
		}
	}
	

	if (flag == 1 || flag == 2)
	{
		monster();
		loader();
	}
	glColor3f(.8, 0, .2);
	glBegin(GL_POLYGON);
	glVertex2f(40, 30);
	glVertex2f(40, 120);
	glVertex2f(160, 120);
	glVertex2f(160, 30);
	glEnd();
	glColor3f(0, 0, 0);

	print("Press '<---' key to shoot left", 45, 65);
	print("Press '--->' key to shoot right", 45, 40);
	print("^", 69, 95);
	print("Press '|' key to shoot straight", 45, 90);
	scoreboard();
	glColor3f(1, 0, 0);
	_itoa_s(floor(goalscored1 / 120), n1, 10);
	print(n1, 430, 220);
	_itoa_s(floor(goalscored2 / 120), n2, 10);
	print(n2, 50, 220);
	glColor3f(0, 0, 0);

	print("Score", 430, 290);
	glColor3f(1, 1, 0);
	print("PLAYER 1", 430, 250);
	glColor3f(0, 0, 0);

	print("Score", 40, 290);
	glColor3f(1, 1, 0);
	print("PLAYER 2", 40, 250);

}
void shoot()//It has things to be displayed when a goal is scored.
{
	glBegin(GL_POLYGON);
	glColor3f(.7, 1, 2);
	glVertex2f(200, 455);
	glVertex2f(200, 495);
	glColor3f(.8, 0.4, 2);
	glVertex2f(300, 495);
	glVertex2f(300, 455);
	glEnd();
	glColor3f(0, 1, 0);
	glPointSize(20);
	glColor3f(1, 0, 0);
	print("HIT ! ! ", 230, 470);
	if (supercount == 0)
	{
		goalscored1 += 10;

	}

	else
	{
		goalscored2 += 10;

	}



}
void blocked()//It has things to be displayed when a goal is saved.
{
	glBegin(GL_POLYGON);
	glColor3f(.7, 1, 2);
	glVertex2f(200, 455);
	glVertex2f(200, 495);
	glColor3f(.8, 0.4, 2);
	glVertex2f(300, 495);
	glVertex2f(300, 455);
	glEnd();
	glColor3f(1, 0, 0);
	glPointSize(20);
	print("OH MISSED!", 230, 470);

}
void shoot1()//It has things to be displayed when a goal is scored.
{
	glBegin(GL_POLYGON);
	glColor3f(.7, 1, 2);
	glVertex2f(200, 455);
	glVertex2f(200, 495);
	glColor3f(.8, 0.4, 2);
	glVertex2f(300, 495);
	glVertex2f(300, 455);
	glEnd();
	glColor3f(0, 1, 0);
	glPointSize(20);
	glColor3f(1, 0, 0);
	print("HIT ! ! ", 230, 470);
	if (supercount == 0)
	{
		goalscored1 += 15;

	}

	else
	{
		goalscored2 += 15;

	}



}
void blocked1()//It has things to be displayed when a goal is saved.
{
	glBegin(GL_POLYGON);
	glColor3f(.7, .1, 2);
	glVertex2f(200, 455);
	glVertex2f(200, 495);
	glColor3f(.8, 0.4, 2);
	glVertex2f(300, 495);
	glVertex2f(300, 455);
	glEnd();
	glColor3f(1, 0, 0);
	glPointSize(20);
	print("OH MISSED!", 230, 470);
	if (supercount == 0)
	{
		goalscored1 = goalscored1 - 5;

	}

	else
	{
		goalscored2 = goalscored2 - 5;

	}

}
void Topmenu1(int id)
{
	char p1[5] = { 0,0,0,0,0 };
	char p2[5] = { 0,0,0,0,0 };
	switch (id)
	{
	case 1:flag = 0;
		count = 0;
		supercount = 0;
		goalscored1 = 0;
		goalscored2 = 0;
		l = 1;
		display();
		break;
	case 2:exit(0);
		break;
	}
}
void Topmenu(int id)
{
	char p1[5] = { 0,0,0,0,0 };
	char p2[5] = { 0,0,0,0,0 };
	switch (id)
	{
	case 1:flag = 0;
		count = 0;
		supercount = 0;
		goalscored1 = 0;
		goalscored2 = 0;
		l = 1;
		display();
		break;
	case 2:exit(0);
		break;
	case 3:flag = 1;
		l = 2;
		count = 0;
		supercount = 0;
		display();
		break;
	}
}
void display()//Main display function
{

	if (flag == 0)
	{
		firstdisp();
	}

	if (flag == 1)//After Enter key is pressed.
	{
		glClearColor(0.0, 0.8, 0.1, 8);
		glClear(GL_COLOR_BUFFER_BIT);
		boundary();
		glColor3f(1, 1, 1);
		glBegin(GL_POLYGON);
		glColor3f(.8, 0, 2);
		glVertex2f(200, 255);
		glVertex2f(200, 295);
		glColor3f(.7, 1, 2);
		glVertex2f(300, 295);
		glVertex2f(300, 255);
		glEnd();
		glColor3f(.8, 0, .2);
		if (l == 1)
			print("LEVEL 1", 230, 270);
		else
			print("LEVEL 2", 230, 270);
		if (supercount == 0)
		{
			glColor3f(1, 1, 1);
			glBegin(GL_POLYGON);
			glColor3f(.7, 1, 2);
			glVertex2f(200, 55);
			glVertex2f(200, 95);
			glColor3f(.8, 0, 2);
			glVertex2f(300, 95);
			glVertex2f(300, 55);
			glEnd();
			glBegin(GL_POLYGON);
			glColor3f(.7, 1, 2);
			glVertex2f(200, 455);
			glVertex2f(200, 495);
			glColor3f(.8, 0, 2);
			glVertex2f(300, 495);
			glVertex2f(300, 455);
			glEnd();
			glColor3f(.8, 0, .2);
			print("PLAYER 1", 230, 470);
			print("Press S to start the game", 205, 80);
			print("Press E exit the game", 205, 60);
		}
		else
		{
			glColor3f(1, 1, 1);
			glBegin(GL_POLYGON);
			glColor3f(.7, 1, 2);
			glVertex2f(200, 455);
			glVertex2f(200, 495);
			glColor3f(.8, 0, 2);
			glVertex2f(300, 495);
			glVertex2f(300, 455);
			glEnd();
			glBegin(GL_POLYGON);
			glColor3f(.7, 1, 2);
			glVertex2f(200, 55);
			glVertex2f(200, 95);
			glColor3f(.8, 0, 2);
			glVertex2f(300, 95);
			glVertex2f(300, 55);
			glEnd();
			glColor3f(.8, 0, .2);
			print("PLAYER 2", 230, 470);
			print("Press S to start the game", 205, 80);
		}
	}

	if (flag == 2)//After 'S' key is pressed.
	{
		redisp();
		bomb();
		glutIdleFunc(idle);

		srand(time(NULL));

		cselect = (rand() % 5) + 1;
	}
	if (flag == 3)//After a suitable key is pressed for shooting.
	{
		redisp();

		glPushMatrix();

		if (cselect == 1)//west movement of the monst has been selected.
		{
			glMatrixMode(GL_MODELVIEW);
			glLoadIdentity();
			glTranslatef(-65, 0, 0);
			monster();
			glPopMatrix();
		}
		else if (cselect == 2)//north movement of the monst has been selected.
		{
			glPushMatrix();
			glMatrixMode(GL_MODELVIEW);
			glLoadIdentity();
			glTranslatef(0, 40, 0);
			monster();
			glPopMatrix();

		}
		else if (cselect == 4)//south east movement of the ball has been selected.
		{
			glPushMatrix();
			glMatrixMode(GL_MODELVIEW);
			glLoadIdentity();
			glTranslatef(65, -65, 0);
			monster();
			glPopMatrix();
			//cselect = 3;
		}
		else if (cselect == 5)//south west movement of the ball has been selected.
		{
			glPushMatrix();
			glMatrixMode(GL_MODELVIEW);
			glLoadIdentity();
			glTranslatef(-65, -65, 0);
			monster();
			glPopMatrix();
			//cselect = 1;
		}
		else
		{
			if (cselect == 3)//east has been selected.
			{
				glPushMatrix();
				glMatrixMode(GL_MODELVIEW);
				glLoadIdentity();
				glTranslatef(65, 0, 0);
				monster();
			}
		}
		glPopMatrix();

		glPushMatrix();
		if (select == 1 || select == 2 || select == 3)//translate bomb
		{
			glTranslatef(j, k, 0);
			bomb();
		}
		glPopMatrix();
		if ((cselect == select) || (cselect == 5 && select == 1) || (cselect == 4 && select == 3))//If the bomb direction and the monster direction is same it will result in a hit.
		{
			if (l==1)
				shoot();
			else

				shoot1();

		}
		else//If the bomb direction and the monster direction is diff it will be blocked.
		{
			if (l==1)//without penalty
				blocked();
			else
				blocked1();//with penalty
		}


	}
	if (flag == 5)
	{
		
		supercount++;
		if (supercount == 1)//Player 1 has played.Flags and count are reset so that second player can play.
		{
			flag = 1;
			count = 0;
			display();
		}



		if (supercount == 2)//Both the players have finished playing.
		{
			float x, y;
			glClearColor(0.0, 0.8, 0.1, 8);
			glClear(GL_COLOR_BUFFER_BIT);
			if (l == 1)
			{
				glutCreateMenu(Topmenu);
				glutAddMenuEntry("PLAY AGAIN", 1);
				glutAddMenuEntry("LEVEL 2", 3);
				glutAddMenuEntry("EXIT", 2);
				glutAttachMenu(GLUT_RIGHT_BUTTON);
			}
			if (l == 2)
			{
				glutCreateMenu(Topmenu1);
				glutAddMenuEntry("PLAY AGAIN", 1);
				glutAddMenuEntry("EXIT", 2);
				glutAttachMenu(GLUT_RIGHT_BUTTON);
				
				glFlush();
			}
			
			boundary();
			glColor3f(1, 0.25, 0.0);
			glBegin(GL_TRIANGLE_FAN);//res outer circle
			for (float i = 0; i <= 390; i++)
			{

				x = cos(i * 2 * 3.142 / 20) * 80;
				y = sin(i * 2 * 3.142 / 20) * 80;
				glVertex2f(x + 250, y + 250);

			}
			glEnd();
			glColor3f(1, 1, 0.0);
			glBegin(GL_TRIANGLE_FAN);//res inner circle
			for (float i = 0; i <= 390; i++)
			{

				x = cos(i * 2 * 3.142 / 20) * 75;
				y = sin(i * 2 * 3.142 / 20) * 75;
				glVertex2f(x + 250, y + 250);

			}

			glEnd();
			//for dashed line
			glPushAttrib(GL_ENABLE_BIT);

			glColor3f(0, 0, 1);
			glLineStipple(1, 0xFF00);
			glLineWidth(4);
			glEnable(GL_LINE_STIPPLE);
			glBegin(GL_LINES);
			glVertex2f(200, 280);
			glVertex2f(300, 280);
			glEnd();
			glPopAttrib();
			glColor3f(0.4, 0, 0);

			if (goalscored1>goalscored2)//If player 1 has scored more goals than player 2.
			{

				glColor3f(0, 0, 1);
				if (l == 2)
				{
					print("CONGRATULATIONS!", 210, 285);
				}
				else
				{
					print("LEVEL 1 COMPLETED!", 210, 285);
				}

				glColor3f(0, 0, 1);
				if (l == 2)
				{
					print("Player 1 is the winner.", 210, 250);
				}
				else
				{
					print("Player 1 is ahead!!", 210, 250);
				}
				print("Player 1  scored:\t", 210, 230);
				g1 = floor(goalscored1 / 120);
				if (g1 == 11)
					g1 = 10;
				_itoa_s(g1, p1, 10);// To convert integer value to char value.
				glColor3f(0, 0, 1);
				print(p1, 280, 230);
				print("Player 2 Scored:\t", 210, 210);
				g2 = floor(goalscored2 / 120);
				if (g2 == 11)
					g2 = 10;
				_itoa_s(g2, p2, 10);
				glColor3f(0, 0, 1);
				print(p2, 280, 210);

			
			}

			else if (goalscored1<goalscored2)//If player 2 has scored more goals than player 1.
			{

				glColor3f(0, 0, 1);
				if (l == 2)
				{
					print("CONGRATULATIONS!", 210, 285);
				}
				else
				{
					print("LEVEL 1 COMPLETED!", 210, 285);
				}

				glColor3f(0, 0, 1);
				if (l == 2)
				{
					print("Player 2 is the winner.", 210, 250);
				}
				else
				{
					print("Player 2 is ahead!!", 210, 250);
				}
				
				print("Player 2 scored:\t", 210, 230);
				g2 = floor(goalscored2 / 120);
				if (g1 == 11)
					g1 = 10;
				_itoa_s(g2, p2, 10);
				glColor3f(0, 0, 1);//To convert integer value to char value.
				print(p2, 280, 230);
				print("Player 1 scored:\t", 210, 210);
				g1 = floor(goalscored1 / 120);
				if (g2 == 11)
					g2 = 10;
				glColor3f(0, 0, 1);
				_itoa_s(g1, p1, 10);
				print(p1, 280, 210);
			}
			else
			{
				glColor3f(0, 0, 1);
				if (l == 2)
				{
					print("DRAW !!!!", 210, 285);
				}
				else
				{
					print("LEVEL 1 COMPLETED!", 210, 285);
				}

				glColor3f(0, 0, 1);

				print("Both Scored Equal points", 210, 250);
				glColor3f(0, 0, 1);
				print("Player 1 scored:\t", 210, 210);
				g1 = floor(goalscored1 / 120);
				if (g2 == 11)
					g2 = 10;
				glColor3f(0, 0, 1);
				_itoa_s(g1, p1, 10);
				print(p1, 280, 210);
				print("Player 2 scored:\t", 210, 230);
				g2 = floor(goalscored2 / 120);
				if (g1 == 11)
					g1 = 10;
				_itoa_s(g2, p2, 10);//To convert integer value to char value.
				print(p2, 280, 230);

			}
			glPushMatrix();
			glLoadIdentity();
			glTranslatef(-125, -50, 0);
			monster();
			glPopMatrix();
			glFlush();

			glPushMatrix();
			glLoadIdentity();
			glTranslatef(125, -50, 0);
			monster();
			glPopMatrix();
			glFlush();

			for (int i = 0; i<40000000; i++);//delay

		}

	}
	glFlush();

}
void key(unsigned char key, int x, int y)
{
	if (flag == 0)
	{
		if (key == char(13))
		{
			flag = 1;
		}
		display();
	}
	if (flag == 1 && supercount == 0)
	{
		if (key == 'S' || key == 's')
		{
			flag = 2;
			display();
		}
		if (key == 'E' || key == 'e')
		{
			exit(0);
		}
	}
	if (flag == 1 && supercount == 1)
	{
		if (key == 'S' || key == 's')
		{
			flag = 2;
			display();
		}
	}
}
void special(int key, int x, int y)
{
	if (count < 6 && (flag == 2 || flag==3 ))
	{
		switch (key)
		{
		case GLUT_KEY_LEFT:select = 1;
							flag = 3;
							count++;
							break;
		case GLUT_KEY_RIGHT: select = 3;
							flag = 3;
							count++;
							break;
		case GLUT_KEY_UP:select=2;
							flag = 3;
							count++;
							break;
		}
	}
	else if(count>=6)
	{

		flag = 5;//After 5 shots have been taken.
		display();
	}
}
int main(int argc, char *argv[])
{
	glutInit(&argc, argv);
	glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
	glutInitWindowSize(1900, 1800);//Window size for full screen.
	glutCreateWindow("Monster Shoot");
	srand(time(NULL));
	myinit();
	glutDisplayFunc(display);
	glutKeyboardFunc(key);
	glutSpecialFunc(special);
	glutIdleFunc(idle);
	glutMainLoop();
	return 0;
}
