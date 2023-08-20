```
#include <stdio.h>
#include <stdlib.h>

#include "Circular_Queue_Optomized.h"

int main()
{
    Queue *Q1;

    QueueState retState;

    Q1 = CreateQueue(5,&retState);

    unsigned int var = 12;
    unsigned int var1 = 13;
    unsigned int var2 = 14;
    unsigned int var3 = 55;
    unsigned int var4 = 112;
    unsigned int var5 = 112;

    retState = Enqueue(Q1,&var);printf("retState = %i\n",retState);
    retState = Enqueue(Q1,&var1);printf("retState = %i\n",retState);
    retState = Enqueue(Q1,&var2);printf("retState = %i\n",retState);
    retState = Enqueue(Q1,&var3);printf("retState = %i\n",retState);
    retState = Enqueue(Q1,&var4);printf("retState = %i\n",retState);
    retState = Enqueue(Q1,&var5);printf("retState = %i\n",retState);

    DisplayQueue(Q1);

    printf("Popped element = %i\n",*(unsigned int *)Dequeue(Q1,&retState));printf("retState = %i\n",retState);
    DisplayQueue(Q1);

    printf("Queue Front: %i\n",*(unsigned int *)QueueFront(Q1,&retState));printf("retState = %i\n",retState);
    printf("Queue Rear: %i\n",*(unsigned int *)QueueRear(Q1,&retState));printf("retState = %i\n",retState);

    printf("Popped element = %i\n",*(unsigned int *)Dequeue(Q1,&retState));printf("retState = %i\n",retState);
    DisplayQueue(Q1);

    printf("Queue Front: %i\n",*(unsigned int *)QueueFront(Q1,&retState));printf("retState = %i\n",retState);
    printf("Queue Rear: %i\n",*(unsigned int *)QueueRear(Q1,&retState));printf("retState = %i\n",retState);

    printf("Popped element = %i\n",*(unsigned int *)Dequeue(Q1,&retState));printf("retState = %i\n",retState);
    DisplayQueue(Q1);

    printf("Queue Front: %i\n",*(unsigned int *)QueueFront(Q1,&retState));printf("retState = %i\n",retState);
    printf("Queue Rear: %i\n",*(unsigned int *)QueueRear(Q1,&retState));printf("retState = %i\n",retState);

    printf("Popped element = %i\n",*(unsigned int *)Dequeue(Q1,&retState));printf("retState = %i\n",retState);
    DisplayQueue(Q1);

    printf("Queue Front: %i\n",*(unsigned int *)QueueFront(Q1,&retState));printf("retState = %i\n",retState);
    printf("Queue Rear: %i\n",*(unsigned int *)QueueRear(Q1,&retState));printf("retState = %i\n",retState);


    retState = Enqueue(Q1,&var);printf("retState = %i\n",retState);
    retState = Enqueue(Q1,&var1);printf("retState = %i\n",retState);
    retState = Enqueue(Q1,&var2);printf("retState = %i\n",retState);
    retState = Enqueue(Q1,&var3);printf("retState = %i\n",retState);
    retState = Enqueue(Q1,&var4);printf("retState = %i\n",retState);
    retState = Enqueue(Q1,&var5);printf("retState = %i\n",retState);

    printf("Popped element = %i\n",*(unsigned int *)Dequeue(Q1,&retState));printf("retState = %i\n",retState);
    DisplayQueue(Q1);

    printf("Queue Front: %i\n",*(unsigned int *)QueueFront(Q1,&retState));printf("retState = %i\n",retState);
    printf("Queue Rear: %i\n",*(unsigned int *)QueueRear(Q1,&retState));printf("retState = %i\n",retState);

    printf("Popped element = %i\n",*(unsigned int *)Dequeue(Q1,&retState));printf("retState = %i\n",retState);
    DisplayQueue(Q1);

    printf("Queue Front: %i\n",*(unsigned int *)QueueFront(Q1,&retState));printf("retState = %i\n",retState);
    printf("Queue Rear: %i\n",*(unsigned int *)QueueRear(Q1,&retState));printf("retState = %i\n",retState);

    printf("Popped element = %i\n",*(unsigned int *)Dequeue(Q1,&retState));printf("retState = %i\n",retState);
    DisplayQueue(Q1);

    printf("Queue Front: %i\n",*(unsigned int *)QueueFront(Q1,&retState));printf("retState = %i\n",retState);
    printf("Queue Rear: %i\n",*(unsigned int *)QueueRear(Q1,&retState));printf("retState = %i\n",retState);

    printf("Popped element = %i\n",*(unsigned int *)Dequeue(Q1,&retState));printf("retState = %i\n",retState);
    DisplayQueue(Q1);

    printf("Queue Front: %i\n",*(unsigned int *)QueueFront(Q1,&retState));printf("retState = %i\n",retState);
    printf("Queue Rear: %i\n",*(unsigned int *)QueueRear(Q1,&retState));printf("retState = %i\n",retState);

    DisplayQueue(Q1);

    printf("Queue Front: %i\n",*(unsigned int *)QueueFront(Q1,&retState));printf("retState = %i\n",retState);
    printf("Queue Rear: %i\n",*(unsigned int *)QueueRear(Q1,&retState));printf("retState = %i\n",retState);


    printf("%i - %i - %i \n",Q1->CurrentSize,
           Q1->QueueFront,Q1->QueueRear);

    printf("Popped element = %i\n",*(unsigned int *)Dequeue(Q1,&retState));printf("retState = %i\n",retState);
/*Delete the last element*/

    Dequeue(Q1,&retState);printf("retState = %i\n",retState);
/* return value is NULL as the Queue is already empty so don't dereference it as it's NULL */

    DestroyQueue(Q1);

    return 0;
}

```
