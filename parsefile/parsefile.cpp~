#include <iostream>
#include <fstream>
#include <string>
#include <sstream>
#include <cstring>
#include <iterator>
#include <vector>
#include <algorithm>

using namespace std;

//Check if file passed is a PHP file
bool isPHP(string hold[],int n)
{
	if(hold[0].compare("<?php")==0)
		return true;
	else
		return false;	
}

//Check if file passed is a Java file
bool isJava(string hold[],int n)
{
	
	vector<string> v;
	v.push_back("String");
	v.push_back("Long");
	v.push_back("Integer");
	v.push_back("Double");
	v.push_back("Class");
	
	for(int i=0;i<n-1;i++){
		
		if((find(v.begin(),v.end(),hold[i])!=v.end())){
			
			for(int j=0;j<hold[i+1].size();j++){
				
				if((hold[i+1].at(j)>='a' && hold[i+1].at(j)<='z') && (hold[i+1].at(j+1)>='A' && hold[i+1].at(j+1)<='Z')){
					return true;
							
				}
			
			}
		}
	}
	return false;
	
}

//Check if file passed is Ruby file
bool isRuby(string hold[],int n)
{
	for(int i=0;i<n;i++){
		if(hold[i].compare("def")==0 || hold[i].compare("end")==0)
			return true;
		
	}
	return false;
}

//List the classes in PHP file
void showClassPHP(string hold[],int n)
{
	for(int i=0;i<n;i++){
		if(hold[i].compare("class")==0)
			cout<<hold[i+1]<<endl;
		}
}

//List the classes in Java file
void showClassJava(string hold[],int n)
{
	for(int i=0;i<n;i++){
		if(hold[i].compare("class")==0)
			cout<<hold[i+1]<<endl;
	}
}

//List the classes in Ruby file
void showClassRuby(string hold[],int n)
{
	for(int i=0;i<n;i++){
		if(hold[i].compare("class")==0)
			cout<<hold[i+1]<<endl;
		}
}

//List the classes in PHP file
void showMethodsPHP(string hold[],int n)
{
	for(int i=0;i<n-2;i++){
		if((hold[i].compare("public")==0) || (hold[i].compare("private")==0)|| (hold[i].compare("protected")==0)){
			if(hold[i+1].compare("function")==0){
			 	 int j=i+2;
				 while((hold[j].at(hold[j].size()-1)==')')){
					 cout<<hold[j];
					 j++;
					 cout<<endl;
				}	
				
			}
		}
	}
	
	
}

//List the methods in Java file
void showMethodsJava(string hold[],int n)
{
	for(int i=0;i<n-2;i++){
		if((hold[i].compare("public")==0) || (hold[i].compare("private")==0)|| (hold[i].compare("protected")==0)){
			if((hold[i+1].compare("String")==0) || (hold[i+1].compare("Integer")==0) || (hold[i+1].compare("Double")==0) || (hold[i+1].compare("Long")==0) || (hold[i+1].compare("void")==0)){
			 cout<<hold[i+1]<<endl;
			 if(hold[i+2].find("(")!=string::npos){	
			 
				 int j=i+2;
				 do{
					 cout<<hold[j]<<endl;
					 j++;
				   }while((hold[j].find(")")!=string::npos));
				 cout<<hold[i+1]<<endl;
			}
			
			

			
			}
		}
	}
}

//List the methods in Ruby file
void showMethodsRuby(string hold[],int n)
{
	for(int i=0;i<n-1;i++){
		if(hold[i].compare("def")==0)
			cout<<hold[i+1]<<endl;
	}
}

//List the class properties of PHP file
void showPropertiesPHP(string hold[],int n)
{
    	for(int i=0;i<n;i++){
	   l1: 	for(int j=0;j<hold[i].size();j++){
			if(hold[i].at(j)=='$'){
				for(int k=j+1;k<hold[i].size();k++){
					if((hold[i].at(k)>='a' && hold[i].at(k)<='z') || (hold[i].at(k)>='A' && hold[i].at(k)<='Z')){
						cout<<hold[i].at(k);
					}
					else{
						i++;
						goto l1;
					}
					
			}		
		}
	}	
}}

//List the class properties of Java file
void showPropertiesJava(string hold[],int n)
{
	for(int i=0;i<n-2;i++){
		if((hold[i].compare("public")==0) || (hold[i].compare("private")==0)|| (hold[i].compare("protected")==0)){
			if((hold[i+1].compare("String")==0) || (hold[i+1].compare("Integer")==0) || (hold[i+1].compare("Double")==0) || (hold[i+1].compare("Long")==0)){
			 if((hold[i+2].at(hold[i+2].size()-1)==';'))
				cout<<hold[i]+" "+hold[i+1]+" "+hold[i+2]<<endl;
			
			}
		}
	}
		
}

//List the class properties of Ruby file
void showPropertiesRuby(string hold[],int n)
{
	for(int i=0;i<n;i++)
	{	
		if(hold[i].find("@@") || hold[i].find("@"))
		cout<<hold[i];
	}
}


int main ()
{
        string str,temp="";
	int count=0;
	ifstream inputfile;
	inputfile.open ("College.java");
	if(inputfile.is_open()){
		while(!inputfile.eof()) {
	        	getline(inputfile,str);
			temp=temp+str; 
        	}
	}
	cout<<temp;

	
	
	int n=temp.size();
	printf("\nSize of String %d",n);
	
	
	char temparray[n];
	for (int i=0; i<n; i++){
    		temparray[i]=temp.at(i);
  	}	
	for(int i=0;temparray[i]!='\0';i++){
    		if(temparray[i]==' '){
        			count++;
        			while(temparray[i]==' ')
        				i++;
		}
	}
	int total=count+1;
     	printf("\nTotal words are %d",total);

	
	string hold[total];
    	int i = 0;
    	stringstream ssin(temp);
    	while (ssin.good() && i < total){
        	ssin >> hold[i];
        	++i;
    	}
    	for(i = 0; i < total; i++){
        	cout << hold[i] << endl;
    	}

	

	if(isPHP(hold,total)){
		printf("%s\n","PHP File");		
		showClassPHP(hold,total);	
		showMethodsPHP(hold,total);	
		showPropertiesPHP(hold,total);
	}
	else if(isJava(hold,total)){
		printf("%s\n","Java File");		
		showClassJava(hold,total);
		showMethodsJava(hold,total);
		showPropertiesJava(hold,total);
	}
	else if(isRuby(hold,total)){
		printf("%s\n","Ruby File");		
		showClassRuby(hold,total);
		showMethodsRuby(hold,total);
		showPropertiesRuby(hold,total);
	}
	else
	cout<<"None";
	

        inputfile.close();
	return 0;
}


	








 
