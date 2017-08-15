#include<iostream.h>
#include<stdio.h>
#include<graphics.h>
#include<process.h>
#include<string.h>
#include<fstream.h>
#include<conio.h>
void menu(int j);
int gd=DETECT,gm;
class element
{
 int period,group;
 float atmmass,mp,bp;
 char atmno[4],nm[20],cat[10],ec[50],symbol[5],oxistate[10];
 public:
 void dp(int a)
 {
  initgraph(&gd,&gm,"C:\\Turboc3\\BGI");
  int left = getmaxx() / 2 - 300;
  int top = getmaxy() / 2-220;
  int right = getmaxx() / 2 - 240;
  int bottom = getmaxy() / 2 -170;
  if(a<=2)
   {
    setfillstyle(1,RED);
    settextstyle(1,EMPTY_FILL,5);
    setcolor(WHITE);
    outtextxy(25,15,symbol);
   }
  else if(a>2 && a<=13)
   {
    setfillstyle(1,CYAN);
    settextstyle(1,EMPTY_FILL,5);
    setcolor(WHITE);
    outtextxy(25,15,symbol);
   }
   else if(a>13 && a<=18)
   {
    setfillstyle(1,BLUE);
    settextstyle(1,EMPTY_FILL,5);
    setcolor(WHITE);
    outtextxy(25,15,symbol);
   }
  rectangle(left,top,right,bottom);
  floodfill(top+2,bottom-2,WHITE);
  left-=5;
  top-=5;
  right+=5;
  bottom+=5;
  rectangle(left,top,right,bottom);
 }
 void display()
 {
  clrscr();
  dp(group);
  cout<<"\n\n\n\n\n\n";
  cout<<"\nName: "<<nm;
  cout<<"\nSymbol: "<<symbol;
  cout<<"\nGroup: "<<group;
  cout<<"\nPeriod: "<<period;
  cout<<"\nAtomic number: "<<atmno;
  cout<<"\nOxidation state: "<<oxistate;
  cout<<"\nMelting point: "<<mp<<" K";
  cout<<"\nBoiling point: "<<bp<<" K";
  cout<<"\nAtomic mass: "<<atmmass<<" amu";
  cout<<"\nConfiguration: "<<ec;
  getch();
 }
 int search(char a[20])
 {
  int i=0;
  if(strcmp(a,nm)==0 || strcmp(a,atmno)==0 || strcmp(a,symbol)==0)
  {
   display();
   i++;
  }
  return i;
 }
};
void table();
void sh()
{
 char s[20];
 element b;
 clrscr();
 ifstream a("El.dat",ios::binary);
 initgraph(&gd,&gm,"C:\\Turboc3\\BGI");
 int z,left = getmaxx() / 2 - 150;
 int top = getmaxy() / 2 - 20;
 int right = getmaxx() / 2 + 150;
 int bottom = getmaxy() / 2 +5;
 rectangle(left,top,right,bottom);
 settextstyle(0,EMPTY_FILL,2);
 outtextxy(110,140,"ENTER THE ELEMENT TO SEARCH:");
 gotoxy(35,15);
 gets(s);
 while(!a.eof())
 {
  a.read((char*)&b,sizeof(b));
  z=b.search(s);
  if(z==1)
  {
   break;
  }
 }
 a.close();
 if(z==0)
 {
  int left = getmaxx() / 2 - 95;
  int top = getmaxy() / 2+120;
  int right = getmaxx() / 2 + 85;
  int bottom = getmaxy() / 2 +160;
  setfillstyle(1,RED);
  rectangle(left,top,right,bottom);
  floodfill(top+2,bottom-2,WHITE);
  left = getmaxx() / 2 - 100;
  top = getmaxy() / 2+115;
  right = getmaxx() / 2 + 90;
  bottom = getmaxy() / 2 +165;
  rectangle(left,top,right,bottom);
  settextstyle(1,EMPTY_FILL,5);
  setcolor(WHITE);
  outtextxy(230,350,"ERROR..!!");
  getch();
 }
 getch();
}
void menu(int j)
{
 clrscr();
 initgraph(&gd,&gm,"C:\\Turboc3\\BGI");
 if(j==1)
 {
  int left = getmaxx() / 2 - 170;
  int top = getmaxy() / 2 - 170;
  int right = getmaxx() / 2 + 140;
  int bottom = getmaxy() / 2 +60;
  rectangle(left,top,right,bottom);
  left = getmaxx() / 2 - 190;
  top = getmaxy() / 2 - 190;
  right = getmaxx() / 2 + 160;
  bottom = getmaxy() / 2 +80;
  rectangle(left,top,right,bottom);
  settextstyle(1,EMPTY_FILL,6);
  setcolor(WHITE);
  outtextxy(165,100,"--MENU--");
  settextstyle(0,EMPTY_FILL,2);
  setcolor(YELLOW);
  outtextxy(150,195,">>Periodic Table");
  settextstyle(0,EMPTY_FILL,2);
  setcolor(RED);
  outtextxy(150,225,">>Search an Element");
  settextstyle(0,EMPTY_FILL,2);
  setcolor(RED);
  outtextxy(150,255,">>Exit");
  if(getch()==13)
  {
   closegraph();
   table();
   closegraph();
   menu(1);
  }
 }
 else if(j==2)
 {
  int left = getmaxx() / 2 - 170;
  int top = getmaxy() / 2 - 170;
  int right = getmaxx() / 2 + 140;
  int bottom = getmaxy() / 2 +60;
  rectangle(left,top,right,bottom);
  left = getmaxx() / 2 - 190;
  top = getmaxy() / 2 - 190;
  right = getmaxx() / 2 + 160;
  bottom = getmaxy() / 2 +80;
  rectangle(left,top,right,bottom);
  settextstyle(1,EMPTY_FILL,6);
  setcolor(WHITE);
  outtextxy(165,100,"--MENU--");
  settextstyle(0,EMPTY_FILL,2);
  setcolor(RED);
  outtextxy(150,195,">>Periodic Table");
  settextstyle(0,EMPTY_FILL,2);
  setcolor(YELLOW);
  outtextxy(150,225,">>Search an Element");
  settextstyle(0,EMPTY_FILL,2);
  setcolor(RED);
  outtextxy(150,255,">>Exit");
  if(getch()==13)
  {
   closegraph();
   sh();
   getch();
   closegraph();
   menu(2);
  }
 }
 else if(j==3)
 {
  int left = getmaxx() / 2 - 170;
  int top = getmaxy() / 2 - 170;
  int right = getmaxx() / 2 + 140;
  int bottom = getmaxy() / 2 +60;
  rectangle(left,top,right,bottom);
  left = getmaxx() / 2 - 190;
  top = getmaxy() / 2 - 190;
  right = getmaxx() / 2 + 160;
  bottom = getmaxy() / 2 +80;
  rectangle(left,top,right,bottom);
  settextstyle(1,EMPTY_FILL,6);
  setcolor(WHITE);
  outtextxy(165,100,"--MENU--");
  settextstyle(0,EMPTY_FILL,2);
  setcolor(RED);
  outtextxy(150,195,">>Periodic Table");
  settextstyle(0,EMPTY_FILL,2);
  setcolor(RED);
  outtextxy(150,225,">>Search an Element");
  settextstyle(0,EMPTY_FILL,2);
  setcolor(YELLOW);
  outtextxy(150,255,">>Exit");
  if(getch()==13)
  {
   closegraph();
   clrscr();
   initgraph(&gd,&gm,"C:\\Turboc3\\BGI");
   settextstyle(0,EMPTY_FILL,3);
   setcolor(WHITE);
   outtextxy(50,100,"THANK YOU FOR USING OUR");
   settextstyle(0,EMPTY_FILL,3);
   setcolor(WHITE);
   outtextxy(200,150,"PROGRAMME");
   settextstyle(0,EMPTY_FILL,3);
   setcolor(BLACK);
   outtextxy(230,195,"MADE BY:-");
   settextstyle(0,EMPTY_FILL,3);
   setcolor(WHITE);
   outtextxy(170,260,"Chinmay Shringi");
   getch();
   exit(0);
  }
 }
}
void main()
{
clrscr();
char w;
int j=1;
while(1)
{
closegraph();
menu(j);
w=getch();
cout<<w;
if(w=='w')
{
 if(j==1)
 {
  j=3;
  closegraph();
  menu(j);
 }
 else
 {
  j--;
  closegraph();
  menu(j);
 }
}
else if(w=='s')
{
 if(j==3)
 {
  j=1;
  closegraph();
  menu(j);
 }
 else
 {
  j++;
  closegraph();
  menu(j);
 }
}
}
getch();
}
void table()
{
initgraph(&gd,&gm,"C:\\Turboc3\\BGI");
settextstyle(1,EMPTY_FILL,5);
setcolor(WHITE);
outtextxy(120,10,"PERIODIC TABLE");
setcolor(WHITE);   //periods
line(595,100,630,100);
line(0,100,35,100);
line(0,130,70,130);
line(420,130,630,130);
line(0,160,70,160);
line(420,160,630,160);
line(0,190,630,190);
line(0,220,630,220);
line(0,250,630,250);
line(0,280,630,280);
line(0,310,630,310);
line(0,100,0,310);  //groups
line(35,100,35,310);
line(70,130,70,310);
line(105,190,105,310);
line(140,190,140,310);
line(175,190,175,310);
line(210,190,210,310);
line(245,190,245,310);
line(280,190,280,310);
line(315,190,315,310);
line(350,190,350,310);
line(385,190,385,310);
line(420,130,420,310);
line(455,130,455,310);
line(490,130,490,310);
line(525,130,525,310);
line(560,130,560,310);
line(595,100,595,310);
line(630,100,630,310);
settextstyle(0,EMPTY_FILL,1);
setcolor(RED);
outtextxy(15,90,"1");//group no
outtextxy(50,90,"2");
setcolor(CYAN);
outtextxy(85,90,"3");
outtextxy(120,90,"4");
outtextxy(155,90,"5");
outtextxy(190,90,"6");
outtextxy(225,90,"7");
outtextxy(260,90,"8");
outtextxy(295,90,"9");
outtextxy(325,90,"10");
outtextxy(360,90,"11");
outtextxy(395,90,"12");
setcolor(YELLOW);
outtextxy(430,90,"13");
outtextxy(465,90,"14");
outtextxy(500,90,"15");
outtextxy(535,90,"16");
outtextxy(605,90,"18");
outtextxy(570,90,"17");
setcolor(RED);
outtextxy(10,105,"1.");   //elements name
outtextxy(10,120,"H");
outtextxy(10,135,"3.");
outtextxy(10,150,"Li");
outtextxy(10,165,"11.");
outtextxy(10,180,"Na");
outtextxy(10,195,"19.");
outtextxy(10,210,"K");
outtextxy(10,225,"37.");
outtextxy(10,240,"Rb");
outtextxy(10,255,"55.");
outtextxy(10,270,"Cs");
outtextxy(10,285,"88.");
outtextxy(10,300,"Fr");
outtextxy(45,135,"4.");
outtextxy(45,150,"Be");
outtextxy(45,165,"12.");
outtextxy(45,180,"Mg");
outtextxy(45,195,"20.");
outtextxy(45,210,"Ca");
outtextxy(45,225,"38.");
outtextxy(45,240,"Sr");
outtextxy(45,255,"56.");
outtextxy(45,270,"Ba");
outtextxy(45,285,"88.");
outtextxy(45,300,"Ra");
setcolor(CYAN);
outtextxy(80,195,"21.");
outtextxy(80,210,"Sc");
outtextxy(80,225,"39.");
outtextxy(80,240,"Y");
outtextxy(80,255,"57-");
outtextxy(80,270,"71" );
outtextxy(80,285,"89-");
outtextxy(80,300,"103");
outtextxy(115,195,"22.");
outtextxy(115,210,"Ti");
outtextxy(115,225,"40.");
outtextxy(115,240,"Zr");
outtextxy(115,255,"72.");
outtextxy(115,270,"Hf" );
outtextxy(110,285,"104.");
outtextxy(115,300,"Rf");
outtextxy(150,195,"23.");
outtextxy(150,210,"V");
outtextxy(150,225,"41.");
outtextxy(150,240,"Nb");
outtextxy(150,255,"73.");
outtextxy(150,270,"Ta" );
outtextxy(145,285,"105.");
outtextxy(150,300,"Db");
outtextxy(185,195,"24.");
outtextxy(185,210,"Cr");
outtextxy(185,225,"42.");
outtextxy(185,240,"Mo");
outtextxy(185,255,"74.");
outtextxy(185,270,"W" );
outtextxy(180,285,"106.");
outtextxy(185,300,"Sg");
outtextxy(220,195,"25.");
outtextxy(220,210,"Mn");
outtextxy(220,225,"43.");
outtextxy(220,240,"Tc");
outtextxy(220,255,"75.");
outtextxy(220,270,"Re" );
outtextxy(215,285,"107.");
outtextxy(220,300,"Bh");
outtextxy(255,195,"26.");
outtextxy(255,210,"Fe");
outtextxy(255,225,"44.");
outtextxy(255,240,"Ru");
outtextxy(255,255,"76.");
outtextxy(255,270,"Os" );
outtextxy(250,285,"108.");
outtextxy(255,300,"Hs");
outtextxy(290,195,"27.");
outtextxy(290,210,"Co");
outtextxy(290,225,"45.");
outtextxy(290,240,"Rh");
outtextxy(290,255,"77.");
outtextxy(290,270,"Ir" );
outtextxy(285,285,"109.");
outtextxy(290,300,"Mt");
outtextxy(325,195,"28.");
outtextxy(325,210,"Ni");
outtextxy(325,225,"46.");
outtextxy(325,240,"Pd");
outtextxy(325,255,"78.");
outtextxy(325,270,"Pt" );
outtextxy(320,285,"110.");
outtextxy(325,300,"Ds");
outtextxy(360,195,"29.");
outtextxy(360,210,"Cu");
outtextxy(360,225,"47.");
outtextxy(360,240,"Ag");
outtextxy(360,255,"79.");
outtextxy(360,270,"Au" );
outtextxy(355,285,"111.");
outtextxy(360,300,"Rg");
outtextxy(395,195,"30.");
outtextxy(395,210,"Zn");
outtextxy(395,225,"48.");
outtextxy(395,240,"Cd");
outtextxy(395,255,"80.");
outtextxy(395,270,"Hg" );
outtextxy(390,285,"112.");
outtextxy(395,300,"Cn");
setcolor(YELLOW);
outtextxy(435,135,"5.");
outtextxy(435,150,"B");
outtextxy(430,165,"13.");
outtextxy(430,180,"Al");
outtextxy(430,195,"31.");
outtextxy(430,210,"Ga");
outtextxy(430,225,"49.");
outtextxy(430,240,"In");
outtextxy(430,255,"81.");
outtextxy(430,270,"Tl" );
outtextxy(425,285,"113.");
outtextxy(425,300,"Uut");
outtextxy(465,135,"6.");
outtextxy(465,150,"C");
outtextxy(465,165,"14.");
outtextxy(465,180,"Si");
outtextxy(465,195,"32.");
outtextxy(465,210,"Ge");
outtextxy(465,225,"50.");
outtextxy(465,240,"Sn");
outtextxy(465,255,"82.");
outtextxy(460,270,"Pb" );
outtextxy(460,285,"114.");
outtextxy(460,300,"Fl");
outtextxy(500,135,"7.");
outtextxy(500,150,"N");
outtextxy(500,165,"15.");
outtextxy(505,180,"P");
outtextxy(500,195,"33.");
outtextxy(500,210,"As");
outtextxy(500,225,"51.");
outtextxy(500,240,"Sb");
outtextxy(500,255,"83.");
outtextxy(500,270,"Bi" );
outtextxy(495,285,"115.");
outtextxy(495,300,"Uup");
outtextxy(535,135,"8.");
outtextxy(540,150,"O");
outtextxy(535,165,"16.");
outtextxy(540,180,"S");
outtextxy(535,195,"34.");
outtextxy(535,210,"Se");
outtextxy(535,225,"52.");
outtextxy(535,240,"Te");
outtextxy(535,255,"84.");
outtextxy(535,270,"Po" );
outtextxy(530,285,"116.");
outtextxy(535,300,"Lv");
outtextxy(570,135,"8.");
outtextxy(575,150,"F");
outtextxy(570,165,"17.");
outtextxy(570,180,"Cl");
outtextxy(570,195,"35.");
outtextxy(570,210,"Br");
outtextxy(570,225,"53.");
outtextxy(575,240,"I");
outtextxy(570,255,"85.");
outtextxy(570,270,"At" );
outtextxy(565,285,"117.");
outtextxy(565,300,"Uus");
outtextxy(605,105,"2.");
outtextxy(605,120,"He");
outtextxy(605,135,"10.");
outtextxy(605,150,"Ne");
outtextxy(605,165,"18.");
outtextxy(605,180,"Ar");
outtextxy(605,195,"36.");
outtextxy(605,210,"Kr");
outtextxy(605,225,"54.");
outtextxy(605,240,"Xe");
outtextxy(605,255,"86.");
outtextxy(605,270,"Rn" );
outtextxy(600,285,"118.");
outtextxy(600,300,"Uuo");
setcolor(WHITE);
//lanthenoids actinoids
line(105,380,630,380);
line(105,410,630,410);
line(105,440,630,440);
line(105,380,105,440);
line(140,380,140,440);
line(175,380,175,440);
line(210,380,210,440);
line(245,380,245,440);
line(280,380,280,440);
line(315,380,315,440);
line(350,380,350,440);
line(385,380,385,440);
line(420,380,420,440);
line(455,380,455,440);
line(490,380,490,440);
line(525,380,525,440);
line(560,380,560,440);
line(595,380,595,440);
line(630,380,630,440);
line(0,85,70,85);//block name
line(75,175,415,175);
line(75,175,75,178);
line(415,175,415,178);
line(70,85,70,88);
line(0,85,0,88);
line(70,85,70,88);
line(420,85,630,85);
line(420,85,420,88);
line(630,85,630,88);
line(105,365,630,365);
line(105,365,105,370);
line(630,365,630,370);
setcolor(MAGENTA);
outtextxy(115,385,"57.");//elements of lenthenoids and actenoids
outtextxy(115,400,"La.");
outtextxy(115,415,"89.");
outtextxy(115,430,"Ac");
outtextxy(150,385,"58.");
outtextxy(150,400,"Ce");
outtextxy(150,415,"90.");
outtextxy(150,430,"Th");
outtextxy(185,385,"59.");
outtextxy(185,400,"Pr");
outtextxy(185,415,"91.");
outtextxy(185,430,"Pa");
outtextxy(220,385,"60.");
outtextxy(220,400,"Nd");
outtextxy(220,415,"92.");
outtextxy(225,430,"U");
outtextxy(255,385,"61.");
outtextxy(255,400,"Pm");
outtextxy(255,415,"93.");
outtextxy(255,430,"Np");
outtextxy(290,385,"62.");
outtextxy(290,400,"Sm");
outtextxy(290,415,"94.");
outtextxy(290,430,"Pu");
outtextxy(325,385,"63.");
outtextxy(325,400,"Eu");
outtextxy(325,415,"95.");
outtextxy(325,430,"Am");
outtextxy(360,385,"64.");
outtextxy(360,400,"Gd");
outtextxy(360,415,"96.");
outtextxy(360,430,"Cm");
outtextxy(395,385,"65.");
outtextxy(395,400,"Tb");
outtextxy(395,415,"97.");
outtextxy(395,430,"Bk");
outtextxy(430,385,"66.");
outtextxy(430,400,"Dy");
outtextxy(430,415,"98.");
outtextxy(430,430,"Cf");
outtextxy(465,385,"67.");
outtextxy(465,400,"Ho");
outtextxy(465,415,"99.");
outtextxy(465,430,"Es");
outtextxy(500,385,"68.");
outtextxy(500,400,"Er");
outtextxy(495,415,"100.");
outtextxy(500,430,"Fm");
outtextxy(535,385,"69.");
outtextxy(535,400,"Tm");
outtextxy(530,415,"101.");
outtextxy(535,430,"Md");
outtextxy(570,385,"70.");
outtextxy(570,400,"Yb");
outtextxy(565,415,"102.");
outtextxy(570,430,"No");
outtextxy(605,385,"71.");
outtextxy(605,400,"Lu");
outtextxy(600,415,"103.");
outtextxy(605,430,"Lr");
settextstyle(0,EMPTY_FILL,1);
setcolor(RED);
outtextxy(8,75,"s-block");
setcolor(YELLOW);
outtextxy(500,75,"p-block");
setcolor(CYAN);
outtextxy(210,165,"d-block");
setcolor(MAGENTA);
outtextxy(330,355,"f-block");
settextstyle(0,EMPTY_FILL,1);
setcolor(GREEN);
outtextxy(0,390,"Lanthanides");
outtextxy(0,420,"Actinides");
getch();
}
