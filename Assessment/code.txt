using System;
using System.Collections.Generic;
using System.Collections;

namespace project1
{
    class Program
    {
        public static List<string> TeacherDataList = new List<string> { "1", "Prajwal", "1/A", "2", "Mohnish", "2/A", "3", "Shubham", "3/A" };
        static void Main(string[] args)
        {
            int choice;
            do
            {
                Console.WriteLine("Type numbers for following actions \n1.View Teacher Data\n2.Add Teacher Data\n3.Update Teacher Data\n4.Delete Teacher Data");
                int key;
                key = Convert.ToInt32(Console.ReadLine());
                switch (key)
                {
                    case 1:
                        {
                            ViewTeacherData();
                            break;
                        }

                    case 2:
                        {
                            AddTeacherData();
                            break;
                        }

                    case 3:
                        {
                            UpdateTeacherData();
                            break;
                        }

                    case 4:
                        {
                            DeleteTeacherData();
                            break;
                        }
                }
                if (key > 4 || key < 0)
                {
                    Console.WriteLine("Invalid Option");
                }
                Console.Write("To continue press 0 ");
                choice = Convert.ToInt32(Console.ReadLine());
            } while (choice == 0);

        }//Main
        public static void ViewTeacherData()
        {
            int size = TeacherDataList.Count;
            Console.WriteLine("ID\tTeacher Name\tSection");
            for (int i = 0; i < TeacherDataList.Count; i += 3)
            {
                Console.Write(TeacherDataList[i] + "\t" + TeacherDataList[i + 1] + "\t\t" + TeacherDataList[i + 2] + "\n");
            }
        }//ViewTeacherData

        public static void UpdateTeacherData()
        {
            int size1 = TeacherDataList.Count;
            Console.WriteLine("Enter the name to update");
            string Name = Console.ReadLine();
            bool flag = false;
            for (int i = 1; i < size1; i += 3)
            {
                if (Name == TeacherDataList[i])
                {
                    Console.WriteLine("Enter the new name");
                    string p = Console.ReadLine();
                    TeacherDataList[i] = p;
                    flag = true;
                    break;
                }
            }
            if (flag == false)
            {
                Console.WriteLine("Name does not match,please check");
            }
        }//UpdateTeacherData

        public static void AddTeacherData()
        {
            Console.WriteLine("Enter the Teacher ID: ");
            string s = Console.ReadLine();
            TeacherDataList.Add(s);
            Console.WriteLine("Enter the Teacher Name: ");
            s = Console.ReadLine();
            TeacherDataList.Add(s);
            Console.WriteLine("Enter the Teacher Class and Section: ");
            s = Console.ReadLine();
            TeacherDataList.Add(s);
        }//AddTeacherData


        public static void DeleteTeacherData()
        {
            Console.WriteLine("Enter the name to delete");
            string s = Console.ReadLine();
            bool flag = false;
            for (int i = 1; i < TeacherDataList.Count; i += 3)
            {
                if (TeacherDataList[i] == s)
                {
                    TeacherDataList.RemoveAt(i - 1);
                    TeacherDataList.RemoveAt(i - 1);
                    TeacherDataList.RemoveAt(i - 1);
                    flag = true;
                }
            }
            if (flag == false)
            {
                Console.WriteLine("Name does not match,please check");
            }
        } //DeleteTeacherData
    }//class
}//namespace

