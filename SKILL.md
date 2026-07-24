---
name: cpp-style
description: C++ coding style rules of algorithm contestant zbc, distilled from several hundred contest solutions. Whenever writing, modifying, or completing C++ code for the user, especially in algorithm contests or problem-solving contexts such as luogu, lanqiao, leetcode, codeforces, atcoder, nowcoder, and hdoj, every rule below MUST be applied without omission. The rules specify every space, comma, and line break so that any model produces exactly the same code style. TRIGGER: write code, solve problems, algorithms, problem solving, c++, cpp, contests, oj, luogu, leetcode, codeforces, atcoder, nowcoder, LuoGu, Lanqiao, solutions, AC, graph theory, DP, dfs, bfs, binary search, greedy.
---

# User C++ Coding Style Rules

> **These rules are strict: every rule must be followed. There is no "it depends" exception.**

---

## 1. Framework Conventions (Copy Exactly)

### 1.1 Simple solutions (syntax problem template, keep everything minimal)

```cpp
#include<bits/stdc++.h>
using namespace std;
int main() {
  <body>
  return 0;
}
```

### 1.2 Standard contest code (most common in algorithm contests, use by default, with i64 and sync disabled)

```cpp
#include<bits/stdc++.h>
using namespace std;
using i64=int64_t;
int main() {
  cin.tie(0)->sync_with_stdio(0);
  <body>
  return 0;
}
```

### 1.3 Define moduli

```cpp
constexpr int mod=1e9+7;
constexpr int64_t MOD=998244353;
```

### 1.4 Multiple test cases

```cpp
int T;
cin>>T;
while (T--) {
  <body>
}
```

### 1.5 LeetCode (keep the original problem signature, add headers and the namespace)

```cpp
/*
 * @lc app=leetcode.cn id=<id> lang=cpp
 * [<id>] <title>
 */
#include<bits/stdc++.h>
using namespace std;
//@lc code=start
class Solution {
public:
  <returnType> <methodName>(<params>) {
    <body>
  }
};
//@lc code=end
```

---

## 2. Spacing Rules

### 2.1 One space between keywords and parentheses

```cpp
for (int i=0;i<n;i++)
while (l<=r)
if (cond)
switch (x)
```

### 2.2 No space between a function/method name and its parentheses

```cpp
int main() {
dfs(dfs,x,y);
q.emplace(i,j);
```

### 2.3 No spaces around binary operators (assignment/arithmetic/comparison/shift)

```cpp
int mid=l+(r-l)/2;
ans+=r-l+1;
a[i]=b[i-1]+1;
int l=0,r=n-1;
x=x*2+1;
```

### 2.4 No spaces around stream operators `>>` and `<<`

```cpp
cin>>n>>m>>k;
cout<<ans<<'\n';
cout<<a<<" "<<b<<'\n';
```

### 2.5 Spaces on both sides of logical operators `&&` and `||`

```cpp
if (nx<0 || nx>=n || ny<0 || ny>=m) continue;
if (x>=1 && x<=n && !visited[x])
```

### 2.6 No spaces around the ternary operator `? :`

```cpp
int lower=comb.empty()? 0:comb.back()+1;
cout<<(x%2? "even":"odd")<<'\n';
return nums[lo]==target? lo:-1;
```

### 2.7 No space after commas

```cpp
int n,m,k;
auto [x,y]=q.front();
vector<pair<int,int>> dir={{0,1},{0,-1},{1,0},{-1,0}};
```

### 2.8 No spaces around the colon in range-for loops

```cpp
for (auto &x:a) cin>>x;
for (auto &[k,v]:mp)
```

### 2.9 No spaces after semicolons in for headers

```cpp
for (int i=0;i<n;i++)
for (int i=n-1;i>=0;i--)
for (int l=0,r=n-1;l<=r;)
```

### 2.10 No spaces after commas in template arguments

```cpp
vector<pair<int,int>>
array<int,2>
function<void(int,int)>
```

### 2.11 No spaces after commas in member initializer lists

```cpp
Dijkstra(int n):g(n+1),vis(n+1) {}
```

---

## 3. Line Breaks and Braces

### 3.1 Opening braces on the same line (K&R)

```cpp
int main() {
void dfs(int x) {
if (cond) {
} else if (cond2) {
} else {
class Solution {
struct drop {
auto dfs=[&](auto &self,int x)->void {
```

### 3.2 Do not add braces for single-statement if/else/loops

```cpp
if (visited[to]) continue;
if (!cond) return false;
else l=mid+1;
for (int i=0;i<n;i++) cin>>a[i];
//Short statements may stay on one line.
if (x<=0 || y<=0 || z<=0) return 1;
if (l>=r) return;
```

