#include <stdio.h>

#define ARRAY_NUM 3

void printMatrix(double *a,int num);
void productMatrix(double *a,double*b,int num,double *ans);
double inSumMatrix(double *a,int num);
void sumMatrix(double *a,double *b,int num,double *ans);
void scaleMatrix(double *a,double c,int num);


int main(){
	
	double x[]={2,-1,1};
	double x1[]={1,0,0},x2[]={0,0.6,0.8},x3[]={0,0.8,-0.6};
	double ans1[ARRAY_NUM],ans2[ARRAY_NUM],ans3[ARRAY_NUM],fans[ARRAY_NUM],buf[ARRAY_NUM];
	double c1,c2,c3;

	printf("-----ベクトル-----\n");
	printf("x1=\n");
	printMatrix(x1,ARRAY_NUM);
	printf("\n");
	printf("x2=\n");
	printMatrix(x2,ARRAY_NUM);
	printf("\n");
	printf("x3=\n");
	printMatrix(x3,ARRAY_NUM);
	printf("------------------\n");

	printf("-------内積-------\n");
	productMatrix(x1,x1,ARRAY_NUM,buf);
	printf("x1*x1=%.2lf\n",inSumMatrix(buf,ARRAY_NUM));
	productMatrix(x1,x2,ARRAY_NUM,buf);
	printf("x1*x2=%.2lf\n",inSumMatrix(buf,ARRAY_NUM));
	productMatrix(x1,x3,ARRAY_NUM,buf);
	printf("x1*x3=%.2lf\n",inSumMatrix(buf,ARRAY_NUM));
	printf("\n");
	productMatrix(x2,x1,ARRAY_NUM,buf);
	printf("x2*x1=%.2lf\n",inSumMatrix(buf,ARRAY_NUM));
	productMatrix(x2,x2,ARRAY_NUM,buf);
	printf("x2*x2=%.2lf\n",inSumMatrix(buf,ARRAY_NUM));
	productMatrix(x2,x3,ARRAY_NUM,buf);
	printf("x2*x3=%.2lf\n",inSumMatrix(buf,ARRAY_NUM));
	printf("\n");
	productMatrix(x3,x1,ARRAY_NUM,buf);
	printf("x3*x1=%.2lf\n",inSumMatrix(buf,ARRAY_NUM));
	productMatrix(x3,x2,ARRAY_NUM,buf);
	printf("x3*x2=%.2lf\n",inSumMatrix(buf,ARRAY_NUM));
	productMatrix(x3,x3,ARRAY_NUM,buf);
	printf("x3*x3=%.2lf\n",inSumMatrix(buf,ARRAY_NUM));
	printf("------------------\n");

	printf("-------成分-------\n");
	productMatrix(x,x1,ARRAY_NUM,ans1);
	productMatrix(x,x2,ARRAY_NUM,ans2);
	productMatrix(x,x3,ARRAY_NUM,ans3);
	printf("a1 = %.2lf\n",c1=inSumMatrix(ans1,ARRAY_NUM));
	printf("a2 = %.2lf\n",c2=inSumMatrix(ans2,ARRAY_NUM));
	printf("a3 = %.2lf\n",c3=inSumMatrix(ans3,ARRAY_NUM));
	printf("------------------\n");

	scaleMatrix(x1,c1,ARRAY_NUM);
	scaleMatrix(x2,c2,ARRAY_NUM);
	scaleMatrix(x3,c3,ARRAY_NUM);

	sumMatrix(x1,x2,ARRAY_NUM,fans);
	sumMatrix(x3,fans,ARRAY_NUM,fans);
	
	printf("\n");
	printf("a1*x1 + a2*x2 + a3*x3 = [%.2lf,%.2lf,%.2lf]\n",fans[0],fans[1],fans[2]);

	return 0;
}

void printMatrix(double *a,int num){
	int cnt=0;
	for(;num>0;num--){
		printf("|%5.2lf|\n",a[cnt]);
		cnt++;
	}
	return;
}

void productMatrix(double *a,double *b,int num,double *ans){
	int cnt=0;
	for(;num>0;num--){
		ans[cnt]=(double)a[cnt]*(double)b[cnt];
		cnt++;
	}
	return;
}

double inSumMatrix(double *a,int num){
	int cnt=0;
	double sum=0;
	for(;num>0;num--){
		sum+=a[cnt];
		cnt++;
	}
	return sum;
}

void sumMatrix(double *a,double *b,int num,double *ans){
	int cnt=0;
	for(;num>0;num--){
		ans[cnt]=a[cnt]+b[cnt];
		cnt++;
	}
	return;
}

void scaleMatrix(double *a,double c,int num){
	int cnt=0;
	for(;num>0;num--){
		a[cnt]=a[cnt]*c;
		cnt++;
	}
	return;
}


