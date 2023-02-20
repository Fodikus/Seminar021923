# Seminar021923
Домашняя работа №8 к семинару "Знакомство с языками программирования"

# Задача 54: Задайте двумерный массив. Напишите программу, которая упорядочит по убыванию элементы каждой строки двумерного массива.
```
void InputMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            matrix[i, j] = new Random().Next(0, 10);
    }
}

void PrintMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            Console.Write($"{matrix[i, j]} \t");
        Console.WriteLine();
    }
}

void SortDescending(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            for (int row = j; row < matrix.GetLength(1); row++)
            {
                if (matrix[i, j] < matrix[i, row])
                {
                    int temp = matrix[i, row];
                    matrix[i, row] = matrix[i, j];
                    matrix[i, j] = temp;
                }
            }

        }
    }
}

Console.Clear();
Console.Write("Введите размер массива: ");

int[] size = Console.ReadLine().Split().Select(x => int.Parse(x)).ToArray();
int[,] matrix = new int[size[0], size[1]];
Console.WriteLine("Начальный массив:");
InputMatrix(matrix);
PrintMatrix(matrix);
SortDescending(matrix);
Console.WriteLine("Сортировка по убыванию:");
PrintMatrix(matrix);
```

# Задача 56: Задайте прямоугольный двумерный массив. Напишите программу, которая будет находить строку с наименьшей суммой элементов.
```
void InputMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            matrix[i, j] = new Random().Next(0, 10);
    }
}

void PrintMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            Console.Write($"{matrix[i, j]} \t");
        Console.WriteLine();
    }
}

int SearchMinIndex(int[,] matrix)
{
    int index = 0;
    int min = 0;
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        int sum = 0;
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            if (i==0)
                min = min + matrix[i,j];
            else
                sum = sum + matrix[i,j];
        }

        if (i==0)
        {
            index = i;
        }
        else if (min>=sum)
        {
            min = sum;
            index = i;  
        }
    }

    return index;
}

Console.Clear();
Console.Write("Введите размер массива: ");

int[] size = Console.ReadLine().Split().Select(x => int.Parse(x)).ToArray();
while (size[0] != size[1])
{
    Console.Write("Вы ошиблись!\nВведите размер массива: ");
    size = Console.ReadLine().Split().Select(x => int.Parse(x)).ToArray();
}
int[,] matrix = new int[size[0], size[1]];
Console.WriteLine("Начальный массив:");
InputMatrix(matrix);
PrintMatrix(matrix);
int minIndex = SearchMinIndex(matrix);
Console.WriteLine($"Cтрока с наименьшей суммой элементов: {minIndex + 1}");
```

# Задача 58: Задайте две матрицы. Напишите программу, которая будет находить произведение двух матриц.
```

```

# Задача 60. ...Сформируйте трёхмерный массив из неповторяющихся двузначных чисел. Напишите программу, которая будет построчно выводить массив, добавляя индексы каждого элемента.
```
void InputMatrix(int[,,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            for (int k = 0; k < matrix.GetLength(2); k++)
                matrix[i, j, k] = RandomValue(matrix, i, j, k); 
        }
    }
}

static int RandomValue(int[,,] matrix, int i, int j, int k)
{
    int value = default;
    bool flag = true;
    while (flag)
    {
        bool noStop = true;
        value = new Random().Next(10, 100);
        for (int x = 0; x < matrix.GetLength(0) && noStop; x++)
        {
            for (int y = 0; y < matrix.GetLength(1) && noStop; y++)
            {
                for (int z = 0; z < matrix.GetLength(2) && noStop; z++)
                {
                    if (matrix[x, y, z] == value) 
                        noStop = false; 
                    if (x == i && y == j && z == k) 
                        flag = false; 
                }
            }
        }
    }
    return value;
}

void PrintMatrix(int[,,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            for (int k = 0; k < matrix.GetLength(2); k++) 
                Console.Write($"{matrix[i, j, k], 1}({i},{j},{k}) \t");
            Console.WriteLine();
        }
    }
}

Console.Clear();
Console.WriteLine("Массив размером 2 x 2 x 2: ");
int[,,] matrix = new int[2, 2, 2];
InputMatrix(matrix);
PrintMatrix(matrix);
```

# Задача 61: Вывести первые N строк треугольника Паскаля. Сделать вывод в виде равнобедренного треугольника.
```

```

# Задача 62. Напишите программу, которая заполнит спирально массив 4 на 4.
```
void PrintMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
            Console.Write($"{matrix[i, j]} \t");
        Console.WriteLine();
    }
}

Console.Clear();
Console.Write("Cпиральный массив 4 на 4: ");
int[,] matrix = new int[4, 4];
Console.WriteLine(); 

int temp = 1;
int i = 0;
int j = 0;

while (temp <= matrix.GetLength(0) * matrix.GetLength(1))
{
    matrix[i, j] = temp;
    temp++;
    if (i <= j + 1 && i + j < matrix.GetLength(1) - 1)
        j++;
    else if (i < j && i + j >= matrix.GetLength(0) - 1)
        i++;
    else if (i >= j && i + j > matrix.GetLength(1) - 1)
        j--;
    else
        i--;
}

PrintMatrix(matrix);
```