### 3.3 Keep dense statements together inside functions; add a blank line only between major logical blocks

```cpp
int main() {
  int n,m;
  cin>>n>>m;
  vector<int> a(n);
  for (auto &x:a) cin>>x;
  auto match=[&](int mid) { ... };
  int l=0,r=INT_MAX;
  while (l<=r) { ... }
  cout<<l<<'\n';
  return 0;
}
```

---

## 4. Naming Rules

### 4.1 Variables use camelCase

```cpp
sufMax,preMin,maxDel,coinGot
xorSum,colSum,bPreMin,pSufMax
opNum,slotCnt,ballUsed
landTimes,jumpMax,usedIdx
lowPrice,maxGot,isPrime,canAfford
```

**Exception: a short 1-2 character marker after `_` is acceptable** (factory lambda / variant distinction / draft comparison)

```cpp
auto make_C=[&](int max_n) { ... };       //Lambda returning combinations from a factory.
auto make_C_other=...;                    //A variant of the same kind.
auto power_dp=...;                        //A variant implementation.
auto ballFate_subSeq=...;                 //A subproblem variant.
auto slotCall_comb=...;                   //Another viewpoint.
```

### 4.2 Short variable names (one or two lowercase letters)

```cpp
n,m,k,T,q     //Problem input.
l,r,lo,hi,mid //Binary search / two pointers.
x,y,z         //Coordinates.
u,v,w         //Graph theory.
i,j           //Loops.
p,b,c,d       //Temporary values.
a,s,t         //Arrays / strings.
```

### 4.3 Fixed vocabulary (variants are not allowed)

| Use | Fixed | Forbidden |
|------|------|------|
| Answer | `ans` | answer/result |
| Temporary value | `tmp` | temp/t |
| Count | `cnt` | count/c |
| Sum | `sum` | total/s |
| Index | `idx`/`pos` | index |
| Iterator | `iter` | it |
| Difference | `dlt` | delta/diff |
| Range | `rng` | - |
| Sorted result | `srt` | - |
| Prefix/suffix | `pre`/`suf` | prefix/suffix |
| Amount | `amo` | amount/num |

### 4.4 DP-related names

```cpp
dp,memo //DP table / memoization.
cur,pre //Rolling array: cur=dp[i&1],pre=dp[~i&1].
cur,nxt //Forward DP: cur=dp[i&1],nxt=dp[~i&1].
```

### 4.5 Common function/lambda names

```cpp
match,check,update,calc,traceback,dfs
isFind,isEnough,isAfford,getSubLIS,canAfford
insert,bitOp,heapify
```

### 4.6 Struct/type aliases use lowercase

```cpp
struct drop {};
using i64=int64_t;
using pii=pair<int,int>;
using dim=array<int64_t,3>;
```

---

## 5. Type Usage

### 5.1 Default to `int`; use `int64_t`/`i64` when overflow is possible

```cpp
int ans=0;
int64_t sum=0;
i64 base=0,dlt=0;
vector<int64_t> num(n);
```

### 5.2 Explicitly cast before multiplication

```cpp
ans+=(int64_t)(c[i]-(l-1))*p[i];
```

### 5.3 Cast to `(int)` before using `.size()`/`.length()` in arithmetic

```cpp
for (int i=0;i<(int)comb.length();i++)
int len=(int)prices.size()-1;
```

### 5.4 Use `vector<char>` for visited (do not use `vector<bool>`)

```cpp
vector<char> vis(n,0);
vector<int> visited(n+1);
```

### 5.5 When guarding against overflow from infinite values, use `INT_MIN/2` or `LLONG_MIN/2` for negative infinity, and `INT_MAX/2` or `LLONG_MAX/2` for positive infinity

```cpp
vector<vector<int>> dp(n+1,vector<int>(m+1,INT_MIN/2));
```

---

## 6. Containers and Construction

### 6.1 Prefer concise CTAD

```cpp
auto maze=vector(n,vector<int>(m));
auto memo=vector(21,vector(21,vector<int>(21,-1)));
auto dp=vector(2,vector(n,vector<int>(k+1)));
```

### 6.2 Prefer `emplace`/`emplace_back`

```cpp
q.emplace(i,j);
cur.emplace_back(other+add);
dp.push_back(x); //Use push when C++ requires it.
```

### 6.3 Use range-for references for input

```cpp
vector<int> a(n);
for (auto &x:a) cin>>x;
```

### 6.4 Structured bindings

```cpp
auto [x,y]=q.front();
auto [d,u]=q.top();
for (auto &[dx,dy]:dir)
```

---

