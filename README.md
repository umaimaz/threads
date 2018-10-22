# threads
thread used to sum values
#include<stdio.h>
#include<stdlib.h>
#include<pthread.h>
int sum1[10];
int arr[1000];
int l=0,m=100;
int s=0;
void * thread(void *arg){

int val=0;

	for(int i=l; i<m; i++){
	    val=val+arr[i];
	}  
	l=l+100;
	m=m+100;
	sum1[s]=val;
	s++;
}

int main(){
int fsum=0;
 for(int i=0; i<1000; i++){

        arr[i]=i;
    }

        pthread_t threads[10];

     for(int i=0; i<10; i++){

	 pthread_create(&threads[i],NULL,thread,(void*)(NULL));
     }
     for(int j=0; j<10; j++){

         pthread_join(threads[j],NULL);
     }
	 for(int i=0;i<10;i++){
 	printf("\n%d",sum1[i]);
	 }
   
return 0;
}
