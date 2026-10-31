# Домашние задание к лабе 6. 
## Дано шестизначное число, определить является ли оно «счастливым».
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <locale.h>

int digits_sum(int number);
int is_lucky(int number);

int main(void)
{
    int number;
    int lucky;

    setlocale(LC_ALL, ".UTF8");

    printf("Введите шестизначное число: ");
    if (scanf("%d", &number) != 1 || number < 100000 || number > 999999)
    {
        printf("Ошибка: нужно ввести шестизначное число.\n");
        return 1;
    }

    lucky = is_lucky(number);
    if (lucky)
        printf("Число %d счастливое\n", number);
    else
        printf("Число %d не счастливое\n", number);

    return 0;
}

int digits_sum(int number)
{
    int sum;
    int d1;
    int d2;
    int d3;

    d1 = number / 100 % 10;
    d2 = number / 10 % 10;
    d3 = number % 10;
    sum = d1 + d2 + d3;

    return sum;
}

int is_lucky(int number)
{
    int left;
    int right;
    int lucky;

    left = digits_sum(number / 1000);
    right = digits_sum(number % 1000);
    lucky = (left == right);

    return lucky;
}
```
## Результат
Введите шестизначное число: 385916
Число 385916 счастливое

Введите шестизначное число: 123456
Число 123456 не счастливое

Введите шестизначное число: 12345
Ошибка: нужно ввести шестизначное число.

## Выполнил
Студент Еркимбеков Дмитрий бИД-261