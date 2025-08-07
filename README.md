# segment-tree
my first project on github about sth i learned<br><br>

You are gave an array that has N elements: a[1],a[1],...,a[N] and Q requests(N,Q<=1e5)(-1e9<=a[i]<=1e9 with 1<=i<=N).
Having 2 type of request:

+(1)Changing the value of 1 element in an array<br>
+(2)Finding the maximum value in range from l to r (l<=r)

Input: array with N elements, Q, and numbers for each request<br>
Output: answer with each 2nd request<br><br><br>

MY CODE:<br><br>
#include<bits/stdc++.h><br>
using namespace std;<br><br>
const int MN=1e5+5;<br>
const int inf=1e9+7;<br><br>
int N,Q,tl,tr,q_id;<br>
int sign,value;<br>
int arr[MN],st[MN<<2];<br>

void build(int id,int l,int r){<br>
&emsp; if(l==r){<br>
&emsp;&emsp;st[id]=arr[l];<br>
&emsp;&emsp;return;<br>
&emsp;}<br>

&emsp;int mid=l+r>>1;<br>
&emsp;build(id<<1,l,mid); &emsp;build(id<<1|1,mid+1,r);<br>
&emsp;st[id]=max(st[id<<1],st[id<<1|1]);<br>;
}<br>

void update(int id,int l,int r,int tar_id,int V){<br>
&emsp;if(id<l ||id>r) return;<br>

&emsp; if(id==l){<br>
&emsp;&emsp; st[id]=V;<br>
&emsp;&emsp; return;<br>
&emsp;}<br>

&emsp;int mid=l+r>>1;<br>
&emsp;update(id<<1,l,mid,tar_id,value); &emsp;update(id<<1|1,mid+1,r,tar_id,value);<br>
&emsp;st[id]=max(st[id<<1],st[id<<1|1]);<br>
}<br>

int main(){<br>
  &emsp;cin>>N;<br>
  &emsp;for(int i=1;i<=N;++i) cin>>arr[i];<br><br>

  &emsp;build(1,1,N);<br>
  &emsp;cin>>Q;<br>
  &emsp;while(Q--){<br>
  &emsp;&emsp;cin>>sign;<br>
  &emsp;&emsp;if(sign==1){<br>
  &emsp;&emsp;&emsp;cin>>q_id>>value;<br>
  &emsp;&emsp;&emsp;update(1,1,N,q_id,value);<br>
  &emsp;&emsp;}<br>
  &emsp;}<br>
}