## 7. Common Algorithm Templates (Copy Exactly)

### 7.1 Binary search on the answer (closed interval, answer ends up in `l`)

```cpp
auto match=[&](int mid)->bool {
  return cond;
};
int l=0,r=INT_MAX;
while (l<=r) {
  int mid=l+(r-l)/2;
  if (match(mid)) r=mid-1;
  else l=mid+1;
}
cout<<l<<'\n';
```

### 7.2 Recursive lambda (pass `self` by default; use `function<>` in C++11)

```cpp
auto dfs=[&](auto &self,int x)->void {
  for (auto &[dx,dy]:dir) {
    int nx=x+dx,ny=y+dy;
    if (nx<0 || nx>=n || ny<0 || ny>=m) continue;
    self(self,nx,ny);
  }
};
dfs(dfs,sx);

function<void(int,int)> dfs=[&](int x,int y) {
  maze[x][y]='*';
  for (auto &d:dir) {
    int nx=x+d[0],ny=y+d[1];
    if (nx<0 || nx>=n || ny<0 || ny>=n || maze[nx][ny]!='0') continue;
    dfs(nx,ny);
  }
};
dfs(0,i);
```

### 7.3 Backtracking skeleton

```cpp
comb.push_back(x);
self(self);
comb.pop_back();

slotUsed[i]=1;
slotCnt++;
self(self);
slotCnt--;
slotUsed[i]=0;
```

### 7.4 LIS template

```cpp
vector<int> dp;
for (auto &x:a) {
  auto iter=lower_bound(dp.begin(),dp.end(),x);
  if (iter==dp.end()) dp.push_back(x);
  else *iter=x;
}
```

### 7.5 Rolling array

```cpp
for (int i=1;i<n;i++) {
  auto &cur=dp[i&1],&pre=dp[~i&1];
}
cout<<dp[~n&1][...]<<'\n';
```

### 7.6 Prefix sum with `partial_sum`

```cpp
partial_sum(num.begin(),num.end(),num.begin());
```

### 7.7 Two-pointer sliding window

```cpp
for (int l=0,r=0;l<=r;) {
  if (r>=n) {
    //update/remove
  } else if (/*The window can expand.*/) {
    //insert
  } else {
    //update
    //remove
  }
}
```

### 7.8 IIFE lambda

```cpp
cout<<[&]() {
  return ans;
} ()<<'\n';

if ([&]() {
  for (int i=0;i<k;i++) if (cnt[i]&1) return false;
  return true;
} ()) { ... }
```

### 7.9 Zero-overhead character mapping

```cpp
cnt[c-'A']++;               //Uppercase -> 0..25.
pos[s[i]-'a']++;            //Lowercase frequency.
int val=s[i]-'a'+1;         // -> 1..26.
int lower=sub.back()-'0'+1; //Digit character -> numeric value.
char elem='A'+idx;          //Index -> uppercase.
cout<<char('a'+i);          //Index -> lowercase.
perm[i]='0'+ball;           //Number -> digit character.
```

### 7.10 Direction arrays

```cpp
vector<pair<int,int>> dir={{0,1},{0,-1},{1,0},{-1,0}};
vector<array<int,2>> dir={{-1,-1},{-1,0},{-1,1},{0,-1},{0,1},{1,-1},{1,0},{1,1}};
```

---

## 8. Comment Rules

### 8.1 Comment format

Do not add a space after `//` or `/*`. Do not add unnecessary spaces inside comments, but spaces between digits and letters are required.

```cpp
//Constant-factor optimization saves the day; this problem is sensitive to constants.
//Mind the explicit cast!
int64_t ans=0; //The problem setter is cruel.
if (dist[i][j]%2==1/*To exclude the -1 case.*/) cout<<'#';
if (nx<0 || nx>=h || ny<0 || ny>=w || dist[nx][ny]!=-1/*visited*/) continue;
```

### 8.2 Comment placement

Short code line + short comment -> same line. If either is long enough to look crowded, put the comment on the line above.

```cpp
//Short code + short comment -> same line.
cin.tie(0)->sync_with_stdio(0); //Constant-factor optimization.
int64_t ans=0; //The problem setter is cruel.
ranges::sort(num); //ranges makes STL code more concise.

//Long comment goes above the code.
//Using reverse iterators and custom lambda comparison logic.
partial_sum(sufMax.rbegin(),sufMax.rend(),sufMax.rbegin(),...);
//Entering the loop means an A character remains, so the previous stage needs another state transition.
(dp[j][k][0]+=dp[j][k][1])%=mod;

```

### 8.3 Comment content

