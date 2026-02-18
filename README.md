# C++ CODES 
1.// Online C++ compiler to run C++ program online
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

# Create a Student class with attributes:name,roll number and marks. Add Member functions to input and display student details. Create at least 3 objects and display their data.
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

# Create a BankAccount class. Initialize account number and balance using a construcotr. Display a message when the destructor is called. Create objects inside a function to observe destructor behavior.
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
# Create an employee class. Make a salary private. Provide getter and setter functions. Add validation: salary cannot be negative
```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

class Employee {
private:
    string name;
    double salary;

public:
    // Constructor
    Employee(string name, double salary) {
        this->name = name;
        setSalary(salary);  // Use setter for validation
    }

    // Getter for name
    string getName() const {
        return name;
    }

    // Setter for name
    void setName(string name) {
        this->name = name;
    }

    // Getter for salary
    double getSalary() const {
        return salary;
    }

    // Setter for salary with validation
    void setSalary(double salary) {
        if (salary < 0) {
            throw invalid_argument("Salary cannot be negative.");
        }
        this->salary = salary;
    }
};

// Example usage
int main() {
    try {
        Employee emp("John", 5000);
        cout << "Name: " << emp.getName() << endl;
        cout << "Salary: " << emp.getSalary() << endl;

        emp.setSalary(-1000);  // This will throw an exception
    }
    catch (const exception& e) {
        cout << "Error: " << e.what() << endl;
    }

    return 0;
}
```
