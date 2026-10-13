# task5

```

using System;

class Program
{
    static void Main()
    {
        Console.OutputEncoding = System.Text.Encoding.UTF8;
        Console.WriteLine("=== ОПЕРАЦИЯ «ОГРАБЛЕНИЕ БАНКА» ===");
        Console.WriteLine("Команда взломщиков вскрывает многоуровневое хранилище\n");

        // 1. Инициализировать массив гаджетов взломщика на 5 наименований
        string[] gadgets = {
            "Термитный бур",
            "ЭМИ-глушилка",
            "Дымовая граната",
            "Флешка с эксплойтом",
            "Трос"
        };

        // 4. Вывести список доступного оборудования через цикл for
        Console.WriteLine("--- Доступное оборудование ---");
        for (int i = 0; i < gadgets.Length; i++)
        {
            Console.WriteLine($"  Слот [{i}]: {gadgets[i]}");
        }
        Console.WriteLine();

        // 5. Найти ячейку с "ЭМИ-глушилка" с помощью Array.IndexOf
        //    перед отключением лазеров
        int emiIndex = Array.IndexOf(gadgets, "ЭМИ-глушилка");
        if (emiIndex != -1)
        {
            Console.WriteLine($"[!] ЭМИ-глушилка найдена в слоте {emiIndex}.");
            Console.WriteLine("    Лазерная решётка отключена.");
            // Можно сразу пометить как использованную
            gadgets[emiIndex] = "Пусто (использовано)";
        }
        else
        {
            Console.WriteLine("ЭМИ-глушилка не найдена! Операция под угрозой.");
        }
        Console.WriteLine();

        // 2. Создать параллельные массивы для рубежей охраны:
        //    тип рубежа, сложность взлома, таймер тревоги
        string[] barrierTypes = {
            "Лазерная решётка",
            "Служба охраны",
            "Бронированный сейф"
        };

        int[] barrierDifficulty = { 35, 70, 130 };   // HP / сложность
        int[] alarmTimers = { 25, 45, 90 };          // секунды до тревоги

        // 6. Записать секунды, потраченные на взлом каждой охранной системы
        //    в массив hackingTimes
        int[] hackingTimes = new int[barrierTypes.Length];

        Console.WriteLine("--- Взлом рубежей охраны ---");
        for (int i = 0; i < barrierTypes.Length; i++)
        {
            // Симуляция: время взлома зависит от сложности
            // (для учебного примера просто задаём реалистичные значения)
            hackingTimes[i] = barrierDifficulty[i] / 2 + 5; // примерная формула

            Console.WriteLine($"Рубеж: {barrierTypes[i]}");
            Console.WriteLine($"  Сложность: {barrierDifficulty[i]} HP");
            Console.WriteLine($"  Таймер тревоги: {alarmTimers[i]} сек");
            Console.WriteLine($"  Время взлома: {hackingTimes[i]} сек");
            Console.WriteLine();
        }

        // 3. Создать массив объемов похищенных средств из ячеек
        //    int[] lootValues (на 6 ячеек)
        int[] lootValues = { 150000, 85000, 320000, 45000, 210000, 175000 };

        // 7. Алгоритмически рассчитать общую сумму добычи из массива lootValues
        int totalLoot = 0;
        for (int i = 0; i < lootValues.Length; i++)
        {
            totalLoot += lootValues[i];
        }
        Console.WriteLine($"Общая сумма добычи: {totalLoot:N0} руб.");
        Console.WriteLine();

        // 8. Найти самый сложный рубеж (максимум по времени взлома)
        //    в массиве hackingTimes
        int maxTime = hackingTimes[0];
        int maxIndex = 0;
        for (int i = 1; i < hackingTimes.Length; i++)
        {
            if (hackingTimes[i] > maxTime)
            {
                maxTime = hackingTimes[i];
                maxIndex = i;
            }
        }
        Console.WriteLine($"Самый сложный рубеж: {barrierTypes[maxIndex]}");
        Console.WriteLine($"  Время взлома: {maxTime} сек");
        Console.WriteLine();

        // 9. Отсортировать массив добычи lootValues по возрастанию через Array.Sort
        Console.WriteLine("Добыча до сортировки: " + string.Join(", ", lootValues));
        Array.Sort(lootValues);
        Console.WriteLine("Добыча после сортировки (по возрастанию): " + string.Join(", ", lootValues));
        Console.WriteLine();

        // 10. Обнулить первые два элемента снаряжения через Array.Clear
        //     после использования на первом этаже
        Console.WriteLine("--- После первого этажа ---");
        Console.WriteLine("Снаряжение до очистки:");
        for (int i = 0; i < gadgets.Length; i++)
            Console.WriteLine($"  [{i}] {gadgets[i]}");

        Array.Clear(gadgets, 0, 2);   // обнуляет первые 2 элемента (ставит null)

        Console.WriteLine("Снаряжение после Array.Clear(0, 2):");
        for (int i = 0; i < gadgets.Length; i++)
        {
            string item = gadgets[i] ?? "Пусто";
            Console.WriteLine($"  [{i}] {item}");
        }

        Console.WriteLine("\n=== Операция завершена ===");
        Console.ReadKey();
    }
}
```

![№1](screens/01.png)
![№2](screens/02.png)
![№3](screens/03.png)
