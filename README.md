






sandeepmaddalaa/sandeepmaddalaa is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.


#include <stdio.h>

#include <malloc.h>

typedef struct Node{

    int data;

    int empty;

    struct Node* next;

}node;  

struct ring_buffer{

    node *buff_start;

    node *start;

    node *end;

};

struct ring_buffer create_buffer(int size)

{

    struct ring_buffer b;

    b.start = (node *) malloc(sizeof(node));

    b.start->empty = 1;

    b.start->next = NULL;

    node *ptr = b.start;

    for(int i=0; i<size-1; i++){

        node *newNode = (node *) malloc(sizeof(node));

        newNode->empty = 1;

        newNode->next = NULL;

        ptr->next = newNode;

        ptr = ptr->next;

    }

    ptr->next = b.start;

    b.end = b.start;

    b.buff_start = b.start;

    return b;

}

void display(struct ring_buffer b)

{

    node* ptr = b.buff_start;

    do{

        if(ptr->empty == 1)

            printf("NULL -> ");

        else

            printf("%d -> ", ptr->data);

        ptr = ptr->next;

    }while(ptr != b.buff_start);

    printf("\b\b\b\b   \b\b\b\n");

}

struct ring_buffer enqueue(struct ring_buffer b, int data)

{

    b.end->data = data;

    b.end->empty = 0;

    b.end = b.end->next;

    return b;

}

struct ring_buffer dequeue(struct ring_buffer b)

{

    b.start->empty = 1;

    b.start = b.start->next;

    return b;

}

int main()

{

    struct ring_buffer b = {NULL, NULL}; 

    int size;

    printf("Enter the fixed size of the buffer: ");

    scanf("%d", &size);

    b = create_buffer(size);

    b = enqueue(b, 1);  display(b);

    b = enqueue(b, 2);  display(b);

    b = enqueue(b, 3);  display(b);

    b = enqueue(b, 4);  display(b);

    b = enqueue(b, 5);  display(b);

    b = enqueue(b, 6);  display(b);

    b = enqueue(b, 7);  display(b);

    b = enqueue(b, 8);  display(b);

    b = enqueue(b, 9);  display(b);

    b = enqueue(b, 10);  display(b);

    b = enqueue(b, 11);  display(b);

    b = dequeue(b);  display(b);

    b = dequeue(b);  display(b);

    b = dequeue(b);  display(b);

     

    b = enqueue(b, 12);  display(b);

    b = enqueue(b, 13);  display(b);

    // display(b);

    return 0;

}

    
  
   
      
          

         




