#include<stdlib.h>
#include<conio.h>
#include<iostream.h>
#include<dos.h>
#include<fstream.h>
#include<string.h>
#include<stdio.h>
struct ref{
  int count,pos,slipno;
}r1;
int mainWindow();
char* getName();
int mainWindow()
   {
    clrscr();
    cout<<"\t\t\t===================\n\t\t\tPHARMACY MANAGEMENT\n\t\t\t===================\n\n\n1.Make a reciept\n2.View Reciept\n3.Search Reciepts\n4.Delete Reciept\n5.Add/Edit a Medicine\n6.Search a Medicine\n7.Delete a Medicine\n8.Add Stock\n9.View Sales\n10.Refund medicine\n11.Exit\n\nSelect the operation: ";
    int choice,a;
    cin>>choice;
    return choice;
  }
class patient
{
 private:
    char name[25];
    int age;
 public:
   setPat()
   {
    clrscr();
    cout<<"\t\t\t==================\n\t\t\tMAKING NEW RECIEPT\n\t\t\t==================\n\n\n";
    cout<<"Enter Name and age of the patient\n";
    cin.ignore();
    cin.getline(name,24);
    cin>>age;
    ofstream fout;
    fout.open("PatientRec.dat",ios::app | ios::binary);
    fout.write((char*)this,sizeof(*this));
    fout.close();
   }
   getPat()
   {
    ref *rp=&r1;
    fstream fin;
    fin.open("Counter.txt",ios::in | ios::binary);
    fin.seekg(-6,ios::end);
    fin.read((char*)rp,sizeof(*rp));
    fin.close();
    clrscr();
    fin.open("PatientRec.dat",ios::in | ios::binary);
    fin.seekg(r1.pos);
    fin.read((char*)this,sizeof(*this));
    cout<<"\nName: "<<name<<" Age: "<<age<<"\t\t\t\tSlip No: "<<r1.slipno;
    fin.close();
   }
    getPati()
   {
    clrscr();
    ifstream fin;
    fin.open("PatientRec.dat",ios::in | ios::binary);
    fin.seekg(r1.pos);
    fin.read((char*)this,sizeof(*this));
    cout<<"\nName: "<<name<<" Age: "<<age<<"\t\t\t\tSlip No: "<<r1.slipno;
    fin.close();
   }
  char* getName()
   {
    char *p=name;
    return p;
   }
};
class medicine
{
 private:
    char nam[29];
    int price,quantity;
 public:
   setMed()
    {
     int flag=0,f=0,f1=0,temp,faltu=1,tq;
     ifstream fin,fin1;
     ref *rp=&r1;
     fin.open("Counter.txt",ios::in | ios::binary);
     fin.seekg(-6,ios::end);
     fin.read((char*)rp,sizeof(*rp));
     fin.close();
     temp=r1.slipno;
     r1.count =0;
     ofstream fout,fout1;
     char n[29],a='y',b;
     fout.open("PatientRec.dat",ios::app|ios::binary);
     fout1.open("temp.dat",ios::out | ios::binary);
     while(a=='y')       // Big while loop for record
     {
       flag=0;
       f1=0;
       f=0;
       b='y';
       clrscr();
       cout<<"\t\t\t==================\n\t\t\tMAKING NEW RECIEPT\n\t\t\t==================\n\n\n";
       cout<<"Enter medicine name ";
       if(faltu==1)
	  cin.ignore();
       cin.getline(n,29);
       int len=strlen(n);
       fin.open("MedicineRecord.dat",ios::in | ios::binary);
       fin.read((char*)this,sizeof(*this));
       cout<<endl;
       faltu=1;
       while(!fin.eof())        //while loop to search for exact matches
       {
	 if(strcmpi(n,nam) == 0)
	  {
		tq=quantity;
		cout<<"\nEnter Quantity: ";
		cin>>quantity;
		if(quantity>tq)
		 {
		  cout<<"\nEntered quantity isn't availible, press Y if you still want to continue\n";
		  b=getch();
		 }
		if(b=='y')
		{
		fout1.write((char*)this,sizeof(*this));
		price = price*quantity;
		fout.write((char*)this,sizeof(*this));
		r1.count++; }
		flag=1;
		break;

	  }
	 fin.read((char*)this,sizeof(*this));
       }
      fin.close();
      if(flag == 0)
       {
	fin.open("MedicineRecord.dat",ios::in | ios::binary);
	strlwr(n);
	n[0] = n[0] - 32;
	char *p=strchr(n,' ');
	p++;
	if(*p >=97 && *p<=123)
	*p = *p -32;
	p=strrchr(n,' ');
	p++;
	if(*p >=97 && *p<=123)
	*p = *p -32;
	fin.read((char*)this,sizeof(*this));
	cout<<"\nRelated Results: ";
	while(!fin.eof())        //while loop to print possible matches
	{
	 if(strncmp(nam,n,len) == 0)
	 {
	      cout<<"\n\tMedicine: "<<nam<<"\tPrice: "<<price;
	      f=1;
	 }
	 fin.read((char*)this,sizeof(*this));
	}
	fin.close();
	if(f ==1)
	{
	 cout<<"\n\nNow enter your choice: ";
	 cin.getline(n,29);
	 fin.open("MedicineRecord.dat",ios::in | ios::binary);
	 fin.read((char*)this,sizeof(*this));
	 cout<<endl;
	 while(!fin.eof())            //While loop for the re-entered spelling
	  {
	   if(strcmpi(n,nam) == 0)
	    {
		tq=quantity;
		cout<<"\nEnter Quantity: ";
		cin>>quantity;
		if(quantity>tq)
		 {
		  cout<<"\nEntered quantity isn't availible, press Y if you still want to continue\n";
		  b=getch();
		 }
		if(b=='y')
		{
		fout1.write((char*)this,sizeof(*this));
		price = price*quantity;
		fout.write((char*)this,sizeof(*this));
		r1.count++; }
	       f1=1;
	       flag=1;
	       break;
	    }
	  else
	    fin.read((char*)this,sizeof(*this));
	  }
	 fin.close();
	  }
       else
	{  cout<<"\nSorry! no result found";
	   getch();  }
}
    if(f1==0 && flag ==0)
    {  cout<<"\nItem does not exists, press any key to try again";
       faltu=0;
    //   cout<<"\nNam at the end of abnormal "<<n;
       getch();
       a='y';    }
    else
     {  cout<<"Press y if you want to add more ";
     //	cout<<"Nam at the end of normal "<<n;
	a=getch();  }
}				 //Big while loop end
  r1.slipno=++temp;
  r1.pos=fout.tellp()-27-(r1.count*33);
  fout1.close();
  fout.close();
  fout.open("Counter.txt",ios::app | ios::binary);
  fout.write((char*)rp,sizeof(*rp));
  fout.close();


  fin.open("MedicineRecord.dat",ios::in | ios::binary);
  fout.open("MedicineRecord.dat",ios::ate | ios::binary);
  fin1.open("temp.dat",ios::in | ios::binary);
  fin1.read((char*)this,sizeof(*this));
  while(!fin1.eof())
  {
   strcpy(n,nam);
   f1=quantity;
   fin.seekg(0);
   fin.read((char*)this,sizeof(*this));
   cout<<endl;
   while(!fin.eof())
   {
    if(!strcmp(n,nam))
    {
     quantity=quantity-f1;
     fout.seekp(fin.tellg()-33);
     fout.write((char*)this,sizeof(*this));
     break;
    }
    fin.read((char*)this,sizeof(*this));
   }       //end of inner while
    fin1.read((char*)this,sizeof(*this));
  }  //end of big while
  fin1.close();
  fin.close();
  fout.close();

  fout.open("Sales.dat",ios::ate | ios::binary);
  fin.open("temp.dat",ios::binary);
  fin1.open("Sales.dat",ios::binary);
  fin.read((char*)this,sizeof(*this));
  while(!fin.eof())
  {
   strcpy(n,nam);
   f1=quantity;
   fin1.seekg(0);
   fin1.read((char*)this,sizeof(*this));
   while(!fin1.eof())
   {
    if(!strcmp(n,nam))
    {
     quantity=quantity+f1;
     fout.seekp(fin1.tellg()-33);
     fout.write((char*)this,sizeof(*this));
     break;
    }
    fin1.read((char*)this,sizeof(*this));
   }       //end of inner while
    fin.read((char*)this,sizeof(*this));
  }  //end of big while
  fin1.close();
  fin.close();
  fout.close();
  remove("temp.dat");
}                     //Function end
    getMed()
    {
    long unsigned int tot=0;
    int a=0;
    ref *rp=&r1;
    ifstream fin;
    fin.open("Counter.txt",ios::in | ios::binary);
    fin.seekg(-6,ios::end);
    fin.read((char*)rp,sizeof(*rp));
    fin.close();
    fin.open("PatientRec.dat",ios::in | ios::binary);
    fin.seekg(r1.pos+27);
    fin.read((char*)this,sizeof(*this));
    cout<<endl;
   while(a < r1.count)
   {
    cout<<"\nMedicine: "<<nam<<"\tPrice: "<<price<<"\tQuantity: "<<quantity;		 \
    tot=tot+price;
    a++;
    fin.read((char*)this,sizeof(*this));
   }
    fin.close();
    cout<<"\n\nTotal amount: "<<tot;
    }
    getMedi()
    {
    int a=0;
    long unsigned int tot=0;
    ifstream fin;
    fin.open("PatientRec.dat",ios::in | ios::binary);
    fin.seekg(r1.pos+27);
    fin.read((char*)this,sizeof(*this));
    cout<<endl;
   while(a < r1.count)
   {
    cout<<"\nMedicine: "<<nam<<"\tPrice: "<<price<<"\tQuantity: "<<quantity;		 \
    a++;
    tot=tot+price;
    fin.read((char*)this,sizeof(*this));
   }
    fin.close();
    cout<<"\n\nTotal Bill: "<<tot;

    }
  makeMed()
  {
   clrscr();
   cout<<"\t\t\t===================\n\t\t\tADDING NEW MEDICINE\n\t\t\t===================\n\n\n";
   ofstream fout,fout1;
   fout.open("MedicineRecord.dat",ios::app | ios::binary);
   fout1.open("Sales.dat",ios::app | ios::binary);
   cout<<"Enter name, price and qunatity of the medicine ";
   cin.ignore();
   cin.getline(nam,29);
   int len=strlen(nam);
   if(len <=2)
    {
     cout<<"\n	Invalid Name, press any key to add again" ;
     getch();
     makeMed();
    }
  else
  { cin>>price;
    cin>>quantity;
    fout.write((char*)this,sizeof(*this));
    quantity=0;
    fout1.write((char*)this,sizeof(*this));
    fout.close();
    fout1.close();
    cout<<"\n\n\t\t\tRECORD IS SUCCESSFULLY ADDED";
  }    }
   char* getNam()
   {
    char *p=nam;
    return p;
   }
   void searchMed()
   {
    clrscr();
    cout<<"\t\t\t==============\n\t\t\tSEARCH MEDICINE\n\t\t\t==============\n\n\n";
    int flag=0;
    char na[29];
    cout<<"Enter the name of medicine ";
    cin.ignore();
    cin.getline(na,28);
    ifstream fin;
    fin.open("MedicineRecord.dat",ios::in | ios::binary);
    fin.read((char*)this,sizeof(*this)) ;
    while(!fin.eof())
    {
     if(!strcmpi(na,getNam()))
     {
      cout<<"\nName: "<<nam<<"\tPrice: "<<price<<"\tStock: "<<quantity;
      flag=1;
     }
       fin.read((char*)this,sizeof(*this)) ;
    }
    if(flag == 0)
      cout<<"Record not found";
   }
  void delMed()
  {
   clrscr();
   cout<<"\t\t\t======================\n\t\t\tDELETE MEDICINE RECORD\n\t\t\t======================\n\n\n";
   char n[29];
   int flag=0;
   cout<<"Enter name of medicine ";
   cin.ignore();
   cin.getline(n,28);
   ifstream fin;
   ofstream fout;
   fin.open("MedicineRecord.dat",ios::in | ios::binary);
   fin.read((char*)this,sizeof(*this));
   fout.open("temp.dat",ios::out | ios::binary);
   while(!fin.eof())
   {
     if(strcmpi(n,nam))
	fout.write((char*)this,sizeof(*this));
      else
       flag=1;
     fin.read((char*)this,sizeof(*this));
   }
   fout.close();
  fin.close();
  remove("MedicineRecord.dat");
  rename("temp.dat","MedicineRecord.dat");
  if(flag==0)
    cout<<"\n\n\t\tRECORD NOT FOUND";
  else
   cout<<"\n\n\t\tRECORD IS SUCCESSFULLY DELETED";
  getch();
 }
 addStock()
 {
  char n[29],a='y';
  int b,flag;
  while(a=='y')
 {
  clrscr();
  cout<<"\t\t\t\t=========\n\t\t\t\tADD STOCK\n\t\t\t\t=========\n\n\n";
  flag=0;
  cout<<"Enter name of medicine: ";
  cin.ignore();
  cin.getline(n,28);
  ifstream fin;
  ofstream fout;
  fin.open("MedicineRecord.dat",ios::in | ios::binary);
  fout.open("MedicineRecord.dat",ios::ate | ios::binary);
  fin.read((char*)this,sizeof(*this));
  while(!fin.eof())
  {
   if(!strcmpi(n,nam))
   {
    flag=1;
    cout<<"Enter new stock: ";
    cin>>b;
    cout<<"Enter new price: ";
    cin>>price;
    quantity=quantity+b;
    fout.seekp(fin.tellg()-33);
    fout.write((char*)this,sizeof(*this));
   }
    fin.read((char*)this,sizeof(*this));
  }
  if(flag ==0)
     cout<<"\nItem doesn't exists, Please enter medicine details first\nPress y to continue, press any other key to go back to main menu";
  else
     cout<<"\n\nPress y to continue";
   a=getch();
  fout.close();
  fin.close();

  }
 }
 void viewSales()
   {
    clrscr();
    cout<<"\t\t\t\t==========\n\t\t\t\tVIEW SALES\n\t\t\t\t==========\n\n\n";
    cout<<"Select the view style:\n\n1.View only searched item\n2.View All\n\nEnter your choice: ";
    int a;
    cin>>a;
    ifstream fin;
    clrscr();
    fin.open("Sales.dat",ios::in | ios::binary);
    if(a==1)
  {
    int flag=0;
    char na[29];
    cout<<"Enter the name of medicine ";
    cin.ignore();
    cin.getline(na,28);
    fin.read((char*)this,sizeof(*this)) ;
    while(!fin.eof())
    {
     if(!strcmpi(na,getNam()))
     {
      cout<<"\nName: "<<nam<<"\tPrice: "<<price<<"\tSold: "<<quantity;
      flag=1;
     }
       fin.read((char*)this,sizeof(*this)) ;
    }
    if(flag == 0)
      cout<<"Record not found";
   }
  else if(a==2)
  {
    fin.read((char*)this,sizeof(*this)) ;
    while(!fin.eof())
    {
     cout<<"\nName: "<<nam<<"\tPrice: "<<price<<"\tSold: "<<quantity;
     fin.read((char*)this,sizeof(*this)) ;
    }
 }
 getch();
}

