
# 其它
* [c++在线编译器,c++语言在线解释器,在线编程网站](https://www.dooccn.com/cpp/)
* [十大经典排序算法最强总结 - hellozhxy的博客 - CSDN博客](https://blog.csdn.net/hellozhxy/article/details/79911867)
* [十大经典排序算法（动图演示） - 一像素 - 博客园](https://www.cnblogs.com/onepixel/p/7674659.html)


# 冒泡排序

* 无优化
```cpp
#include <iostream>

void swap(int* a, int *b){
    int tmp = *a; 
    *a = *b;
    *b = tmp;
}

void bubblesort(int* a, int n){
    for(int i=0; i<n; i++){
        for(int j=0; j<n-1; j++){
            if (a[j] > a[j+1]){
                swap(&a[j], &a[j+1]);
            }
        }
    }
}

int main(int argc, char** argv){
    int a[5] = {3,2,7,6,1};
    bubblesort(a, 5);
    
    for(int i=0; i<5; i++){
        std::cout << a[i] << " ";
    }
    std::cout << std::endl;
    
    return 0;
}
```


* 简单优化
```cpp
#include <iostream>

void swap(int* a, int *b){
    int tmp = *a; 
    *a = *b;
    *b = tmp;
}

void bubblesort(int* a, int n){
    for(int i=0; i<n-1; i++){
        // j < n-i-1
        for(int j=0; j<n-i-1; j++){
            if (a[j] > a[j+1]){
                swap(&a[j], &a[j+1]);
            }
        }
    }
}

int main(int argc, char** argv){
    int a[5] = {3,2,7,6,1};
    bubblesort(a, 5);
    
    for(int i=0; i<5; i++){
        std::cout << a[i] << " ";
    }
    std::cout << std::endl;
    
    return 0;
}

```





* 进一步优化
```cpp
#include <iostream>

void swap(int* a, int *b){
    int tmp = *a; 
    *a = *b;
    *b = tmp;
}

void bubblesort(int* a, int n){
    // 添加提前退出
    bool flag = false;
    for(int i=0; i<n-1; i++){
        flag = false;
        for(int j=0; j<n-i-1; j++){
            if (a[j] > a[j+1]){
                swap(&a[j], &a[j+1]);
                flag = true;
            }
        }
        if (!flag){
            break;
        }
    }
}

int main(int argc, char** argv){
    int a[5] = {3,2,7,6,1};
    bubblesort(a, 5);
    
    for(int i=0; i<5; i++){
        std::cout << a[i] << " ";
    }
    std::cout << std::endl;
    
    return 0;
}
```





# 选择排序

* 直接选择排序
```cpp
#include <iostream>

void swap(int* a, int *b){
    int tmp = *a; 
    *a = *b;
    *b = tmp;
}

void select_sort(int* a, int n){
    for(int i=0; i<n; i++){
        int min_v = a[i];
        int ind = i;
        for(int j=i+1; j<n; j++){
            if(a[j]<min_v){
                ind = j;
                min_v = a[j];
            }
        }
        swap(&a[i], &a[ind]);
    }
}

int main(int argc, char** argv){
    int a[5] = {3,2,7,6,1};
    select_sort(a, 5);
    
    for(int i=0; i<5; i++){
        std::cout << a[i] << " ";
    }
    std::cout << std::endl;
    
    return 0;
}
```


* 直接选择排序优化版（不需要临时变量）
```cpp
#include <iostream>

void swap(int* a, int *b){
    int tmp = *a; 
    *a = *b;
    *b = tmp;
}

void select_sort(int* a, int n){
    for(int i=0; i<n; i++){
        int ind = i;
        for(int j=i+1; j<n; j++){
            if(a[j]<a[ind]){
                ind = j;
            }
        }
        swap(&a[i], &a[ind]);
    }
}

int main(int argc, char** argv){
    int a[5] = {3,2,7,6,1};
    select_sort(a, 5);
    
    for(int i=0; i<5; i++){
        std::cout << a[i] << " ";
    }
    std::cout << std::endl;
    
    return 0;
}
```
