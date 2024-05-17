# asqre-zoho_Coding-round-answer

// Question -1
#include <bits/stdc++.h>
using namespace std;


int findMin(vector<int> &nums, int n){
    unordered_map<int, int> m;
    int ans=INT_MAX;

    for(int i=0;i<n;i++){
        if(m.find(nums[i])!=m.end()){
            int dist=i-m[nums[i]];
            ans=min(ans, dist);
        }
        m[nums[i]]=i;
    }

    if(ans==INT_MAX){
        return -1;
    }

    return ans;
}



int main(){
    #ifndef ONLINE_JUDGE
        freopen("input.txt", "r", stdin);
        freopen("output.txt", "w", stdout);
    #endif

    int n;
    cin>>n;
    vector<int> nums(n);
    for(int i=0;i<n;i++){
        int a;
        cin>>a;
        nums[i]=a;
    }
    

    cout<<findMin(nums, n)<<endl;

    return 0;
}
*/

/*
Ex-1
8
1 2 10 3 4 11 1 7 

Ex-2
6
7 1 3 4 1 7

Ex-3
5
1 2 3 4 10
*/

// ===========================================

/*
// Question - 2

#include <bits/stdc++.h>
using namespace std;

int findPairs(vector<int> &nums){
    int ans=0;
    unordered_map<int, int> m;

    for(auto i : nums){
        m[i]++;
    }

    for(auto it : m){
        int freq=it.second;
        int pairs=freq/2;
        ans+=pairs;
    }
    return ans;
}


int main(){
    #ifndef ONLINE_JUDGE
        freopen("input.txt", "r", stdin);
        freopen("output.txt", "w", stdout);
    #endif

    int n;
    cin>>n;
    vector<int> nums(n);
    for(int i=0;i<n;i++){
        int a;
        cin>>a;
        nums[i]=a;
    }

    cout<<findPairs(nums)<<endl;

    return 0;
}
*/

/*
Ex-1
9
10 20 20 10 10 30 50 10 20
*/

//============================================

// Question - 3
#include <bits/stdc++.h>
using namespace std;


int gcd(int a, int b) {
    if (b == 0) return a;
    return gcd(b, a % b);
}

void printMixedFraction(double n) {
    int integerPart = (int)n;
    double fractionalPart = n - integerPart;

    int den = 1;

    while (abs(fractionalPart - (int)(fractionalPart)) > 1e-9) {
        fractionalPart *= 10;
        den *= 10;
    }

    cout<<"not infinite loop"<<endl;
    int commonDivisor = gcd((int)(fractionalPart), den);

    int num = (int)(fractionalPart) / commonDivisor;
    den /= commonDivisor;

    cout << "Mixed Fraction: " << integerPart << " " << num << "/" << den << endl;
}

int main(){
    #ifndef ONLINE_JUDGE
        freopen("input.txt", "r", stdin);
        freopen("output.txt", "w", stdout);
    #endif

    double n;
    cin>>n;

    printMixedFraction(n);

    return 0;
}


/*
Ex-1
2.5

Ex-2
6.25
*/
//=============================================
/*
// question 4

#include <bits/stdc++.h>
using namespace std;


int findA(string s, int n){
    int len=s.size();
    int cntA=0;

    for(auto c: s){
        if(c=='a'){
            cntA++;
        }
    }  

    // last repeated
    int rem=n%len;
    int remA=0;
    for(int i=0;i<rem;i++){
        if(s[i]=='a'){
            remA++;
        }
    }

    int ans = (cntA*(n/len)) + remA;

    return ans;
}


int main(){
    #ifndef ONLINE_JUDGE
        freopen("input.txt", "r", stdin);
        freopen("output.txt", "w", stdout);
    #endif

    string s;
    cin>>s;

    int n;
    cin>>n;

    cout<<findA(s, n)<<endl;

    return 0;
}

/*
Ex-1
aba
10

Ex-2
abcac
10

*/

