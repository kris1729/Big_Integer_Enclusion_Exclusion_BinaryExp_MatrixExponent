# IMP_Qust_Concept
# Inclusion And Exclution ---> # Important
- |A U B|  ==  A + B - |A ∩ B|
- |A U B U B|  ==  A + B + C - |A ∩ B| - |B ∩ C| - |A ∩ C| + |A ∩ B ∩ C|

> Note -> Negative sign for the Even Size and Possitive sign for the ODD Size

![](./Luv_Question/Enclusion%20Exclusion%20Base%20.png)

- you have to find the number of way , of 3 child group 's names has 
  at vowel is commen

 ### Approch -->
 in which we see the total ans of common A , Common E , Common I, Common O , Common U , and have to remove which count Common A and B both like 
 ... in all of them.

 ### Formula 
 | A ∪ E ∪ I ∪ O ∪ U | == for odd +ve for Even size Negative 


## steps
- input 
- write code for store all the combination of vowel frequency

```cpp
#include <bits/stdc++.h>
using namespace std;

// generate subset

vector<string> subsets(string s)
{
    int sz = (1 << s.size());
    vector<string> ans;
    for (int mask = 0; mask < sz; mask++)
    {
        string subset;
        for (int bit = 0; bit < s.size(); bit++)
        {
            if (mask & (1 << bit))
                subset.push_back(s[bit]);
        }
        if (subset.size())
            ans.push_back(subset);
    }
    return ans;
}
// end subsets
int main()
{
    // input start
    int t;
    cin >> t;
    while (t--)
    {
        int n;
        cin >> n;
        string str[n];
        for (int i = 0; i < n; i++)
            cin >> str[i];

        // input end
        unordered_map<string, int> mp;

        for (int i = 0; i < n; i++)
        {
            // all distinct vowel's store in a set dist_vowel in a string
            set<char> dist_vowel;
            for (auto ch : str[i])
            {
                if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u')
                    dist_vowel.insert(ch);
            }
            // dist_vowel's make a string
            string vowel_str;
            for (auto ch : dist_vowel)
                vowel_str.push_back(ch);

            // take all the subset which is possible by vowel_str

            vector<string> all_subsets = subsets(vowel_str);

            // and store all the subset in the hsh map
            for (auto vowel_subset : all_subsets)
                mp[vowel_subset]++;
        }

        // for (auto x : mp)
        //     cout << x.first << " " << x.second << endl;


  // Main Logic Exclution Exclution for this question
  long long ans =0;
  for(auto &pr :mp){
    if(pr.second<3) continue;
    long long cnt = pr.second;
    // no of ways -- > nC3
    long long ways = ct*(ct-1)(ct-2)/6;
    // if even size odd then +ve i even than -ve
   if(pr.first.size()%2==0)ans -= way;
   else ans += way;
  }

  cout<<ans<<endl;
    }
}
```
# Find the total numberr witch are the less than 500 and divisible by the first 3 prime number
first three prime {2,3,5}
- N(2)--- 500/2 = 250
- N(3) --- 500/3 = 166
- N(5) --- 500 / 5 = 100
- N(2,3) -- 500  / 6 = 83
- N(2,5) --  500 / 15 = 50
- n(3,5) -- 500/ 15 = 33
- N(2,3,5) -- 500/30 = 18

|2 U 3 U 5 | == 250 + 166 + 100 - 83 -50 - 33 +18

# Find the total number witch are the less than 10^18 and divisible by the first 10 prime number

```cpp
int n = 10;
vector<int>{2,3,5,7,11,13,17,19,23,29};

// make all possible sunsets
vector<int>subsets












 # Gcd , O(logN)
```cpp
int Gcd(int a , int b){
    // if(b==0)return a;
    if(a%b==0)return b;
    else return (b,a%b);
}
```
```cpp
__gcd(12,18); // or
gcd(13,52);
``` 


# Binay Exponentiation -

> pow(a,b) return ans in double data type it high chance of error in prision

## Using recrsion O(logb)

```cpp
 int BinaryExpon(int a , int b){
    if(b==1)return 1;
    int res = BinaryExpon(a,b/2);
    if(b%2==1)
    return a*res*res;
    else
    return res*res;
}
```

if Modulo M = 1e9+7

```cpp
int M = 1e9+7;
int BinaryExpon(int a , int b){
    if(b==1)return 1;
    int res = BinaryExpon(a,b/2);
    if(b%2==1)
    return (a*((res*1LL*res)%M))%M;
    else
    return (res*1LL*res)%M;
}
```

## using Itreation

let 5^13 , than we take binary of 13 (1101) and we multiply all the power of 5 where binary is 1 menas === 5^8 _ 5^4 _ 5^1

```cpp
int BinaryExp(int a, int b) {
    int ans = 1;
    while (b) {
        if (b & 1) {
            ans = (ans * a) % M;
        }
        a = (a * a) % M;
        b >>= 1;
    }
    return ans;
}
```

if M = 1e9+7 than

```cpp
int M = 1e9 + 7;
int BinaryExp(int a, int b) {
    int ans = 1;
    while (b) {
        if (b & 1) {
            ans = (ans * 1LL * a) % M;
        }
        a = (a * 1LL * a) % M;
        b >>= 1;
    }
    return ans;
}
```

# Large Exp # IMPORTANT HAI 

in binary Exponent between a and b value is **int** , a&b&M<=10^9

> # IF a<=10^18 or a<=2^1024
>
> in this case , a can be reduce a

# a^b % M = ((a%M)^b)%M

> # if M>=10^18
>
> in this case when we calculate
> a = (a\*a)%M it overflow the long long range
> so that use use the

### **Binary Multiplication**

menas , can't multiply directily so use this ,
in b/w --> 5\*4 means ---> 5 + 5 + 5 + 5

> a\*a = a+a+a+.... a time
> a+a<10^18 so (a+a)%M each step

but we use binary addition for multiplication
in log(n) time complexity
5*13 = 5*(1101) = 5(8+4+0+1)

```cpp

//1. main function for claculate the binary Exp
long long BinaryExp(long long a , long long b , long long M){
    long long ans = 1;
    while(b>0){
    if(b&1){
        ans = BinaryMultiply(ans,a,M);
    }
    a = BinaryMultiply(a,a,M);
    b >>=1;}
    return ans;
}
// 2.function for binary multiply
// but in Log(n) complexity
long long BiaryMultiply(long long a ,long long b , long long M){
    long long ans =0;
    while(b>0){
    if(a&1){
        ans = (ans+a)%M;
    }
    a = (a +a)%M;
    b >>= 1;
    }
    return ans;
}
```

# Large Exp , eural theuram 
> # when b>=10^18 


