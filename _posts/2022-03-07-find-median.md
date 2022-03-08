---
layout: post
title: 面试reviews
date: 2022-03-01
author: 麻瓜码农
categories: [interview]
comments: true
toc: true
---

面试整理总结 查缺补漏！！
## Find Median

### Find Median from Data Stream

https://leetcode.com/problems/find-median-from-data-stream/

1. two heaps: min and max
2. heap balance


    a. add to max heap -> O(logN)
    b. add max.peek() to min heap -> O(logN)
    c. delete max heap peek -> O(logN)
    d. compare max size and min size
    e. if max size is smaller 
    f. add min peek to max -> O(logN)
    g. delete min peek -> O(logN)


注意heap的插入之间复杂度和顶部删除都是O(logN).

Time complexity: O(logN)

Space complexity: O(1)

    // two heaps
    // minHeap and maxHeap
    // mid = (minHead + maxHeap) / 2 or maxHeap.peek();
    // 1. add to minHeap
    // 2. add to maxHeap
    
    PriorityQueue<Integer> min;
    PriorityQueue<Integer> max;

    public MedianFinder() {
        min = new PriorityQueue<>();
        max = new PriorityQueue<>((a, b) -> (b - a));
    }
    
    // O(logN) 3 * heap insertion, 2 * heap deletion from top O(logN)
    public void addNum(int num) {
        max.add(num);
        //balance step
        min.add(max.peek());
        max.poll();
        if (max.size() < min.size()) {
            max.add(min.peek());
            min.poll();
        }
    }
    
    public double findMedian() {
        
        return max.size() == min.size() ? (double) (max.peek() + min.peek()) / 2 : max.peek();
    }


### Median of Two Sorted Arrays

https://leetcode.com/problems/median-of-two-sorted-arrays/

// L1 | R1 

// L2 | R2

// L1 < R2 and L2 < R1 and L1 + L2 = (len1 + len2) / 2;

binary search on nums1 or nums2


    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        // L1 | R1 
        // L2 | R2 
        // L1 < R2 and L2 < R1 and L1 + L2 = (len1 + len2) / 2;
        
        int len1 = nums1.length;
        int len2 = nums2.length;
        
        if (len1 > len2) {
            return findMedianSortedArrays(nums2, nums1);
        }
        int start = 0;
        int end = len1;
        
        while (start <= end) {
            int mid = (start + end) / 2;
            int cut1 = mid;
            int cut2 = (len1 + len2) / 2 - mid;
            
            int L1 = cut1 == 0 ? Integer.MIN_VALUE : nums1[cut1 - 1];
            int R1 = cut1 == len1 ? Integer.MAX_VALUE : nums1[cut1];
            int L2 = cut2 == 0 ? Integer.MIN_VALUE : nums2[cut2 - 1];
            int R2 = cut2 == len2 ? Integer.MAX_VALUE : nums2[cut2];

            if (L1 > R2) {
                end = mid - 1;
            } else if (L2 > R1) {
                start = mid + 1;
            } else {
                return (len1 + len2) % 2 == 0 ? ((double) Math.max(L1, L2) + (double) Math.min(R1, R2)) / 2 : Math.min(R1, R2);
            }
        }
        
        return len2 % 2 != 0 ? nums2[len2 / 2] : ((double) nums2[len2 / 2 - 1] + (double) nums2[len2 / 2]) / 2;
    }
