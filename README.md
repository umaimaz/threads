# threads
thread used to sum values
#include<stdio.h>
#include<stdlib.h>
#include<pthread.h>

void * thread(void *arg){
int sum[10];
int val=0;
int arr[1000];

    for(int i=0; i<1000; i++){

        arr[i]=i;
    }
int l=0,m=99;
    for(int j=0; j<10; j++){
l=l+1;
	for(int k=l; k<=m; k++){

	    val=val+arr[k];
	}  
	l=l+99;
	m=m+100;
	sum[j]=val;

        val=0;

    }
return((void *)sum);
}

int main(){

int sum_return[10];
        pthread_t threads[10];

     for(int i=1; i<=10; i++){

	 pthread_create(&threads[i],NULL,thread,NULL);
     }
     for(int j=1; j<=10; j++){

         pthread_join(threads[j],(void**)&sum_return[j]);
         printf("value returned by thread %d is %d\n" ,j, sum_return[j]);
     }
    
return 0;
}
