#include<iostream>
#include<cstdlib>
#include<ctime>
using namespace std;
int lenght(char *);
bool isEqual(char *,char *);
void clearStr(char *);
void delSent(char *,char *);
void delWord(char *,char);
void mixWord(char *);
void capLet(char *);
int findRepeat(char *,char *);
void reverse(char *);
int main()
{
	
}

int lenght(char *str)
{
	int l=0;
	while(str[l]!='\0')
	{
		l++;
	}
	
	return l;
}

bool isEqual(char *str,char *str2)
{
	int u=lenght(str);
	
	if(u != lenght(str2))
	{
		return 0;
	}
	
	for(int i=0;i<u;i++)
	{
		if(str[i]!=str2[i])
		{
			return 0;
		}
	}
	
	return 1;
}

void delSent(char *str,char *str2)
{
	int i=0;
	char sent[100];
	while(str[i]!='\0')
	{
		int k=0;
		while(str[i]!=' ' && str[i]!='\0')
		{
			sent[k]=str[i];
			i++;
			k++;
		}
		sent[k]='\0';
		i++;
		if(isEqual(sent,str2))
		{
			int uz=lenght(sent);
			for(int t=i-uz-1;str[t+uz]!='\0';t++)
			{
				str[t]=str[t+uz+1];
			}
		}
		clearStr(sent);
	}
}
void clearStr(char *str)
{
	str[0]='\0';
}

void delWord(char *str,char w)
{
	for(int i=0;str[i]!='\0';i++)
	{
		if(str[i]==w)
		{
			for(int t=i;str[t]!='\0';t++)
			{
				str[t]=str[t+1];
			}
		}
	}
}

void mixWord(char *str)
{
	char temp;
	srand(static_cast<unsigned int>(time(0)));
	int i=0;
	int uzunluk;
	for(i=0;str[i]!='\0';)
	{
		uzunluk=0;
		while(str[i]!=' ' && str[i]!='\0')
		{
			i++;
			uzunluk++;
		}
		i++;
		
		int rast;
		for(int t=i-uzunluk-1;str[t]!=' ' && str[t]!='\0';t++)
		{
			rast=i-uzunluk-1 +rand()%uzunluk;
			temp=str[t];
			str[t]=str[rast];
			str[rast]=temp;
		}
	}
}

void capLet(char *str)
{
	cout<<str[0];
	int i=0;
	while(str[i]!='\0')
	{
		if(str[i]==' ')
		{
			cout<<str[i+1];
		}
		i++;
	}
}

int findRepeat(char *str,char *str2)
{
	int i=0;
	char sent[100];
	int repeat=0;
	while(str[i]!='\0')
	{
		int k=0;
		while(str[i]!=' ' && str[i]!='\0')
		{
			sent[k]=str[i];
			i++;
			k++;
		}
		sent[k]='\0';
		i++;
		if(isEqual(sent,str2))
		{
			repeat++;
		}
		clearStr(sent);
	}
	
	return repeat;
	
}

void reverse(char *str)
{
	char sent[100];
	clearStr(sent);
	int i=lenght(str);
	int t=0;
	while(i>=-1)
	{
		if(str[i]==' ' || str[i]=='\0' || i==-1)
		{
			
			int k=i+1;
			while(str[k]!=' ' && str[k]!='\0')
			{
				sent[t]=str[k];
				k++;
				t++;
				
			}
			
			if(str[i] == ' ')
        	{
            	sent[t] = ' ';
            	t++;
        	}
			
		}
		
		i--;
	}
	//clearStr(str);
	
	for(int c=0;c<lenght(str);c++)
	{
		str[c]=' ';
	}
	for(int a=0;sent[a]!='\0';a++)
	{
		str[a]=sent[a];
	}
}
