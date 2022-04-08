#include <vector>
using namespace std;

vector<vector<int>> threeNumberSum(vector<int> array, int targetSum) {

	vector<vector<int>> ans;
	vector<int> temp;

	if(array.size() < 3)
		return ans;
	
	sort(array.begin(), array.end());
	
	for(int i=0; i<array.size()-2; i++)
	{
		int j=i+1, k=array.size()-1;
		
		if(array[i]+array[j]+array[k] == targetSum)
		{
				temp.push_back(array[i]);
				temp.push_back(array[j]);
				temp.push_back(array[k]);
				ans.push_back(temp);
				temp.clear();
				if(++j == k)
					continue;
		}
		while(array[i]+array[j]+array[k] != targetSum)
		{
			if((array[i]+array[j]+array[k]) > targetSum)
				k--;
			else if((array[i]+array[j]+array[k]) < targetSum)
				j++;
			if(j==k)
				break;
			if(array[i]+array[j]+array[k] == targetSum)
			{
				temp.push_back(array[i]);
				temp.push_back(array[j]);
				temp.push_back(array[k]);
				ans.push_back(temp);
				temp.clear();
				if(++j == k)
					break;
			}
		}
	}
	
  return ans;
}
