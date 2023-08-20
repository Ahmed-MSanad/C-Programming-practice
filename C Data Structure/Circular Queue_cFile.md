```
// This is Oueue.c file

#include <stdio.h>
#include <stdlib.h>

#include "Circular_Queue_Optomized.h"

Queue *CreateQueue(unsigned int Size,QueueState *retState){
    Queue *q = NULL;
    *retState = Q_NOK;

    if(NULL == retState){
        *retState = Q_NULL_POINTER;
        q = NULL;
    }
    else{
        /* Create the Queue Structure */
        q = (Queue *)malloc(sizeof(Queue));
        if(NULL == q){
            *retState = Q_NOK;
            q = NULL;
        }
        else{
            /* Create the array of void pointers */
            q->data = (void **)calloc(Size,sizeof(void *));

            if(!q->data){
                *retState = Q_NOK;
                free(q);
                q = NULL;
            }
            else{
                q->QueueRear = -1;
                q->QueueFront = -1;
                q->CurrentSize = 0;
                q->QueueSize = Size;
                *retState = Q_OK;
            }
        }
    }
    return q;
}


QueueState DestroyQueue(Queue *q){
    QueueState retState;
    if(NULL == q){
        retState = Q_NULL_POINTER;
    }
    else{
        free(q->data);
        q->data = NULL;
        free(q);
        q = NULL;
        retState = Q_OK;
    }
    return retState;
}

static unsigned char isFull(Queue *q){
    return (q->CurrentSize >= (q->QueueSize));
}

static unsigned char willDoRareCircle(Queue *q){
    return (q->QueueRear == q->QueueSize);
}

static void DoRareCircle(Queue *q){
    q->QueueRear = 0;
}

QueueState Enqueue(Queue *q,void *data)
{
    QueueState retState = Q_NOK;
    if((NULL == q) || (NULL == data)){
        #ifdef DEBUG
        printf("NULL pointer is sent !!\n");
        #endif // DEBUG
        retState = Q_NOK;
    }
    else if(isFull(q)){
        #ifdef DEBUG
        printf("The queue is FULL !!\n");
        #endif // DEBUG
        retState = Q_FULL;
    }
    else{
        (q->QueueRear)++;
        if(willDoRareCircle(q)){
/* NOTE: we are sure that the queue isn't full
so assigning rear to 0 won't override any value
as if the front is in position 0 then the
else if would be implemented */
            DoRareCircle(q);
        }
        else{}
        q->data[q->QueueRear] = data;
        if(q->CurrentSize == 0){
            q->CurrentSize = 1;
            q->QueueFront = 0;
        }
        else{
            q->CurrentSize++;
        }
        retState = Q_OK;
    }
    return retState;
}

static unsigned char isEmpty(Queue *q){
    return (q->CurrentSize == ZERO);
}

static unsigned char willDoFrontCircle(Queue *q){
    return ((q->QueueFront >= q->QueueSize));
}

static void DoFrontCircle(Queue *q){
    q->QueueFront = 0;
}


void *Dequeue(Queue *q,QueueState *retState)
{
    void *DequeuedValue = NULL;
    if(NULL == q || NULL == retState){
        #ifdef DEBUG
        printf("NULL pointer is sent !!\n");
        #endif // DEBUG
        *retState = Q_NULL_POINTER;
        DequeuedValue = NULL;
    }
    else if(isEmpty(q)){
        #ifdef DEBUG
        printf("The queue is already Empty !!\n");
        #endif // DEBUG
        *retState = Q_EMPTY;
        DequeuedValue = NULL;
    }
    else{
        DequeuedValue = q->data[q->QueueFront];
        q->QueueFront++;
        q->CurrentSize--;
        if(willDoFrontCircle(q)){
            DoFrontCircle(q);
        }
        else{}
        if(0 == q->CurrentSize){
/*Queue is empty*/
            q->QueueFront = q->QueueRear = -1;
        }
        else{}
        *retState = Q_OK;
    }
    return DequeuedValue;
}

QueueState DisplayQueue(Queue *q){
    QueueState retState;
    if(NULL == q){
        #ifdef DEBUG
        printf("NULL pointer is sent !!\n");
        #endif // DEBUG
        retState = Q_NULL_POINTER;
    }
    else if(isEmpty(q)){
        #ifdef DEBUG
        printf("The queue is already Empty !!\n");
        #endif // DEBUG
        retState = Q_EMPTY;
    }
    else{
        unsigned int counter = q->QueueFront;
        while(counter != q->QueueRear){
            if(counter == q->QueueSize)counter = 0;
            printf("%i - ",*(unsigned int *)q->data[counter]);
            counter++;
        }
        printf("%i\n",*(unsigned int *)q->data[counter]);
        retState = Q_OK;
    }
    return retState;
}

void *QueueFront(Queue *q,QueueState *retState){
    void *retValue = NULL;
    if(NULL == q || NULL == retState){
        *retState = Q_NULL_POINTER;
    }
    else if(isEmpty(q)){
        *retState = Q_EMPTY;
        retValue = NULL;
    }
    else{
        retValue = q->data[q->QueueFront];
        *retState = Q_OK;
    }
    return retValue;
}

void *QueueRear(Queue *q,QueueState *retState){
    void *retValue = NULL;
    if(NULL == q || NULL == retState){
        *retState = Q_NULL_POINTER;
    }
    else if(isEmpty(q)){
        *retState = Q_EMPTY;
        retValue = NULL;
    }
    else{
        *retState = Q_OK;
        retValue = q->data[q->QueueRear];
    }
    return retValue;
}

QueueState GetCurrentSize(Queue *q,
                          uint32 *QueueSize)
{
    QueueState retState = Q_NOK;
    if((NULL == q) || (NULL == QueueSize)){
        #ifdef DEBUG
        printf("NULL Queue structure OR NULL Queue Size variable!!\n");
        #endif // DEBUG
        retState = Q_NOK;
    }
    else{
        retState = Q_OK;
        *QueueSize = q->CurrentSize;
    }
    return retState;
}

```
