## Interview Experience - D.E. Shaw

#### Online Assessment  
Due to some technical difficulties, there were two online assessments and top 5 out of each of those were shortlisted further.

oa 1 problem 1 was identical to the one below (this problem appeared in the LeetCode weekly in the same week after the OA, quite the coincidence)

You are given a string \(s\) consisting of uppercase English letters.

You are allowed to insert **at most one** uppercase English letter at **any** position (including the beginning or end) of the string.

Return the **maximum** number of occurrences of \(\texttt{LCT}\) that can be formed in the resulting string after **at most one insertion**.

- Constraints: \(n \le 10^5\)  
- https://leetcode.com/problems/maximum-number-of-subsequences-after-one-inserting/

problem 2 was  
Given an array \(A\) of length \(n\). If you activate the \(i\)-th element (where \(A_i = x\)), you can choose to either cover indices \([i - x + 1,\,i]\) or \([i,\,i + x - 1]\). Find the minimum number of elements that need to be activated to cover the whole array, or report that it is impossible.

- Constraints: \(n \le 10^3\), \(A_i \le n\)

OA 2 problem 1

**Problem Statement:**  
You are given \(n\) items, each with a weight between \(1.01\) kg and \(2.9\) kg (inclusive). You also have access to an unlimited number of boxes, each of which can hold up to \(3.00\) kg in total.

Your task is to pack all items into boxes such that:  
- The total weight of items in any single box does not exceed \(3.00\) kg.  
- Each item must be placed in exactly one box.  
- You use the **minimum number of boxes** possible.  

---

**Input Constraints:**  
- \(1 \le n \le 1000\)  
- Each item’s weight is a real number in \([1.01,\,2.9]\) kg, with at most two decimal places.  

---

You are given an array of \(n\) positive integers \(a_1, a_2, \dots, a_n\). Your task is to find the number of arrays \(b_1, b_2, \dots, b_n\) that satisfy the following conditions:

1. \(1 \le b_i \le a_i\) for every \(i\).  
2. \(b_i \neq b_{i+1}\) for every \(i\in\{1,2,\dots,n-1\}\).  

Since the number of valid arrays can be very large, output the result **modulo** \(998244353\).

---

**Input Format**  
- The first line contains a single integer \(n\) — the length of the array \(a\) \((1 \le n \le 2\cdot10^5)\).  
- The second line contains \(n\) integers \(a_1, a_2, \dots, a_n\) \((1 \le a_i \le 10^9)\).  

**Output Format**  
Print a single integer — the number of valid arrays \(b\), taken modulo \(998244353\).

Apart from these there was a technical MCQ and aptitude section in both the OAs.

solved 1.1 easily, partially solved 1.2 but could not submit it so it didn't count  
2.1 was very easy  
2.2 was a difficult problem; I was not able to pass even a single hidden test case  

#### Technical Round 1  
It started off with basic introduction about myself, and my hobbies; the interviewers were very friendly and nice, then they asked me to take them through everything in my resume, followed by a discussion on my projects.  
They asked me about MongoDB, JWT, and database-related questions.

Meanwhile another interviewer prepared a problem for me:

**Problem:** Parse a string which consists of lowercase letters `a–z`, digits `0–9`, `[` and `]`. Everything inside square brackets repeats \(x\) times, where \(x\) is the number just before the bracket.

For example:  
\[
\texttt{ab2[bc2[c]]}
\]
would change to  
\[
\texttt{abbcccbccc}
\]

They asked to write pseudocode for my solution.

Another problem followed:

Given the size of an array \(n\) \((n \le 10^5)\) and a number \(m\) \((m \le 9)\), generate the lexicographically largest string which satisfies the following conditions:

- There’s only a single `1`.  
- All `2`’s are placed at least two positions apart.  
- All `m`’s are placed at least two positions apart.  

problem 3.  
You’re given a large sorted array, but you don’t know its size; you have to search for a given number.

problem 4.  
You’re given an array of known size, and you have two threads/processors available at your disposal. How can you increase the speed/efficiency of binary search by making use of those?

problem 5  
Given an array of size \(n\), we know for sure that one of the elements appears more than \(n/2\) times; we have to find that element in linear time and constant space.  
_(Fumbled this one TwT)_

problem 6  
Given a tree and two nodes \(A\) and \(B\), I was asked to find their least common ancestor.

problem 7  
It was a classic knapsack problem, where we had a fixed budget, costs of stocks, and their returns; we needed to maximize the return while staying within the budget.  
_Follow-up:_ There's also a risk percentage associated with each stock.

That was it for the first round, it lasted more than an hour (time flew by).

#### Technical Round 2  
I started with a brief introduction about myself; they asked me if I’ve ever had my solution hacked on Codeforces, or if I’ve ever hacked anyone else's solutions (makes sense, because they're looking for SDET).

problem 1  
You’re given a stream which gives you boxes of size \(x\); you have to group them in groups of 3 such that the difference between the size of the smallest and the largest in the triplet does not exceed the given threshold \(T\).

_Follow-up:_ Now instead of triplets, you have to group them in groups of \(m\).  
_(My solution to the follow-up was correct but I could not provide the most optimal approach for it.)_

problem 2  
The problem boiled down to:

Given two integers \(x\) and \(y\), we have to make \(x = y\). To do that, we can choose some integer \(P\), then repeat the process below until \(P\) is positive:

- Add \(P\) to either \(x\) or \(y\).  
- Decrease \(P\) by 1.

Find the least \(P\) such that upon selection it is possible to make \(x\) and \(y\) equal.

problem 3  
You’re given an array of intervals (bands) of size \(n\). Let \(l_i\) and \(r_i\) denote the left and right end of the \(i\)-th interval, and \(c_i\) denote its cost. There’s also some bonus: suppose there’s a band \(b_i\) such that we have some band greater than \(b_i\) and some band smaller than \(b_i\), then we get \(b_i\) as well. We have to purchase some of the bands such that the bandwidth is maximized and the cost is minimized, and we have to answer it for every prefix of the bands array.

*Then I was asked to figure out some edge case my approach wasn't covering; I managed to find it.*

Then I was asked in depth about my projects, from high-level idea to the APIs. They first asked about high-level ideas of the projects and later went into the technical details as well.

They asked me why I wanted to join as an SDET and what makes me best suited for this role, and asked me if I had a memorable experience when I managed to solve a bug or find a bug in something meaningful.

Followed by some real world scenario problems:

1. Two people are simultaneously booking movie tickets; they select the same seat and book, and both are offered the same seat, which shouldn't be possible. What could be done to prevent this?  
   There can be multiple answers to this, but I went with using a message broker (message queue) to make sure the operations are handled one at a time and there's no duplicate booking.

2. While using social media, it's taking time for your feed to fully load but when someone posts anything it goes through instantly, what could be the cause for this?  
   This was followed by discussion on normalization, CDNs, master–slave architecture, and load balancing.
q
3. While ordering food from an app we manage to go to the payment screen and make the payment but the payment fails and it shows that the restaurant is already closed. What could be the cause for this?  
   This was followed by a small discussion on strong consistency and eventual consistency.

That was all for the second technical interview.
There was no HR round.