  void refMed()
  {
   clrscr();
   cout<<"\t\t\t===============\n\t\t\tREFUND MEDICINE\n\t\t\t===============\n\n\n";
   ifstream fin;
   ofstream fout;
   fin.open("Medicine.dat",ios::binary | ios::in);
   fout.open("Medicine.dat",ios::ate | ios::binary);
   char n[29];
   int q,flag=0;
   cout<<"Enter medicine name: ";
   cin.ignore();
   cin.getline(n,28);
   fin.read((char*)this,sizeof(*this));
   while(!fin.eof())
   {
    if(!strcmpi(n,nam))
    {
     cout<<"Enter quantity: ";
     cin>>q;
     quantity = quantity + q;
     fout.seekp(fin.tellg()-33);
     fout.write((char*)this,sizeof(*this));
     flag=1;
     break;
    }
      fin.read((char*)this,sizeof(*this));
   }
     fin.close();
     fout.close();
     flag=0;
     fin.open("Sales.dat",ios::binary | ios::in);
     fout.open("Sales.dat",ios::ate | ios::binary);
     fin.read((char*)this,sizeof(*this));
     while(!fin.eof())
    {
     if(!strcmpi(n,nam))
    {
     quantity = quantity - q;
     fout.seekp(fin.tellg()-33);
     fout.write((char*)this,sizeof(*this));
     flag=1;
     break;
    }
      fin.read((char*)this,sizeof(*this));
   }
   if(flag ==0)
     cout<<"Record not found";
  else
     cout<<"\n\n\t\t\tRecord Has Been Edited";
      getch();
    fin.close();
     fout.close();
 }

