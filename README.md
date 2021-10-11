# hello-world
осматриваюсь на git hub ' e (11.10.2021 14:08) может тут реально можно будет найти чтото интересное :D
#include <iostream>
#include <math.h>

// Задние 2 пункт 1 
float mExp(float epsilon, int x)//Функция exp вычисляет значение экспоненты от val и возвращает его. Возвращаемое значение (экспонента числа val) — это число е, возведенное в степень val.


{
	int n = 1;
	float sum = 1, fact = 1; 

	while (fabs(pow(x, n) / fact) > epsilon)//Функция fabs вычисляет абсолютное значение (модуль) и возвращает его |х| .
	{//Функция pow() библиотеки cmath принимает два параметра: a, b. Первое число a  (базовое) возводится в степень b.
		fact = fact * n;
		sum += (pow(x, n) / fact);
		n++;
	}
	float delta = sum - exp(x);
	std::cout << x << "\t\t" << sum << "\t\t" << delta << "\t\t" << n << std::endl;//Cout - это объект выходного потока пространства имен std::. Это необъявленный идентификатор.
	//Cin - это объект входного потока пространства имен std: std::cin >> x; В данном коде программы используется оператор cin, операция взятия из потока >> чтобы получить от пользователя введенное им значение.
	return delta, n;
}

// Задача номер 3.1
float mSin(float epsilon, float x)
{
	int n = 1;
	float sum = x, fact = 1;
	while (fabs(pow(x, n) / fact) > epsilon)
	{
		fact = fact * (2 * n + 1);
		sum = sum + (pow(-1, n) * pow(x, (2 * n + 1))) / fact;
		n++;

	}
	float delta = sum - sin(x);
	return delta, n;
}

//4 точка 1
float mCos(float epsilon, float x)
{
	int n = 1;
	float sum = 1, fact = 1;
	while (fabs(pow(x, n) / fact) > epsilon)
	{
		fact = fact * (2 * n );
		sum = sum + (pow(-1, n) * pow(x, (2 * n ))) / fact;
		n++;
	}
	float delta = sum - cos(x);
	return delta, n;
}



int main()
{
	//1.111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111
	int array1[6] = { 1,2,3,4,5,6 };
	//Одномерный массив — массив, с одним параметром, характеризующим количество элементов одномерного массива. 
	//Фактически одномерный массив — это массив, у которого может быть только одна строка, и n-е количество столбцов. Столбцы в одномерном массиве — это элементы массива. 
	int array2[6] = { 23,21,32,12,32,73 };
	int array3[6] = { 6,5,4,3,2,1 };

	//2.3
	int array_x[11] = { -5,-4,-3,-2,-1,0,1,2,3,4,5 };
	float epsilon = 0.001;

	for (int count = 0; count < 11; count++)
	{
		mExp(epsilon, array_x[count]);
	}
	//2.4
	epsilon = 0.000001;
	std::cout <<"\n\n\n"<< "epsilon = " << epsilon << "\n\n";

	for (int count = 0; count < 11; count++)
	{
		mExp(epsilon, array_x[count]);
	}

	//3.2
	epsilon = 0.001;
	double array_sin_cos[7] = { 0, M_PI / 2,  M_PI, 3 * M_PI / 2, M_PI / 6, M_PI / 3, M_PI / 4 };

	for (int count = 0; count < 7; count++)
	{
		mSin(epsilon, array_sin_cos[count]);
	}

	//4.2
	for (int count = 0; count < 7; count++)
	{
		mCos(epsilon, array_sin_cos[count]);
	}
}
