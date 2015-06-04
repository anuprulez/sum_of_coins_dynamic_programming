//sum_of_coins_dynamic_programming
//Dynamic Programming



#include <stdlib.h>
#include <iostream>
#include <limits.h>

using namespace std;

int find_dp_min_coins(int [], int, int);

int main(){
	
	int coin_values[3] = {1,3,5};
	int num_coins = 3;
	int sum = 11;
	int result = find_dp_min_coins(coin_values, num_coins, sum);
	std::cout << "The number of coins: " << result << std::endl;
	return 0;
}

int find_dp_min_coins(int value[], int num, int sum){
	int mins[sum+1];
	int i,j;
	for(i = 1; i <= sum; i++){
		mins[i] = SHRT_MAX;
	}
	mins[0] = 0;

	for(i = 1; i <= sum; i++){
		for(j = 1; j <= num; j++){
			if(value[j] <=i && ((mins[i - value[j]] + 1) < mins[i])){
				mins[i] = mins[i-value[j]] + 1;	
				std::cout << "i: " << i << " mins[i] " << mins[i] << std::endl;	
			}
		}
	}
	return mins[sum];
}
