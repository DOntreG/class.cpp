# class.cpp
/* Programmer: D'Ontre Gilliard
   Date Written: 2/4/2021
   Purpose:  A program that uses this method to calculate a contestant’s score
   Description: A particular talent competition has five judges,
				each of whom awards a score between 0 and 10 to each performer.
*/
#include <iostream>
#include <iomanip>
using namespace std;

void getJudgeData(double&);
double calScore(double, double, double, double, double);
int findHighest(double, double, double, double, double);
int findLowest(double, double, double, double, double);

int main()
{
	double Score1, Score2, Score3, Score4, Score5;

	cout << "\nThis program calculates a performer final score. \n"
		<< "--------------------------------------------------\n\n";


	getJudgeData(Score1);
	getJudgeData(Score2);
	getJudgeData(Score3);
	getJudgeData(Score4);
	getJudgeData(Score5);

	cout << "\nThe Contestant score is: ";

	cout << calScore(Score1, Score2, Score3, Score4, Score5);

	cout << endl;

	return 0;

}


void getJudgeData(double& Score)
{

	do
	{
		cout << "Enter a Judge's score: ";
		cin >> Score;
		
		if (Score < 0 || Score > 10)

		{
			cout << "\nError! Invalid Score.\n"
				<< "Judge's Score must be greater than 0 and less than 10.\n";

		}

	} while (Score < 0 || Score > 10);

}

// Calculations
double calScore(double Score1, double Score2, double Score3, double Score4, double Score5)

{

	int High,
		Low;
	double Avg;

	High = findHighest(Score1, Score2, Score3, Score4, Score5);
	Low = findLowest(Score1, Score2, Score3, Score4, Score5);

	if (High == static_cast<int>(Score1))
	{
			if (Low == static_cast<int>(Score2))
				Avg = (Score3 + Score4 + Score5) / 3;
			else if (Low == static_cast<int>(Score3))
				Avg = (Score2 + Score4 + Score5) / 3;
			else if (Low == static_cast<int>(Score4))
				Avg = (Score3 + Score2 + Score5) / 3;
			else
				Avg = (Score2 + Score3 + Score4) / 3;
		}
	else if (High == static_cast<int>(Score2))
	{
		if (Low == static_cast<int>(Score1))
			Avg = (Score3 + Score4 + Score5) / 3;
		else if (Low == static_cast<int>(Score3))
			Avg = (Score1 + Score4 + Score5) / 3;
		else if (Low == static_cast<int>(Score4))
			Avg = (Score3 + Score1 + Score5) / 3;
		else
			Avg = (Score1 + Score3 + Score4) / 3;
	}
	else if (High == static_cast<int>(Score3))
	{
		if (Low == static_cast<int>(Score2))
			Avg = (Score1 + Score4 + Score5) / 3;
		else if (Low == static_cast<int>(Score1))
			Avg = (Score2 + Score4 + Score5) / 3;
		else if (Low == static_cast<int>(Score4))
			Avg = (Score1 + Score2 + Score5) / 3;
		else
			Avg = (Score2 + Score1 + Score4) / 3;
	}
	else if (High == static_cast<int>(Score4))
	{
		if (Low == static_cast<int>(Score2))
			Avg = (Score3 + Score1 + Score5) / 3;
		else if (Low == static_cast<int>(Score3))
			Avg = (Score2 + Score1 + Score5) / 3;
		else if (Low == static_cast<int>(Score1))
			Avg = (Score3 + Score2 + Score5) / 3;
		else
			Avg = (Score2 + Score3 + Score1) / 3;
	}
	else
	{
		if (Low == static_cast<int>(Score2))
			Avg = (Score3 + Score4 + Score1) / 3;
		else if (Low == static_cast<int>(Score3))
			Avg = (Score2 + Score4 + Score1) / 3;
		else if (Low == static_cast<int>(Score4))
			Avg = (Score3 + Score2 + Score1) / 3;
		else
			Avg = (Score2 + Score3 + Score4) / 3;
	}

	return Avg;
}

// Finding Highest
int findHighest(double Score1, double Score2, double Score3, double Score4,
	double Score5)
{
	if (Score1 > Score2 && Score1 > Score3 && Score1 > Score4 && Score1 > Score5)
		return Score1;
	else if (Score2 > Score1 && Score2 > Score3 && Score2 > Score4 &&
		Score2 > Score5)
		return Score2;
	else if (Score3 > Score2 && Score3 > Score1 && Score3 > Score4 &&
		Score3 > Score5)
		return Score3;
	else if (Score4 > Score2 && Score4 > Score3 && Score4 > Score1 &&
		Score4 > Score5)
		return Score4;
	else
		return Score5;
}

//Find Lowest
int findLowest(double Score1, double Score2, double Score3, double Score4,
	double Score5)
{
	if (Score1 < Score2 && Score1 < Score3 && Score1 < Score4 && Score1 < Score5)
		return Score1;
	else if (Score2 < Score1 && Score2 < Score3 && Score2 < Score4 &&
		Score2 < Score5)
		return Score2;
	else if (Score3 < Score2 && Score3 < Score1 && Score3 < Score4 &&
		Score3 < Score5)
		return Score3;
	else if (Score4 < Score2 && Score4 < Score3 && Score4 < Score1 &&
		Score4 < Score5)
		return Score4;
	else
		return Score5;
}
