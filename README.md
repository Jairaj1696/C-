# C++ CODES 
# 1.
```cpp
#include <iostream>
using namespace std;
int main()
{
    int *a;
    int b;
    int c;
    cout<< "Enter The number b:-"<< endl;
    cin>>b;
    cout<<"Enter the number c:-"<< endl;
    cin>>c;
    
    a=&b;
    c=*a;
    
    cout<< a;
    cout<<b;
    cout<< "\n" << endl;
    cout<<c;
    return 0;
    
}
``` 

# 2.Create a Student class with attributes:name,roll number and marks. Add Member functions to input and display student details. Create at least 3 objects and display their data.
```cpp
#include <iostream>
using namespace std;
class Student{
    private:
        string name ;
        int rollNumber;
        float marks;
    public:
        void input(){
            cout<<"Enter Name :";
            cin>>name;
            
            cout<<"Enter Roll Number :";
            cin>>rollNumber;
            
            cout<<"Enter Marks :";
            cin>>marks;
        }

    void display(){
        cout<<"\nStudent Details:\n";
        cout<<"Name"<<name<<endl;
        cout<<"Roll Number"<<rollNumber<<endl;
        cout<<"Marks"<<marks<<endl;
        
    }
};
int main(){
    Student s1,s2,s3;
    cout<<"Enter details for student 1 \n";
    s1.input();
    cout<<"\nEnter details for student 2 \n";
    s2.input();
    cout<<"\nEnter details for student 3 \n";
    s3.input();
  cout<<"\n Displaying Student Data \n";
  s1.display();
  s2.display();
  s3.display();
  return 0;
}
```

# 3. Create a BankAccount class. Initialize account number and balance using a construcotr. Display a message when the destructor is called. Create objects inside a function to observe destructor behavior.
```cpp
#include <iostream>
using namespace std;
class BankAccount{
    private:
        int accountNumber;
        double balance;
    public :
        //Constructor
        BankAccount(int accNo,double bal){
            accountNumber=accNo;
            balance=bal;
            cout<<"Constructor called for Account No :"<<accountNumber<<endl;
            
        }
        //Distructor
        BankAccount(){
            cout<<"Distructor called for Account No;"<<accountNumber<<endl;
            
        }
        //Display function
        void display(){
            cout<<"Account Number:"<<accountNumber<<endl;
            cout<<"Balance :"<<balance<<endl;
        }
};
//Function to create objects
void createAccounts(){
    BankAccount acc1(101,5000.50);
    BankAccount acc2(102,10000.75);
    BankAccount acc3(103,696969.69);
    cout<<"\nInside createAccounts() function \n";
    acc1.display();
    acc2.display();
    acc3.display();
    cout<<"Exiting createAccounts() function....\n";
};
int main(){
    
    cout<<"Entering main()\n";
    createAccounts();

    
    return 0;
}
```
# 4. Create an employee class. Make a salary private. Provide getter and setter functions. Add validation: salary cannot be negative
```cpp
#include <iostream>
using namespace std;

class Employee {
private:
    double salary;
public:
    // Constructor
    Employee(double s = 0) {
        setSalary(s);
    }

    // Setter with validation
    void setSalary(double s) {
        if (s < 0) {
            cout << "Error: Salary cannot be negative." << endl;
        } else {
            salary = s;
        }
    }

    // Getter
    double getSalary() const {
        return salary;
    }
};

int main() {
    Employee emp;

    emp.setSalary(50000);
    cout << "Salary: " << emp.getSalary() << endl;

    emp.setSalary(-1000); // invalid
    cout << "Salary after invalid update: " << emp.getSalary() << endl;

    return 0;
}

```

# 5. Create a class Calculator. Overload a function add() for : int, double, three integers.
```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
};

int main() {
    Calculator calc;

    int x, y, z;
    double d1, d2;

    // two integers
    cout << "Enter two integers: ";
    cin >> x >> y;
    cout << "Sum (int): " << calc.add(x, y) << endl;

    // two doubles
    cout << "Enter two doubles: ";
    cin >> d1 >> d2;
    cout << "Sum (double): " << calc.add(d1, d2) << endl;

    // three integers
    cout << "Enter three integers: ";
    cin >> x >> y >> z;
    cout << "Sum (three ints): " << calc.add(x, y, z) << endl;

    return 0;
}
```
