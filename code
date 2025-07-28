#include <iostream>
#include <vector>
#include <cmath>
#include <cctype>

using namespace std;


long long convertToDecimal(const string& value, int base) {
    long long result = 0;
    for (char c : value) {
        int digit;
        if (isdigit(c))
            digit = c - '0';  // For '0'-'9'
        else
            digit = tolower(c) - 'a' + 10;  // For 'a'-'z'

        result = result * base + digit;
    }
    return result;
}


long long lagrangeInterpolation(const vector<pair<long long, long long>>& shares, int k) {
    long long secret = 0;

    for (int i = 0; i < k; ++i) {
        long long xi = shares[i].first;
        long long yi = shares[i].second;

        long long numerator = 1;
        long long denominator = 1;

        for (int j = 0; j < k; ++j) {
            if (i == j) continue;
            long long xj = shares[j].first;

            numerator *= -xj;
            denominator *= (xi - xj);
        }

        secret += yi * (numerator / denominator);  
    }

    return secret;
}

int main() {
    //  Test Case 1 
    int threshold1 = 3;
    vector<pair<long long, long long>> shares1 = {
        {1, convertToDecimal("4", 10)},
        {2, convertToDecimal("111", 2)},
        {3, convertToDecimal("12", 10)},
        {6, convertToDecimal("213", 4)}
    };

   
    vector<pair<long long, long long>> input1(shares1.begin(), shares1.begin() + threshold1);


    // Test Case 2 
    int threshold2 = 7;
    vector<pair<long long, long long>> shares2 = {
        {1, convertToDecimal("13444211440455345511", 6)},
        {2, convertToDecimal("aed7015a346d63", 15)},
        {3, convertToDecimal("6aeeb69631c227c", 15)},
        {4, convertToDecimal("e1b5e05623d881f", 16)},
        {5, convertToDecimal("316034514573652620673", 8)},
        {6, convertToDecimal("2122212201122002221120200210011020220200", 3)},
        {7, convertToDecimal("20120221122211000100210021102001201112121", 3)},
        {8, convertToDecimal("20220554335330240002224253", 6)},
        {9, convertToDecimal("45153788322a1255483", 12)},
        {10, convertToDecimal("1101613130313526312514143", 7)}
    };

   
    vector<pair<long long, long long>> input2(shares2.begin(), shares2.begin() + threshold2);


    
    long long secret1 = lagrangeInterpolation(input1, threshold1);
    long long secret2 = lagrangeInterpolation(input2, threshold2);

    cout << "Test Case 1: " << secret1 << endl;
    cout << "Test Case 2: " << secret2 << endl;

    return 0;
}
