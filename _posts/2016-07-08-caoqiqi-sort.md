---
layout: post
title: 排序
date: 2016-07-10
excerpt: 各种排序的js代码实现
tags: [冒泡,直插,选择,希尔,堆,归并,快速]
comments: true
---
<style type="text/css">
    *{
    font-family:"幼圆";
    font-weight:bold;   
}
    h2{
    color:#000;
    background-color:#1CA366;
}
    em{
    color:red;
}
    h3{
    color:#2841D8;
}
</style>

## 冒泡排序
 
```javascript
function bubbleSort(arr){
        for(var i=1;i<arr.length;i++){
            for(var j=arr.length-1;j>i-1;j--){
                if(arr[j]<arr[j-1]){
                    var temp=arr[j];
                    arr[j]=arr[j-1];
                    arr[j-1]=temp;
                }
            }
        }
        document.write('<br />冒泡排序'+arr);
    }
```

## 直接插入排序
 
```javascript
function insertSort(arr){
        for(var i=1;i<arr.length;i++){
            var temp=arr[i];
            for(var j=i-1;j>=0&&temp<arr[j];j--){
                arr[j+1]=arr[j];
                
            }
            arr[j+1]=temp;
            
        }
        document.write('<br />直接插入排序'+arr);
}
```

## 选择排序
 
```javascript
function selectSort(arr){
        var temp = 0;
        for(var i=0;i<arr.length-1;i++){
            var min=i;
            for(var j=i;j<arr.length;j++){
                if(arr[min]>arr[j]){
                    min = j;
                }
            }
            if(min!=i){
                temp = arr[i];
                arr[i] = arr[min];
                arr[min] = temp;
            }
        }
        document.write('<br />选择排序'+arr);
}
```


## 希尔排序
 
```javascript
function shellSort(arr){
        for(var l=Math.floor(arr.length/2);l>=1;l=Math.floor(l/2)){
            for(var i=l;i<arr.length;i++){
                for(var j=i-l;j>=0&&arr[j+l]<arr[j];j-=l){
                    var temp=arr[j+l];
                    arr[j+l]=arr[j];
                    arr[j]=temp;
                }
            }
        }
        document.write('<br />希尔排序'+arr);
}
```

## 堆排序
 
```javascript
function sort(arr,start,end){

            var Index=start;//存储根节点
            var left=2*start+1; //左节点
            var right=2*start+2; //右节点
            while(left<=end){//如果存在左节点
                if(arr[left]>arr[start]){//左节点大于父节点
                Index = left;
                }
                if(right<=end&&arr[right]>arr[Index]){//存在右节点且右节点大于Index节点
                Index = right;
                }
                //如果需要交换，则交换，更新根节点，左节点，右节点
                if(Index!=start){ 
                    var temp=arr[start];
                    arr[start]=arr[Index];
                    arr[Index]=temp;
                    start=Index;
                    left=2*start+1;
                    right=2*start+2;
                //不需要交换，则跳出
                }else{
                    break;
                }
                
            }
        }
        //堆排序
        function heapSort(arr){
            var len=arr.length;
            //构造大根堆
            for(var j=Math.floor((len-2)/2);j>=0;j--){
                sort(arr,j,len-1);
            }

            //交换第一个节点与剩余树的最后一个节点
            for(var i=len-1;i>0;i--){
                var temp=arr[0];
                arr[0]=arr[i];
                arr[i]=temp;
                //调整堆
                sort(arr,0,i-1);
            }
            document.write('<br />堆排序'+arr);
        }
```

## 归并排序
 
```javascript
//将两个有序数组排序
        function merge(arr1,arr2){
            var result=[];
            while(arr1.length>0&&arr2.length>0){
                if(arr1[0]<arr2[0]){
                    result.push(arr1.shift());
                }else{
                    result.push(arr2.shift());
                }
            }
            return result.concat(arr1).concat(arr2);
        }

        //递归实现数组排序
        function mergeSort(arr){
            if(arr.length==1){
                return arr;
            }
            var middle=Math.floor(arr.length/2);
            var left=arr.slice(0,middle);
            var right=arr.slice(middle);
            return merge(mergeSort(left),mergeSort(right));
        } 
```

## 快速排序
 
```javascript
function quickSort(arr){
            var len=arr.length;
            var a=quick(0,len-1);
            document.write('</br>快速排序'+a);
        }

        function quick(start,end){
            var left=start;//左索引
            var right=end;//右索引
            var flag=arr[left];//标志值
            if((end-start)>1){
            while(left<right){
                for(;left<right;right--){
                    if(arr[right]<flag){
                        arr[left++]=arr[right];//将右索引位置的元素放到左索引的位置，左索引加1
                        break;
                    }
                }
                for(;left<right;left++){
                    if(arr[left]>flag){
                        arr[right--]=arr[left];//将左索引位置的元素放到右索引的位置，右索引加1
                        break;
                    }
                }
            }
            arr[left]=flag; //将标志值放入数组
            quick(0,left-1);
            quick(left+1,end);
            return arr;
        }
    }
```

## 直接用函数排序
 
```javascript
/*直接用函数排序*/
        arr.sort(function(a,b){return a-b;});
        document.write('直接用函数排序'+arr);
```
