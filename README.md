PrimeNumbers
============

Check if given number is Prime

using System;

using System.Collections.Generic;

class PrimeNumbers

{

    static void Main()
    
    {
        // Prime numbers are divisible only by themselves and 1 
        // The most simple way to determine if number is prime is with trial devison
        // www.wikihow.com/Check-if-a-Number-Is-Prime - mathematical info about how to check if number is prime
       
        while (true)
        {
            Console.WriteLine("Type number to check if it is Prime /1 to 100/:");
            Console.ForegroundColor = ConsoleColor.Yellow;

            int number = int.Parse(Console.ReadLine());

            Console.ResetColor();

            if (number % 2 == 0)
            {
                if (number == 2)
                {
                    TextIsPrime(number);
                }

                else
                {
                    TextNotPrime(number);

                    Console.WriteLine("Evenly divisible by the number 2");
                    Console.WriteLine();
                }
            }

            if (number % 2 == 1)
            {
                if (number == 1)
                {
                    Console.WriteLine("The number must be a whole number greater than 1");
                    Console.WriteLine();
                }

                else
                {
                    double numberSqrtD = Math.Sqrt(number);

                    int numberSqrtI = Convert.ToInt32(numberSqrtD);

                    List<int> devisibleBy = new List<int>() { };
                    
                    bool primeOrNot_1 = false;
                    bool primeOrNot_2 = false;

                    for (int i = 2; i <= numberSqrtI; i++)
                    {
                        if (number % i == 0) // if evenly divisible by any whole number from 3 to Math.Sqrt(number) = NOT PRIME
                        {
                            primeOrNot_1 = true;

                            devisibleBy.Add(i);
                        }

                        if (number % i == 1) // if NOT evenly divisible by any whole number from 3 to Math.Sqrt(number) = PRIME
                        {
                            primeOrNot_2 = true;
                        }
                    }

                    if (primeOrNot_1 == false && primeOrNot_2 == true)
                    {
                        TextIsPrime(number);

                        Console.WriteLine("Not evenly divisible by any whole number from 2 to it's Rounded square root {0}", numberSqrtI);
                        Console.WriteLine();
                    }

                    if (primeOrNot_1 == true)
                    {
                        
                        TextNotPrime(number);

                        Console.WriteLine("Evenly divisible by following numbers from 3 to it's Rounded square root {0}", numberSqrtI);

                        foreach (int item in devisibleBy)
                        {
                            Console.Write("{0}, ", item);
                        }

                        Console.WriteLine();
                        Console.WriteLine();
                    }
                }
            }
        }
    }

    static void TextNotPrime(int number)
    {
        Console.WriteLine();
        Console.Write("The number {0} is ", number);
        Console.ForegroundColor = ConsoleColor.Red;
        Console.Write("NOT Prime");
        Console.ResetColor();
        Console.WriteLine();
    }

    static void TextIsPrime(int number)
    {
        Console.WriteLine();
        Console.Write("The number {0} ", number);
        Console.ForegroundColor = ConsoleColor.Green;
        Console.Write("IS Prime");
        Console.ResetColor();
        Console.WriteLine();
    }
}
