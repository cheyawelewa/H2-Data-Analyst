# H2-Data-Analyst


To find the consecutive months with the highest sales, I will:
Look for the pair (or sequence) of consecutive months where the sum of their sales is the highest.
For each pair of consecutive months, calculate the sum of their sales.
Keep track of the maximum sum found and the corresponding months.
At the end, report the months with the highest consecutive sales sum.
This approach can be generalized to any dataset of monthly sales, not just the one provided.

#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
int main() {  
    // Example
    vector<string> months = {"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"};  
    vector<int> sales = {100, 113, 110, 85, 81, 101, 94, 106, 105, 102, 86, 63};  
  
    int n = sales.size();  
    if (n < 2) {  
        cout << "Not enough data for consecutive months." << endl;  
        return 0;  
    }  
  
    int max_sum = sales[0] + sales[1];  
    int start_index = 0;  
  
    for (int i = 1; i < n - 1; ++i) {  
        int current_sum = sales[i] + sales[i + 1];  
        if (current_sum > max_sum) {  
            max_sum = current_sum;  
            start_index = i;  
        }  
    }  
  
    cout << "Consecutive months with highest sales: " << months[start_index] << " and " << months[start_index + 1] << endl;  
    cout << "Total sales: " << max_sum << " million USD" << endl;  
  
    return 0;  
}  



Input: months[], sales[]  
max_sum = sales[0] + sales[1]  
start_index = 0  
  
For i from 1 to length(sales) - 2:  
    current_sum = sales[i] + sales[i+1]  
    If current_sum > max_sum:  
        max_sum = current_sum  
        start_index = i  
  


	•	Only Finds Pairs: The solution only finds the highest sum for two consecutive months. 
	•	Ignores Non-Consecutive Highs: It does not consider non-consecutive months with high sales, which might also be useful for campaign planning.
	•	No Tie Handling: If there are multiple pairs with the same maximum sum, only the first is reported.