// ==================================
/*
// Question 5

#include <bits/stdc++.h>
using namespace std;

string isSubsequence(string A, string B){
    stack<char> st;

    for(auto ch: A){
        st.push(ch);
    }

    int i=B.size()-1;
    while(!st.empty() && i>=0){
        if(st.top()==B[i]){
            st.pop();
        }
        i--;
    }

    if(st.empty()){
        return "YES";
    }

    return "NO";
}


int main(){
    #ifndef ONLINE_JUDGE
        freopen("input.txt", "r", stdin);
        freopen("output.txt", "w", stdout);
    #endif

    string A;
    cin>>A;

    string B;
    cin>>B;

    cout<<isSubsequence(A, B)<<endl;

    return 0;
}

*/
/*
Ex-1
Set 
Sangeet

Ex-2
Zoho
India

Ex-3
Set
Step
*/

//=====================================
/*

// Question - 6
#include<bits/stdc++.h>
using namespace std;
// inorder traversal is also called heap sort
void inorderTraversal(vector<int>& nums, int n) {
    priority_queue<int, vector<int>, greater<int>> pq;

    for(auto i: nums){
        pq.push(i);
    }

    while(!pq.empty()){
        cout<<pq.top()<<", ";
        pq.pop();
    }

    cout<<endl;
}

int main(){
    #ifndef ONLINE_JUDGE
        freopen("input.txt", "r", stdin);
        freopen("output.txt", "w", stdout);
    #endif

    int n;
    cin>>n;
    vector<int> nums(n);
    for(int i=0;i<n;i++){
        int a;
        cin>>a;
        nums[i]=a;
    }

    cout << "Inorder Traversal: ";
    inorderTraversal(nums, n);

    return 0;
}

*/
/*
Ex-1
6
4 2 5 1 3 0
*/

//========================================================
/*
// question - 7

#include <bits/stdc++.h>
using namespace std;

int minHeight(int h1, int h2, int h3){
    int ans=min(h1, h2);
    return min(ans, h3);
}

int findMinHeight(vector<int> &s1, vector<int> &s2, vector<int> &s3, int n1, int n2, int n3){
    //find height of each cylinder
    int h1=0, h2=0, h3=0;

    // store each cylinder in their respective stack
    stack<int> stack1;
    stack<int> stack2;
    stack<int> stack3;

    for(int i=n1-1;i>=0;i--){
        h1+=s1[i];
        stack1.push(s1[i]);
    }

    for(int i=n2-1;i>=0;i--){
        h2+=s2[i];
        stack2.push(s2[i]);
    }

    for(int i=n3-1;i>=0;i--){
        h3+=s3[i];
        stack3.push(s3[i]);
    }

    int maxHeight=minHeight(h1, h2, h3);

    while((!stack1.empty() && !stack2.empty() && !stack3.empty()) && (h1!=h2 || h2!=h3)){
        if(h1>maxHeight){
            h1-=stack1.top();
            stack1.pop();
            maxHeight=minHeight(h1, h2, h3);
        }
        if(h2>maxHeight){
            h2-=stack2.top();
            stack1.pop();
            maxHeight=minHeight(h1, h2, h3);
        }
        if(h3>maxHeight){
            h3-=stack3.top();
            stack3.pop();
            maxHeight=minHeight(h1, h2, h3);
        }
    }

    return maxHeight;
}


void printVector(vector<int> &nums){
    for(auto i: nums){
        cout<<i<<", ";
    }
    cout<<endl;
}

int main(){
    #ifndef ONLINE_JUDGE
        freopen("input.txt", "r", stdin);
        freopen("output.txt", "w", stdout);
    #endif

    int n1, n2, n3;
    cin>>n1>>n2>>n3;

    vector<int> s1(n1);
    for(int i=0;i<n1;i++){
        int a;
        cin>>a;
        s1[i]=a;
    }

    vector<int> s2(n2);
    for(int i=0;i<n2;i++){
        int a;
        cin>>a;
        s2[i]=a;
    }

    vector<int> s3(n3);
    for(int i=0;i<n3;i++){
        int a;
        cin>>a;
        s3[i]=a;
    }

    // printVector(s1);
    // printVector(s2);
    // printVector(s3);

    cout<<findMinHeight(s1, s2, s3, n1, n2, n3)<<endl;

    return 0;
}
*/
/*
//Ex
5 3 4
3 2 1 1 1
4 3 2
1 1 4 1
*/

//======================================================

