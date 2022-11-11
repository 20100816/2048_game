#include<bits/stdc++.h>
#include<windows.h>
#include<conio.h>
using namespace std;
const int N=4; //边长
/*
上: 72
下: 80
左: 75
右: 77 
*/
class game {
	// Private section
	public:
		// Public Declarations
		void Initializing(string T){
			title=T;
			score=0;
			Max_s=0;
			sum_s=0;
			for(int i=1;i<=N;i++)
				for(int j=1;j<=N;j++)
					Map[i][j]=0;
		}
		void Hide(){//用于隐藏控制台光标 
			HANDLE				hOut;
			CONSOLE_CURSOR_INFO	curInfo;
			hOut=GetStdHandle(STD_OUTPUT_HANDLE); 
			curInfo.dwSize=1;
			curInfo.bVisible=0;
			SetConsoleCursorInfo(hOut,&curInfo);
		}
		void paint(){
			int s=5*N+1-title.size()+4;
			for(int i=1;i<=s/2;i++) cout<<' ';
			cout<<title;
			for(int i=1;i<=s/2;i++) cout<<' ';
			cout<<endl;
			cout<<"sorce: "<<score<<" Producer: David"<<endl;
			cout<<"  ";
			for(int i=1;i<=N*5+1;i++) cout<<'-';
			cout<<endl;
			for(int i=1;i<=N;i++){
				cout<<"  ";
				cout<<'|';
				for(int j=1;j<=N;j++){
					if(Map[i][j]){
						cout<<setw(4)<<Map[i][j];
						cout<<'|'; 
					}else{
						cout<<"    |"; 
					}
				}
				cout<<endl;
				cout<<"  ";
				for(int i=1;i<=N*5+1;i++) cout<<'-';
				cout<<endl;
			}
		}
		bool over(){
			for(int i=1;i<=N;i++){
				for(int j=1;j<=N;j++){
					if(Map[i][j]==Map[i-1][j]||Map[i][j]==Map[i][j-1]||Map[i][j]==Map[i][j+1]||Map[i][j]==Map[i+1][j])
						return 0;
				}
			}
			return 1;
		}
		void Generated(){
			srand(time(0));
			int x=rand()%N+1,y=rand()%N+1;
			while(Map[x][y]!=0){
				x=rand()%N+1,y=rand()%N+1;
			}
			Map[x][y]=2;
		}
		void up(){
			for(int i=1;i<=N;i++){
				for(int j=N;j>=1;j--){
					if(Map[i][j]!=0){
						for(int k=i;k>=1;k--){
							if(!Map[k][j]){
								Map[k][j]=Map[k+1][j];
								Map[k+1][j]=0;
								continue;
							}
							if(Map[k][j]==Map[k+1][j]){
								Map[k][j]*=2;
								score+=Map[k][j];
								Max_s=max(Max_s,Map[k][j]);
								sum_s--;
								Map[k+1][j]=0;
								break;
							}
						}
					}
				}
			}
			if(sum_s!=N*N){
				sum_s++;
				Generated();
			}
		}
		void down(){
			for(int i=N;i>=1;i--){
				for(int j=1;j<=N;j++){
					if(Map[i][j]!=0){
						for(int k=i;k<=N;k++){
							if(!Map[k][j]){
								Map[k][j]=Map[k-1][j];
								Map[k-1][j]=0;
								continue;
							}
							if(Map[k][j]==Map[k-1][j]){
								Map[k][j]*=2;
								score+=Map[k][j];
								Max_s=max(Max_s,Map[k][j]);
								sum_s--;
								Map[k-1][j]=0;
								break;
							}
						}
					}
				}
			}
			if(sum_s!=N*N){
				sum_s++;
				Generated();
			}
		}
		void left(){ 
			for(int i=1;i<=N;i++){
				for(int j=1;j<=N;j++){
					if(Map[i][j]!=0){
						for(int k=j;k>=1;k--){
							if(!Map[i][k]){
								Map[i][k]=Map[i][k+1];
								Map[i][k+1]=0;
								continue;
							}
							if(Map[i][k]==Map[i][k+1]){
								Map[i][k]*=2;
								score+=Map[i][k];
								Max_s=max(Max_s,Map[i][k]);
								sum_s--;
								Map[i][k+1]=0;
								break;
							}
						}
					}
				}
			}
			if(sum_s!=N*N){
				sum_s++;
				Generated();
			}
		}
		void right(){
			for(int i=1;i<=N;i++){
				for(int j=N;j>=1;j--){
					if(Map[i][j]!=0){
						for(int k=j;k<=N;k++){
							if(!Map[i][k]){
								Map[i][k]=Map[i][k-1];
								Map[i][k-1]=0;
								continue;
							}
							if(Map[i][k]==Map[i][k-1]){
								Map[i][k]*=2;
								score+=Map[i][k];
								Max_s=max(Max_s,Map[i][k]);
								sum_s--;
								Map[i][k-1]=0;
								break;
							}
						}
					}
				}
			}
			if(sum_s!=N*N){
				sum_s++;
				Generated();
			}
		}		
		void test(){
			int key=getch();
			key=getch();
			if(key==72) up();
			if(key==80) down();
			if(key==75) left();
			if(key==77) right();
		}
		void run(){
			system("title 2048小游戏"); //设置窗口名称 
			Hide(); 
			while(1){
				if(sum_s==N*N&&over()){
					cout<<"You lose! You got"<<score<<"point.";
					system("pause");
					return;
				}
				if(Max_s==2048){
					cout<<"You winner!";
					system("pause");
					return;
				}
				paint();
				test();
				system("cls");
			}
		} 
	protected:
		// Protected Declarations
		int Map[N+2][N+2];  //地图 
		string title; //游戏名字 
		int score; //分数
		int Max_s; //场上最高方块(_s:方块)
		int sum_s; //一共的方块总数 
};
int main(){
	game s;
	s.Initializing("2048 games");
	s.run(); 
	return 0;
}
