# Queens_Problem
Chess Queens Problem solved using recursion/back-tracking. the solution prints the position of each of the queen and finally prints the number of found solutions.
#include<iostream>
#include<vector>
using namespace std;

vector<int> column, rightD, leftD , row;
int n , equi , solutions;
void printSol()
{
	for (int i = 0; i < row.size(); ++i){
		cout << "( " << i << " , " << row[i] << " )" << " ";
	}
	cout << endl;
	
	solutions++;
}
void placeQ(int r)
{
	for (int i = 0; i < n; ++i)
	{
		if (column[i] == 0 && leftD[r + i] == 0 && rightD[r - i + equi] == 0) {
			row[r] = i;
			column[i] = 1;
			leftD[r + i] = 1;
			rightD[r - i + equi] = 1;

			if (r < n - 1)
				placeQ(r + 1);
			else
			{
				printSol();
			}
			column[i] = 0;
			leftD[r + i] = 0;
			rightD[r - i + equi] = 0;
		}
	}
}
int main()
{
	cin >> n;
	column.resize(n);
	rightD.resize(2 * n - 1);
	leftD.resize(2 * n - 1);
	row.resize(n);
	equi = n - 1;
	fill(column.begin(), column.end(), 0);
	fill(rightD.begin(), rightD.end(), 0);
	fill(leftD.begin(), leftD.end(), 0);
	placeQ(0);
	cout << solutions << endl;
	return 0;
}
