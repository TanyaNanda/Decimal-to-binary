Decimal-to-binary
=================
// testcomplement.cpp : Defines the entry point for the console application.
//

#include "stdafx.h"
#include <iostream>
#include <math.h>
using namespace std;

const int maxLength=16; // represent the bit 


void decimal2binary(int dec, int *binaryNumber)

{
	int quotient=dec;

	for(int k=0;k<maxLength;k++)
	{
		binaryNumber[k]=0;
	}
 


for(int i=0;i<maxLength && quotient!=0; i++)
   {   
	   binaryNumber[i]=quotient%2;

      quotient/=2;

   }  

}



void complementFilp (int *a)
{
 int l, c=0;
 char b[16];
 

for(int i=0; i<maxLength; i++)
{

a[i]=!a[i]; //==0?1:0;

}

}


void addone(int *a)
{
	int c=1;

for(int i=0; i<maxLength && c!=0; i++)

{
c=a[i];
	
a[i]=!a[i];

}

}

















void assertEquals (int expected, int actual) {
	if (expected != actual) {
	cout << "Expected " << expected << " but got " << actual << endl;
	}
}


void testcomplement()
{
	cout << " Test complementFlip function" << endl;

	int expected =0;
	int binarynumer[maxLength];
	
	for( int i=0; i<maxLength;i++)
	{
		binarynumer[i]=0;
	}
	complementFilp(binarynumer);

	for(int i=0;i<maxLength;i++)
	{
	assertEquals(1,binarynumer[i]);
	}

	complementFilp(binarynumer);

	for(int i=0;i<maxLength;i++)
	{
	assertEquals(0,binarynumer[i]);
	}

for( int i=0; i<maxLength;i++)
	{
		binarynumer[i]=i%2;
	}
complementFilp(binarynumer);

	for(int i=0;i<maxLength;i++)
	{
	assertEquals(!(i%2),binarynumer[i]);
	}

}

void testdecimal2binary()
{
	cout << "test decimal to binary";


	int binarynumer[maxLength];

	for(int i=0;i<maxLength;i++)
	{

		binarynumer[i]=-1;
	}
	decimal2binary(0,binarynumer);

	for(int i=0;i<maxLength;i++)
	{
	assertEquals(0,binarynumer[i]);
	
	}
	cout << "testing 5";
	decimal2binary(5,binarynumer);

	assertEquals(1,binarynumer[0]);
	assertEquals(0,binarynumer[1]);
	assertEquals(1,binarynumer[2]);

	for(int i=3;i<maxLength;i++)
	{
	assertEquals(0,binarynumer[i]);
	
	}

	decimal2binary(pow(2,maxLength-1)-1,binarynumer);

	for (int i = 0; i <maxLength-1; i++)
	{
assertEquals(1,binarynumer[i]);
	}

	assertEquals(0,binarynumer[maxLength-1]);

}


void testaddone()
{
	cout << " Test add one function"<< endl;

	int excepted =0;
	int binarynumber[maxLength];

	for( int i=0; i<maxLength;i++)
	{
		binarynumber[i]=0;
	}
	addone(binarynumber);

	assertEquals(1,binarynumber[0]);

	for(int i=1;i<maxLength;i++)
	{
	assertEquals(0,binarynumber[i]);
	}

	for( int i=0; i<maxLength;i++)
	{
		binarynumber[i]=1;
	}
	addone(binarynumber);

	for(int i=0;i<maxLength;i++)
	{
	assertEquals(0,binarynumber[i]);
	}



}


void runtest()
{
	testcomplement();
	testdecimal2binary();
	testaddone();
}

int maintest()
{
	runtest();

	
	system("PAUSE");
	return 0;
}

int main()
{
int num;
int a[maxLength];

cout << "Enter The Decimal Number (from -32768 to 32767) " << endl;
cin >> num ;
if(num<-32768 || num>32767)
{

	cout << "Enter Different Number (from -32768 to 32767) " << endl;
	cin >> num;
}

decimal2binary(abs(num),a);

if( num<0)
{
complementFilp(a);
addone(a);
}

for( int i=maxLength-1; i>=0; i--)
{
cout << a[i] ;

}
cout << endl;
system("PAUSE") ;
	
return 0;

}
