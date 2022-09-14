#bubble sort
#0,1..1,2..2,3 옆 인덱스의 수와 비교해서 크다면 자리 바꿈
#배열의 길이만큼 두 수를 비교하면서 앞자리 자리가 크다면 바꿈
def bubble_sort(a):
    n=len(a)
    for i in range(n):
        for j in range(0,n-i-1):
            if a[j]>a[j+1]:
                a[j],a[j+1]=a[j+1],a[j]
            print(a) #과정 출력
    #최종출력하기
    for i in range(n):
        print("%d " %a[i], end = "")
        
a=[7,5,8,1,2,9,3,6]
bubble_sort(a)