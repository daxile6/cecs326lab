#include <stdio.h>
#include <sys/stat.h>
#include <sys/mman.h>
#include <fcntl.h>
#include <unistd.h>
#include <time.h>
#include <signal.h>
#include <stdbool.h>
#include<stdlib.h>
void printSwim_Mill();
void intHandler(int);
// void handle_sigint(int);
static volatile int running =1;
pid_t fish;
pid_t pellet;
int* mySharedMem;

int main(int argc, char** argv){
   

   const char* name = "Array";
   int shm_fd;
   shm_fd = shm_open(name, O_CREAT | O_RDWR, S_IRWXU);
   
   ftruncate(shm_fd, sizeof(char) *40);  
   /*
   fish[0]
   pellet_info[1-4]
   pellet_itsel[1-4][5-8][9-12][13-16][17-20][21-24]
   number of pellets[25]
   next_memory_of_pellet[26];
   nummber of pellets caught[10]
   */
   mySharedMem = mmap(NULL, sizeof(int) *40, PROT_WRITE, MAP_SHARED, shm_fd, 0);
   char swim_mill[50];
   // mySharedMem[0] = 1;
   // mySharedMem[1] = 2;
   // mySharedMem[2] = 3;
   mySharedMem[25] = 0;
   mySharedMem[26] =0;

   // printf("%d",mySharedMem[3]);


   time_t startTime;
   time_t now;
   float elapsedTime;
   float timer = 30;
   time(&startTime);
   mySharedMem[8]= elapsedTime;
   mySharedMem[9] = timer;
   mySharedMem[10] =0;

   signal(SIGINT, intHandler);
   for (int i = 0; i < 50; i++){
      swim_mill[i] = '~';
      }
   swim_mill[mySharedMem[0]] = 'F';

   fish = fork();
   if(fish <0){
      perror("The fish process was not created successfully");
   }
   else if( fish == 0){
       printf("this is the child fish process: %d ",fish);
       printf("\n");
       printf("now we will enter fish.c ");
       char* args[] = {"fish",NULL};
       execv(args[0],args);
       printf("If you're getting this message then you have ran into a error using execv");
       
   }
   else{
      for(int i=0; i< 6;i++){
               pellet = fork();
               if (pellet < 0 ){
               perror("The pellet process was not created successfully");
               printf("\n");
               }
               else if(pellet ==0){
               printf("this is the child pellet process: %d ",pellet);
               printf("\n");
               printf("now we will enter pellet.c ");
               char* args[] = {"pellet",NULL};
               execv(args[0],args);
               printf("If you're getting this message then you have ran into a error using execv");
               }

            //    else{
            //       for (int i = 0; i < 50; i++){
            //          swim_mill[i] = '~';

            //       }
            //       swim_mill[mySharedMem[0]] = 'F';

            //       for(int i= 1; i<7;i++){
            //       swim_mill[mySharedMem[i]] = 'P';
            //       }
            //       printSwim_Mill(swim_mill);
            //       printf("\n");
            //       now = time(NULL);
            //       elapsedTime = difftime(now,startTime);
            // }

            sleep(1);
            }   
   }
   printf("testing");
   // int pellet_ID1 = mySharedMem[2];
   // int pellet_ID2 = mySharedMem[5];
   // int pellet_ID3 = mySharedMem[9];
   // printf("fish: %d", mySharedMem[0]);
   // printf("\n");
   // printf("Pellet-ID1: %d", pellet_ID1);
   // printf("\n");
   // printf("Pellet-ID2: %d", pellet_ID2);
   // printf("\n");
   // printf("Pellet-ID3: %d", pellet_ID3);
   // printf("\n");
   printf("sharedmem[1]: %d", mySharedMem[1]);
   printf("\n");
   printf("sharedmem[2]: %d", mySharedMem[2]);
    printf("\n");
   printf("sharedmem[3]: %d", mySharedMem[3]);
    printf("\n");
   printf("sharedmem[4]: %d", mySharedMem[4]);
    printf("\n");
     printf("sharedmem[5]: %d", mySharedMem[5]);
   printf("\n");
   printf("sharedmem[6]: %d", mySharedMem[6]);
    printf("\n");
   printf("sharedmem[7]: %d", mySharedMem[7]);
    printf("\n");
   printf("sharedmem[8]: %d", mySharedMem[8]);
    printf("\n");
    printf("sharedmem[9]: %d", mySharedMem[9]);
    printf("\n");
     printf("sharedmem[10]: %d", mySharedMem[10]);
   printf("\n");
   printf("sharedmem[11]: %d", mySharedMem[11]);
    printf("\n");
   printf("sharedmem[12]: %d", mySharedMem[12]);
    printf("\n");
   printf("sharedmem[13]: %d", mySharedMem[13]);
    printf("\n");
    printf("sharedmem[14]: %d", mySharedMem[14]);
    printf("\n");
    printf("sharedmem[15]: %d", mySharedMem[15]);
    printf("\n");
    printf("sharedmem[16]: %d", mySharedMem[16]);
    printf("\n");
    printf("sharedmem[17]: %d", mySharedMem[17]);
    printf("\n");
    printf("sharedmem[18]: %d", mySharedMem[18]);
    printf("\n");
    printf("sharedmem[19]: %d", mySharedMem[19]);
    printf("\n");
    printf("sharedmem[20]: %d", mySharedMem[20]);
    printf("\n");


   // for(int i =1; i<7;i++){

   // }
   swim_mill[mySharedMem[16]*11 + mySharedMem[15]] = 'P';
   printSwim_Mill(swim_mill);
   

   // int new_timer = 1;
   // int max =30;
   // printf("starting");
   // printSwim_Mill(swim_mill);
   // printf("\n");
   // printf("Dropping the pellets in the stream");
   // for(int i =1; i<7; i++){
   //    swim_mill[mySharedMem[i]] = 'P';
   //    printSwim_Mill(swim_mill);
   //    printf("\n");
   //       // sleep(1);
   //       // now = time(NULL);
   //       // elapsedTime = difftime(now,startTime);
   //       // // sleep(1);
   //       // new_timer +=1;
   //    }

   // printf("Pellets Dropping");
   // for(int i = 0; i<5;i++){
   //    for(int i=1; i<7;i++){
   //    swim_mill[mySharedMem[i]] = '~';
   //    swim_mill[mySharedMem[i]+10] = 'P';
   //    printSwim_Mill(swim_mill);
   //    printf("\n");
   //    }

   // }

   // printf("FINAL SWIM_MILL");
   // printSwim_Mill(swim_mill);
   //    // printSwim_Mill(swim_mill);
   //    // printf("\n");
   //    // now = time(NULL);
   //    // elapsedTime = difftime(now,startTime);
   //    //check that every index store in the array has a P
   //    //if it does then don't do anything
   //    // if it does not then need to put a P there and make the position above that into a ~ and make next P+=10


   
}
  

void printSwim_Mill(char swim_mill[]){
   for (int i=0; i< 5; i++){
            for (int j=0; j< 10; j++){
               printf("%c", swim_mill[i*10 +j]);
            }
            printf("\n");
         }
}

void intHandler(int dummy){
   printf("\n");
   printf("ProcessKilled");
   printf("\n");
   running = 0;
   kill(fish,SIGINT);
   printf("\n");
   printf("fish has been killed");
   printf("\n");
   kill(pellet,SIGINT);
   printf("\n");
   printf("pellet has been killed");
   printf("\n");
   int detach = munmap(NULL,sizeof(int)*40);
   if (detach == -1){
      perror("You got an error trying to detach!");
   }

   else{
      printf("\n");
      printf("Succesfully detached Memory");
      printf("\n");
   }

}
