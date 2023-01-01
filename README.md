# gfg-Count-even-length
Problem of the day

Example:

Input: n = 2
Output: 6
Explanation: There are 6 sequences of length 
2*n, the sequences are 0101, 0110, 1010, 1001, 
0000 and 1111.

class Solution{
	public:
	int mod = 1e9+7;
	long long inv(long long int i){
	    if(i == 1) return 1;
	    return (mod - ((mod/i)* inv(mod%i))%mod + mod)%mod;
	}
	
	int compute_value(int n)
	{
	    // Code here
	    long long int ans = 1, nCr = 1;
	    for(int r = 1; r<=n; r++){
	        nCr = (((nCr*(n+1-r))%mod)*inv(r))%mod;
	        ans = (ans + (nCr*nCr)%mod)%mod;
	    }
	    return ans%mod;
	}
};
