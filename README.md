# TaxiProbleminConsole-CSharp
An app calling taxis 
```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace taxiProblem
{
    class Program
    {
        static void Main(string[] args)
        {
            // creating 5 taxis
            Taxi taxi1 = new Taxi(6, 8, 1);
            Taxi taxi2 = new Taxi(2, 9, 2);
            Taxi taxi3 = new Taxi(4, 3, 3);
            Taxi taxi4 = new Taxi(9, 3, 4);
            Taxi taxi5 = new Taxi(1, 7, 5);
            Console.WriteLine("Hello Mr. {0}, \n   The nearest taxi to you is {1}m away from you, and your trip will cost you {2}$. " , CustomerHolder.james.Name , CustomerHolder.james.CallTaxi() , CustomerHolder.james.CallTaxi()*3/10);
        }
    }
    class ArrayHolder
    {
        public static double[] distancesArr = new double[5];
    }
    class CustomerHolder
    {
        public static Customer ikram = new Customer(0, 0 , "Ikram");
        public static Customer james = new Customer(5, 6, "James");
    }
    class Taxi
    {
        public int xTaxiCoor;
        public int yTaxiCoor;
        public int TaxiNumRow;
        public double Distance;
        public Taxi(int _xTaxi, int _yTaxi, int _taxiNum)
        {
            this.xTaxiCoor = _xTaxi;
            this.yTaxiCoor = _yTaxi;
            this.TaxiNumRow = _taxiNum;
            this.Distance = EstimateDistance(CustomerHolder.james);
            ArrayHolder.distancesArr[this.TaxiNumRow - 1] = this.Distance;
        }
        public double EstimateDistance(Customer _customer)
        {
            return Math.Floor(Math.Sqrt(((this.xTaxiCoor - _customer.xCustCoor) * (this.xTaxiCoor - _customer.xCustCoor)) + ((this.yTaxiCoor - _customer.yCustCoor) * (this.yTaxiCoor - _customer.yCustCoor))));
        }
    }
    class Customer
    {
        public string Name;
        public int xCustCoor;
        public int yCustCoor;
        public Customer(int _xCust, int _yCust , string _name)
        {
            this.Name = _name;
            this.xCustCoor = _xCust;
            this.yCustCoor = _yCust;
        }
        public double CallTaxi()
        {
            return ArrayHolder.distancesArr.Min(); 
        }
    }
}   
```
