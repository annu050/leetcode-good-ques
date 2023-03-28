/*
APPROACH 1
this brute force approach is good but TLE happens as take o(n^3)time complexity

class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
//sorting is done so that if we get repeated array then the values will also be in same order then set will not take them twice
        sort(nums.begin(), nums.end());
        set<vector<int>> sets;
        vector<vector<int>> ans;
        for(int i=0;i<nums.size()-2;i++){
            for(int j=i+1;j<nums.size()-1;j++){
                for(int k=j+1;k<nums.size();k++){
                    if(nums[i]+nums[j]+nums[k]==0){
                        sets.insert({nums[i],nums[j],nums[k]});
                    }
                }
            }
        }
        for(auto i:sets){
            ans.push_back(i);
        }
        return ans;
    }
};
*/

//approach 2
class Solution{
public:
    vector<vector<int>> threeSum(vector<int>& nums){
        int high,low;
        int n=nums.size();
        sort(nums.begin(),nums.end());
        set<vector<int>> set;
        vector<vector<int>> ans;
        for(int i=0;i<n-2;i++){
//here we have fixed our i and after using all the combinations with other 2 then we increment i and then again make combination
            low=i+1;
            high=n-1;
            while(low<high){
                if(nums[i]+nums[low]+nums[high]<0){
                    low++;
                }
                else if(nums[i]+nums[low]+nums[high]>0){
                    high--;
                }
                else{
                    set.insert({nums[i],nums[low],nums[high]});
                    low++;
                    high--;
                }
            }
        }
        for(auto i: set){
            ans.push_back(i);
        }
        return ans;

    }
};




