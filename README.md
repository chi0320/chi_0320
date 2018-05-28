# chi_0320#include<iostream>
#include<fstream>
#include<string.h>
using namespace std; 

class dnode{
	public:
		char id_char[20];
		char date[20];
		char info[100];
		char mixture[200];
		int id;
};
class diary
{
public:
	dnode new_node; 
	
fstream file;
char info[100];
char date[20];
char name[20];
char diary_info[200];


void write_diary()
{
	memset(new_node.mixture,'\0',sizeof(new_node.mixture));
	cout << "\n�п�J�n�s���ɮצW��:\n";
	cin >> name;
	
	cout << "\n�п�J�n�g��������� yyyy-mm-nn :\n";
	cin >> new_node.date;

	cout << "\n�п�J�n�g�J��O�����e:\n";
	cin >> new_node.info;
	
	new_node.id=0;
	sprintf(new_node.id_char,"%d", new_node.id);
	
	strcat(new_node.mixture, new_node.id_char);
	strcat(new_node.mixture, "�A");
	strcat(new_node.mixture, new_node.date);
	strcat(new_node.mixture, "�A");
	strcat(new_node.mixture, new_node.info);
	strcat(new_node.mixture, "\n");
}

void write_to_diary()
{
	fstream file;
	size_t num= strlen(new_node.mixture);
	
	file.open(name, ios::app);
	file.write(new_node.mixture,num);
	cout << "�����w����~" <<endl;
	file.close();

}

int Read()
{
	fstream file;
	
	cout << "\n�п�J�nŪ���ɮצW��:\n";
	cin >> name;
	file.open(name, ios::in);
	file.read(new_node.mixture,sizeof(new_node.mixture));
	
	cout <<"��O���e : \n";
	cout <<new_node.mixture<<endl;

	file.close();
}

int askagain()
{
	cout << "�O�_�n�g�t�@�g��O? <�n:Y/���n:N>" ;
	char conti;
	cin >> conti;
	if (conti== 'Y' or conti=='y'){
		cout <<"�{���~��\n";
		return 1;
	} 
	else if(conti=='N' or conti=='n'){
		cout <<"�{������\n";
		return 0;
	}
	else{
		cout <<"���~���O�A�ЦA��J�@��\n";
	}
}

int menu()
{
	cout<<"�п�ܱz�n���檺�ʧ@:\n";
		cout<<"(1)�g��O (2)Ū��O (3)�[��/�ק���|�W�� (4)���}\n ";
}
};


int main()
{
	diary test;
	int a;
	for(;;)
	{
		test.menu();
		cin>>a;
		if(a==1)
		{
			do{
				test.write_diary();
				test.write_to_diary();
			}while(test.askagain());
		}
		else if(a==2)
		{
			test.Read();	
		}
		else if(a==3)
		{
			if(test.name[0]=='\0')
			{
				char chose;
	              cout<<"(A) �s�W�ɮצW�� (B) �^�W�@�h \n";
	              cin>> chose;
	              if(chose=='A' or chose=='a')
	              {
	              	do{
				          test.write_diary();
				          test.write_to_diary();
		     	    }while(test.askagain());
				  }
				  else 
				      continue;
		    }
		    else
			{
				char chose;
				cout <<"�ثe��O�ɮצW�٬��G" << test.name <<endl;
	              cout<<"(A) �ק��ɮצW�� (B) �^�W�@�h\n";
	              cin>> chose;
	              if(chose=='A' or chose=='a')
	              {
	              	do{
				          test.write_diary();
				          test.write_to_diary();
		     	    }while(test.askagain());
				  }
				  else 
				      continue;
			 } 
		}
		else
		    break;
	}
	 
	 return 0;
}
