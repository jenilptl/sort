##quick sort 

#include<stdio.h>
#include<time.h>

int partition(int a[],int l,int r) {
  int pivot = a[l];
  int i = l+1;
  int j = r;

  while(1) {
    while(i<=r && a[i]<=pivot) {
      i++;
    }
    while(a[j]>pivot) {
      j--;
    }
    if(i<j) {
      int temp = a[i];
      a[i] = a[j];
      a[j] = temp;
      i++;
      j--;
    }
    else {
      break;
    }
  }
  a[l] = a[j];
  a[j] = pivot;
  return j;
}

void quickSort(int a[],int l,int r) {
  if(l<r) {
    int p = partition(a,l,r);
    quickSort(a,l,p-1);
    quickSort(a,p+1,r);
  }
}

void main() {
  int n,i,j;
  clock_t start,end;
  double time_taken;

  printf("Enter the size of an array:");
  scanf("%d",&n);

  int a[n];
  printf("Enter array elements:");
  for(i=0;i<n;i++) {
    scanf("%d",&a[i]);
  }

  start = clock();
  quickSort(a,0,n-1);
  end = clock();

  printf("Sorted array:\n");
  for(i=0;i<n;i++) {
    printf("%d ",a[i]);
  }

  time_taken = (double)(end-start)/CLOCKS_PER_SEC;
  printf("\nCPU time:%f",time_taken);
}

##bubble sort

#include<stdio.h>
#include<time.h>

void bubbleSort(int a[],int n) {
  int i,j,temp;

  for(i=0;i<n-1;i++) {
    for(j=0;j<n-i-1;j++) {
      if(a[j]>a[j+1]) {
        temp = a[j];
        a[j] = a[j+1];
        a[j+1] = temp;
      }
    }
  }
}

void main() {
  int n,i,j;
  clock_t start,end;
  double time_taken;

  printf("Enter the size of an array:");
  scanf("%d",&n);

  int a[n];
  printf("Enter array elements:");
  for(i=0;i<n;i++) {
    scanf("%d",&a[i]);
  }

  start = clock();
  bubbleSort(a,n);
  end = clock();

  printf("Sorted array:\n");
  for(i=0;i<n;i++) {
    printf("%d ",a[i]);
  }

  time_taken = (double)(end-start)/CLOCKS_PER_SEC;
  printf("\nCPU time:%f",time_taken);
}

##insertion sort

#include<stdio.h>
#include<time.h>

void insertionSort(int a[],int n) {
  int i,j,key;

  for(i=1;i<n;i++) {
    key = a[i];
    j = i-1;

    while(j>=0 && a[j]>key) {
      a[j+1] = a[j];
      j--;
    }

    a[j+1] = key;
  }
}

void main() {
  int n,i,j;
  clock_t start,end;
  double time_taken;

  printf("Enter the size of an array:");
  scanf("%d",&n);

  int a[n];
  printf("Enter array elements:");
  for(i=0;i<n;i++) {
    scanf("%d",&a[i]);
  }

  start = clock();
  insertionSort(a,n);
  end = clock();

  printf("Sorted array:\n");
  for(i=0;i<n;i++) {
    printf("%d ",a[i]);
  }

  time_taken = (double)(end-start)/CLOCKS_PER_SEC;
  printf("\nCPU time:%f",time_taken);
}

##selection sort

#include<stdio.h>
#include<time.h>

void selectionSort(int a[],int n) {
  int i,j,min,temp;

  for(i=0;i<n-1;i++) {
    min = i;

    for(j=i+1;j<n;j++) {
      if(a[j]<a[min]) {
        min = j;
      }
    }

    if(min!=i) {
      temp = a[i];
      a[i] = a[min];
      a[min] = temp;
    }
  }
}

void main() {
  int n,i,j;
  clock_t start,end;
  double time_taken;

  printf("Enter the size of an array:");
  scanf("%d",&n);

  int a[n];
  printf("Enter array elements:");
  for(i=0;i<n;i++) {
    scanf("%d",&a[i]);
  }

  start = clock();
  selectionSort(a,n);
  end = clock();

  printf("Sorted array:\n");
  for(i=0;i<n;i++) {
    printf("%d ",a[i]);
  }

  time_taken = (double)(end-start)/CLOCKS_PER_SEC;
  printf("\nCPU time:%f",time_taken);
}

##merge sort

#include<stdio.h>
#include<time.h>

void merge(int a[],int l,int m,int r) {
  int i,j,k;
  int n1 = m-l+1;
  int n2 = r-m;

  int b[n1],c[n2];

  for(i=0;i<n1;i++) {
    b[i] = a[l+i];
  }

  for(j=0;j<n2;j++) {
    c[j] = a[m+1+j];
  }

  i=0;
  j=0;
  k=l;

  while(i<n1 && j<n2) {
    if(b[i]<=c[j]) {
      a[k] = b[i];
      i++;
    }
    else {
      a[k] = c[j];
      j++;
    }
    k++;
  }

  while(i<n1) {
    a[k] = b[i];
    i++;
    k++;
  }

  while(j<n2) {
    a[k] = c[j];
    j++;
    k++;
  }
}

void mergeSort(int a[],int l,int r) {
  if(l<r) {
    int m = (l+r)/2;

    mergeSort(a,l,m);
    mergeSort(a,m+1,r);
    merge(a,l,m,r);
  }
}

void main() {
  int n,i,j;
  clock_t start,end;
  double time_taken;

  printf("Enter the size of an array:");
  scanf("%d",&n);

  int a[n];
  printf("Enter array elements:");
  for(i=0;i<n;i++) {
    scanf("%d",&a[i]);
  }

  start = clock();
  mergeSort(a,0,n-1);
  end = clock();

  printf("Sorted array:\n");
  for(i=0;i<n;i++) {
    printf("%d ",a[i]);
  }

  time_taken = (double)(end-start)/CLOCKS_PER_SEC;
  printf("\nCPU time:%f",time_taken);
}