 void rr()
 {
  int a;
  ofstream fout;
  ifstream fin;
  fin.open("MedicineRecord.dat",ios::binary | ios::in);
  fout.open("Sales.dat",ios::binary | ios::out);
  fin.read((char*)this,sizeof(*this));
  while(!fin.eof())
  {
   quantity=0;
   fout.write((char*)this,sizeof(*this));
   fin.read((char*)this,sizeof(*this));
  }
  fout.close();
  fin.close();
 }
};
class reciept: public patient,public medicine
{
 public:
   void makeReciept()
   {
    setPat();
    setMed();
    getPat();
    getMed();
   }
   void viewReciept()
   {
    int flag=0,s;
    clrscr();
    ref *rp=&r1;
    cout<<"\t\t\t\t============\n\t\t\t\tVIEW RECIEPT\n\t\t\t\t============\n\n\n";
    cout<<"Enter Slip no ";
    cin>>s;
    ifstream fin1,fin2;
    fin1.open("Counter.txt",ios::in | ios::binary);
    fin2.open("PatientRec.dat",ios::in | ios::binary);
    fin1.read((char*)rp,sizeof(*rp));
    fin2.read((char*)this,sizeof(*this));
    while(!fin1.eof())
    {
     if(s==r1.slipno)
     {
      getPati();
      getMedi();
      flag=1;
     }
     fin1.read((char*)rp,sizeof(*rp));
     fin2.seekg(r1.pos);
     fin2.read((char*)this,sizeof(*this));
    }
    if(flag == 0)
	cout<<"\nRecord not found";
   }
   void search()
   {
     ref *rp=&r1;
     int choice,flag=0;
     clrscr();
     cout<<"\t\t\t\t==============\n\t\t\t\tSEARCH RECIEPT\n\t\t\t\t==============\n\n\n";
     cout<<"Select the way to search\n\n1.Search by Name\n2.Search in the given range\n3.Back\n\nEnter your chocie: ";
     cin>>choice;
     if(choice == 1)
     {
      searchReciept();
      getch();
     }
     else if(choice == 2)
     {
      int ub,lb;
      cout<<"\nEnter the starting slip no ";
      cin>>lb;
      cout<<"Enter the ending slip no ";
      cin>>ub;
      clrscr();
      ifstream fin1,fin2;
      fin1.open("Counter.txt",ios::in | ios::binary);
      fin2.open("PatientRec.dat",ios::in | ios::binary);
      fin1.read((char*)rp,sizeof(*rp));
      fin2.read((char*)this,sizeof(*this));
      cout<<"Showing reciepts from "<<lb<<" to "<<ub;
      cout<<endl;
      while(!fin1.eof())
      {
       if(r1.slipno >=lb && r1.slipno <=ub)
      {
       cout<<"\nSlip no: "<<r1.slipno<<"\tName: "<<getName();
       flag=1;
      }
      fin1.read((char*)rp,sizeof(*rp));
      fin2.seekg(r1.pos);
      fin2.read((char*)this,sizeof(*this));
    }
    if(flag == 0)
	cout<<"\nRecord not found";
    getch();
   }


     else if(choice == 3)
     {
     }


   }
     void searchReciept()
   {
    int flag=0,len;
    clrscr();
    ref *rp=&r1;
    char n[25],*p;
    cout<<"Enter a name ";
    cin.ignore();
    cin.getline(n,24);
    len=strlen(n);
    ifstream fin1,fin2;
    fin1.open("Counter.txt",ios::in | ios::binary);
    fin2.open("PatientRec.dat",ios::in | ios::binary);
    fin1.read((char*)rp,sizeof(*rp));
    fin2.read((char*)this,sizeof(*this));
    while(!fin1.eof())
    {
     char *p=getName();
     if(strcmpi(p,n) == 0)
     {
      cout<<"\nSlip no: "<<r1.slipno<<"\tName: "<<getName();
      flag=1;
     }
     fin1.read((char*)rp,sizeof(*rp));
     fin2.seekg(r1.pos);
     fin2.read((char*)this,sizeof(*this));
    }
    if(flag == 0)
      cout<<"\nRecord not found";
   }
  void delReciept()