Use English. Explain what something is only when it is difficult to understand or rarely used; otherwise explain why it is needed or point out a pitfall. Do not write comments with personal emotions like some user comments do.

```cpp

//Using reverse iterators and custom lambda comparison logic.
partial_sum(sufMax.rbegin(),sufMax.rend(),sufMax.rbegin(),...);

//Entering the loop means an A character remains, so the previous stage needs another state transition.
(dp[j][k][0]+=dp[j][k][1])%=mod;

//Constant-factor optimization saves the day; this problem is sensitive to constants.
//Necessary pruning; without this line the solution will TLE.
//Guard against out-of-bounds access.
ans+=(int64_t)(c[i]-(l-1))*p[i]; //Mind the explicit cast!
```

Leave one space before `//` by default. The exact number of spaces is not enforced; the comment only needs to look visually separate.

### 8.4 One-line algorithm summary comment at the top

Place it after `using namespace std;` and immediately before `int main()`, on its own line. Omit it for very simple problems and do not add extra blank lines.

```cpp
//Simple greedy + binary search on the answer.
//Classic prefix sum with flexible use.
//Greedy + linear basis.
//Insight-based BFS; init cases are difficult to derive.
//Recursive simulation.
//State compression.
```

### 8.5 Replaced old solution: keep the entire `/* ... */` block

```cpp
//TLE DP solution.
/*
int main() {
  ...
}
*/
```

Put the old solution **after the correct solution**, with a performance note such as `//Weak data happens to AC` or `//TLE DP solution`.

### 8.6 Forbidden comment styles

- Do not use comments to explain "what the code does" when the code already says it, unless the logic is very hidden.
- Do not write Chinese comments. All comments, including "TODO" and "FIXME", must be in English.

---

## 9. Forbidden Items (Guardrail Checklist)

1. **Do not use `endl`** - always use `'\n'`.
2. **Do not use Tab indentation** - always use 2 spaces.
3. **Do not use `#include <bits/stdc++.h>` with a space** - always use `#include<bits/stdc++.h>`.
4. **Use `emplace`/`emplace_back` instead of `push({})` when possible** - but use `dp.push_back(x)` normally when C++ requires push.
5. **Do not use `vector<bool>`** - use `vector<char>` or `vector<int>` for visited.
6. **Do not use Allman braces** (braces on their own lines) - always use K&R.
7. **Do not use all-snake_case variable names** - always use camelCase; a short 1-2 character marker after `_` is the only exception, such as `make_C` or `power_dp`.
8. **Do not use `static_cast<>()`** - use C-style `(int)` casts.
9. **Do not use `#ifndef DEBUG / #define debug / #endif`** - those are added manually by the user while debugging.
10. **Do not use `int l = 0, r = n - 1;` with spaces** - always use `int l=0,r=n-1;`.
11. **Do not use `for (int i = 0; i < n; i++)` with spaces in the for header** - always use `for (int i=0;i<n;i++)`.
12. **Do not use `cin >> n >> m;` with spaces around stream operators** - always use `cin>>n>>m;`.
13. **Do not use separate headers such as `#include <iostream>` in contest code** - always use `#include<bits/stdc++.h>`.
14. **Do not omit `return 0;` from `main`** - it must be added at the end.
15. **Do not use blank lines.**

---

## 10. Quick Self-Check

- [ ] Indentation is always 2 spaces, with no Tab.
- [ ] `#include<bits/stdc++.h>` has no space.
- [ ] There is a space after keywords and before `(` (`if`/`for`/`while`/`switch`).
- [ ] There is no space before `(` in function calls.
- [ ] Binary operators (`=` `+` `-` `*` `/` `%` `<<` `>>` `<` `>` `==` `!=`) have no spaces on either side.
- [ ] `&&` and `||` have spaces on both sides.
- [ ] `? :` has no spaces on either side.
- [ ] There are no spaces after commas, including in template arguments and initializer lists.
- [ ] There are no spaces after semicolons in for headers.
- [ ] Stream operators `>>` and `<<` have no spaces.
- [ ] Range-for colons have no spaces on either side.
- [ ] Use `'\n'`, not `endl`, for line breaks.
- [ ] Use K&R braces; the opening brace stays on the same line.
- [ ] Do not add braces around single statements.
- [ ] `main` ends with `return 0;`.
- [ ] There is no `#ifndef DEBUG` debug block.
- [ ] Use `(int)` casts, not `static_cast<>()`.
- [ ] Use `vector<char>` for visited, not `vector<bool>`.
- [ ] Prefer `emplace`/`emplace_back`.
- [ ] Put an algorithm summary comment before `int main()`; omit it for simple problems.
- [ ] There are no extra blank lines.
