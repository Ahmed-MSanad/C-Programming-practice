```
// This is Queue.h File

#ifndef CIRCULAR_QUEUE_OPTOMIZED_H
#define CIRCULAR_QUEUE_OPTOMIZED_H

#include "platFormTypes.h"

#define ZERO 0
#define DEBUG

typedef struct{
    void **data;        /* double pointer to an array of void pointers */
    sint32 QueueFront;
    sint32 QueueRear;
    sint32 CurrentSize;
    uint32 QueueSize;
}Queue;

/*
    using #defines instead of enum is more save
    in speaking of the memory space as the enum
    size is compiler dependent.
*/


typedef enum{
    Q_OK = 0,
    Q_NOK,
    Q_FULL,
    Q_EMPTY,
    Q_NULL_POINTER,
}QueueState;

Queue *CreateQueue(uint32 Size,QueueState *retState);

QueueState DestroyQueue(Queue *q);

QueueState Enqueue(Queue *q,void *data);

void *Dequeue(Queue *q,QueueState *retState);

QueueState DisplayQueue(Queue *q);

void *QueueFront(Queue *q,QueueState *retState);

void *QueueRear(Queue *q,QueueState *retState);

QueueState GetCurrentSize(Queue *q,
                          uint32 *QueueSize);

#endif // CIRCULAR_QUEUE_OPTOMIZED_H

```