  {
   clrscr();
   medicine m,*p;
   p=&m;
   ref *r=&r1;
   int s,a=0,flag=0,position;
   cout<<"\t\t\t\t==============\n\t\t\t\tDELETE RECIEPT\n\t\t\t\t==============\n\n\n";
   cout<<"Enter the slip no ";
   cin>>s;
   ifstream fin,fin1;
   ofstream fout,fout1;
   fin.open("Counter.txt",ios::in | ios::binary);
   fin1.open("PatientRec.dat",ios::in | ios::binary);
   fout.open("temp.txt",ios::out | ios::binary);
   fout1.open("temp1.dat",ios::out | ios::binary);
   fin.read((char*)r,sizeof(*r));
   fin1.read((char*)this,sizeof(*this));
   while(!fin.eof())
  {
    if(s==r1.slipno)
     {

	flag=1;
	position=27+(33*r1.count);
     //	cout<<"\nDelete ";
     }
     else if(s!=r1.slipno && flag == 1)
     {
	fout1.write((char*)this,sizeof(*this));
	a=0;
	while(a<(r1.count-1))
	{
	 fin1.read((char*)p,sizeof(*p));
	 fout1.write((char*)p,sizeof(*p));
	 a++;
	}
       //	cout<<"\nDeleted ";
	r1.pos=r1.pos-position;
	fout.write((char*)r,sizeof(*r));
     }

    else if(s!=r1.slipno && flag == 0)
     {
       fout.write((char*)r,sizeof(*r));
       fout1.write((char*)this,sizeof(*this));
       a=0;
       while(a<r1.count-1)
       {
	 fin1.read((char*)p,sizeof(*p));
	 fout1.write((char*)p,sizeof(*p));
	 a++;
       }
   //  cout<<"\nNot yet ";

    }                 	       //end of conditions
   fin.read((char*)r,sizeof(*r));
   fin1.seekg(r1.pos);
   fin1.read((char*)this,sizeof(*this));
  }                                 //end of big loop
  fout.close();
  fin.close();
  fin1.close();
  fout1.close();
  remove("PatientRec.dat");
  remove("Counter.txt");
  rename("temp1.dat","PatientRec.dat");
  rename("temp.txt","Counter.txt");
  if(flag ==1)
    cout<<"\n\n\t\tRECORD IS SUCCESSFULLY DELETED";
  else
    cout<<"\n\n\t\tRECORD NOT FOUND";
  getch();
  }
};
main()
{
 clrscr();
 reciept r;
 int choice=mainWindow();
 if(choice == 1)
  {
   r.makeReciept();
   getch();
   main();
  }
 else if(choice == 2)
  {
   r.viewReciept();
   getch();
   main();
  }
  else if(choice == 3)
{
 r.search();
 main();
}
 else if(choice == 4)
 {
  r.delReciept();
  main();
 }
 else if(choice == 5)
  {
   r.makeMed();
   main();
  }
 else if(choice == 6)
 {
  r.searchMed();
  getch();
  main();
 }
 else if(choice == 7)
 {
  r.delMed();
  main();
 }
 else if(choice == 8)
 {
  r.addStock();
  main();
 }
  else if(choice==9)
  {
 //  r.rr();
     r.viewSales();
   main();
  }
  else if(choice ==10)
  {
   r.refMed();
   main();
  }
  else if(choice == 11)
    exit(0);
  else
    main();
 getch();
}
