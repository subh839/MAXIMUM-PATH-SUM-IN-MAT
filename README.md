# MAXIMUM-PATH-SUM-IN-MATRIX

 int t[501][501];
    int maxSumPath(int x,int y,int N,vector<vector<int>> &m){
        if(x == N or y<0 or y == N){
            return 0;
        }
        if(x == N-1){
            return m[x][y];
        }
        if(t[x][y] != -1){
            return t[x][y];
        }
        t[x][y] = m[x][y] + max({ maxSumPath(x+1,y,N,m) , maxSumPath(x+1,y-1,N,m) , maxSumPath(x+1,y+1,N,m) });
        return t[x][y];
    }

    int maximumPath(int N, vector<vector<int>> Matrix)
    {   
        memset(t , -1 , sizeof(t));
        int ans = INT_MIN;
        for(int i=0;i<N;i++){
            ans = max(ans , maxSumPath(0,i,N,Matrix) );
        }
        return ans;
    }
    };
