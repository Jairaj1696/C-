# C++ CODES 

# Creating a Student class with attributes: name, roll number, and marks and performing certain operations.
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
INPUT/OUTPUT
```
Enter details for Student 1:
Enter name: Alice
Enter roll number: 101
Enter marks: 85
Enter details for Student 2:
Enter name: Bob
Enter roll number: 102
Enter marks: 92
Enter details for Student 3:
Enter name: Charlie
Enter roll number: 103
Enter marks: 78

Displaying student details:
Name: Alice
Roll Number: 101
Marks: 85
-------------------
Name: Bob
Roll Number: 102
Marks: 92
-------------------
Name: Charlie
Roll Number: 103
Marks: 78
-------------------
```

# Creating a BankAccount Class with Constructor and Destructor.
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
INPUT/OUTPUT
```
Calling createAccounts function:
Account 12345 created with balance $1000.00
Account 67890 created with balance $2500.00
Inside createAccounts function.
Destructor called for account 67890
Destructor called for account 12345
Back in main. Program ending.
```

# Creating an Employee class with private specifier and validation.
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
INPUT/OUTPUT
```
Employee 1:
Name: Alice
Salary: $50000.00

Employee 2:
Name: Bob
Salary: $0.00

After updating Employee 2's salary:
Name: Bob
Salary: $45000.00
```

# Creating a class Calculator and using method overloading.
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
INPUT/OUTPUT
```
Enter two integers: 3 5
Sum (int): 8
Enter two doubles: 2.2 4.3
Sum (double): 6.5
Enter three integers: 1 2 3
Sum (three ints): 6
```

# Student Class with Dynamic Subjects Array using Struct.
```cpp
#include <iostream>
#include <string>

struct Subject {
    std::string name;
    int marks;
};

class Student {
private:
    int roll;
    std::string name;
    Subject* subjects;
    int n;

public:
    // Constructor: Allocates dynamic memory for n subjects
    Student(int r, std::string nm, int num_subjects) : roll(r), name(nm), n(num_subjects) {
        subjects = new Subject[n];
    }

    // Destructor: Frees dynamic memory for subjects
    ~Student() {
        delete[] subjects;
    }

    // Input function: Inputs details for each subject
    void input() {
        for (int i = 0; i < n; ++i) {
            std::cout << "Enter subject " << (i + 1) << " name: ";
            std::cin >> subjects[i].name;
            std::cout << "Enter marks for " << subjects[i].name << ": ";
            std::cin >> subjects[i].marks;
        }
    }

    // Display function: Shows student and subject details
    void display() const {
        std::cout << "Roll: " << roll << std::endl;
        std::cout << "Name: " << name << std::endl;
        std::cout << "Subjects:" << std::endl;
        for (int i = 0; i < n; ++i) {
            std::cout << "  " << subjects[i].name << ": " << subjects[i].marks << std::endl;
        }
        std::cout << "Total Marks: " << total() << std::endl;
        std::cout << "Grade: " << grade() << std::endl;
        std::cout << "-------------------" << std::endl;
    }

    // Total function: Sums up marks
    int total() const {
        int sum = 0;
        for (int i = 0; i < n; ++i) {
            sum += subjects[i].marks;
        }
        return sum;
    }

    // Grade function: Assigns grade based on total (assuming max marks per subject is 100, total max is 100*n)
    char grade() const {
        int t = total();
        int max_possible = 100 * n;
        double percentage = (static_cast<double>(t) / max_possible) * 100;
        if (percentage >= 90) return 'A';
        else if (percentage >= 80) return 'B';
        else if (percentage >= 70) return 'C';
        else if (percentage >= 60) return 'D';
        else return 'F';
    }

    // Getter for name (used for finding topper)
    std::string getName() const { return name; }
};

int main() {
    int N;
    std::cout << "Enter number of students: ";
    std::cin >> N;

    // Dynamic array of student pointers
    Student** students = new Student*[N];

    for (int i = 0; i < N; ++i) {
        int roll, n_subjects;
        std::string name;
        std::cout << "\nEnter details for Student " << (i + 1) << ":" << std::endl;
        std::cout << "Roll: ";
        std::cin >> roll;
        std::cout << "Name: ";
        std::cin >> name;
        std::cout << "Number of subjects: ";
        std::cin >> n_subjects;

        students[i] = new Student(roll, name, n_subjects);
        students[i]->input();
    }

    // Display all students
    std::cout << "\nDisplaying all students:" << std::endl;
    for (int i = 0; i < N; ++i) {
        students[i]->display();
    }

    // Find topper (student with highest total marks)
    int topper_index = 0;
    int max_total = students[0]->total();
    for (int i = 1; i < N; ++i) {
        if (students[i]->total() > max_total) {
            max_total = students[i]->total();
            topper_index = i;
        }
    }
    std::cout << "Topper: " << students[topper_index]->getName() << " with total marks " << max_total << std::endl;

    // Free memory: Delete each student (destructor handles subjects), then the array
    for (int i = 0; i < N; ++i) {
        delete students[i];
    }
    delete[] students;

    return 0;
}
```
INPUT/OUTPUT
```
Enter number of students: 2

Enter details for Student 1:
Roll: 101
Name: Alice
Number of subjects: 2
Enter subject 1 name: Math
Enter marks for Math: 90
Enter subject 2 name: Science
Enter marks for Science: 85

Enter details for Student 2:
Roll: 102
Name: Bob
Number of subjects: 2
Enter subject 1 name: Math
Enter marks for Math: 80
Enter subject 2 name: Science
Enter marks for Science: 95

Displaying all students:
Roll: 101
Name: Alice
Subjects:
  Math: 90
  Science: 85
Total Marks: 175
Grade: A
-------------------
Roll: 102
Name: Bob
Subjects:
  Math: 80
  Science: 95
Total Marks: 175
Grade: A
-------------------
Topper: Alice with total marks 175
```

# PatientQueue Class with Priority Enqueue.
```cpp
#include <iostream>
#include <string>

struct Node {
    int id;
    std::string name;
    int severity;
    Node* next;
};

class PatientQueue {
private:
    Node* front;  // Points to the front of the queue (highest priority)

public:
    // Constructor
    PatientQueue() : front(nullptr) {}

    // Destructor: Frees all nodes
    ~PatientQueue() {
        while (front) {
            dequeue();  // Dequeue will handle deletion
        }
    }

    // Enqueue: Inserts based on severity (higher severity first)
    void enqueue(int id, std::string name, int severity) {
        Node* newNode = new Node{id, name, severity, nullptr};

        if (!front || severity > front->severity) {
            // Insert at front if higher severity or empty queue
            newNode->next = front;
            front = newNode;
        } else {
            // Find position to insert (after nodes with higher or equal severity)
            Node* current = front;
            while (current->next && current->next->severity >= severity) {
                current = current->next;
            }
            newNode->next = current->next;
            current->next = newNode;
        }
        std::cout << "Enqueued: " << name << " (ID: " << id << ", Severity: " << severity << ")" << std::endl;
    }

    // Dequeue: Removes and deletes the front node
    void dequeue() {
        if (!front) {
            std::cout << "Queue is empty. Cannot dequeue." << std::endl;
            return;
        }
        Node* temp = front;
        front = front->next;
        std::cout << "Dequeued: " << temp->name << " (ID: " << temp->id << ", Severity: " << temp->severity << ")" << std::endl;
        delete temp;
    }

    // Display: Shows all patients in the queue
    void display() const {
        if (!front) {
            std::cout << "Queue is empty." << std::endl;
            return;
        }
        Node* current = front;
        std::cout << "Patient Queue (from highest to lowest priority):" << std::endl;
        while (current) {
            std::cout << "ID: " << current->id << ", Name: " << current->name << ", Severity: " << current->severity << std::endl;
            current = current->next;
        }
    }
};

int main() {
    PatientQueue queue;

    // Demonstrate enqueue
    queue.enqueue(1, "Alice", 5);
    queue.enqueue(2, "Bob", 3);
    queue.enqueue(3, "Charlie", 7);  // Higher severity, should go to front
    queue.enqueue(4, "Diana", 4);

    std::cout << "\nAfter enqueues:" << std::endl;
    queue.display();

    // Demonstrate dequeue
    std::cout << "\nDequeue operations:" << std::endl;
    queue.dequeue();
    queue.display();

    queue.dequeue();
    queue.display();

    // Add more and dequeue
    queue.enqueue(5, "Eve", 6);
    std::cout << "\nAfter adding Eve:" << std::endl;
    queue.display();

    queue.dequeue();
    queue.display();

    // Destructor will clean up remaining nodes when queue goes out of scope
    return 0;
}
```
INPUT/OUTPUT
```
Enqueued: Alice (ID: 1, Severity: 5)
Enqueued: Bob (ID: 2, Severity: 3)
Enqueued: Charlie (ID: 3, Severity: 7)
Enqueued: Diana (ID: 4, Severity: 4)

After enqueues:
Patient Queue (from highest to lowest priority):
ID: 3, Name: Charlie, Severity: 7
ID: 1, Name: Alice, Severity: 5
ID: 4, Name: Diana, Severity: 4
ID: 2, Name: Bob, Severity: 3

Dequeue operations:
Dequeued: Charlie (ID: 3, Severity: 7)
Patient Queue (from highest to lowest priority):
ID: 1, Name: Alice, Severity: 5
ID: 4, Name: Diana, Severity: 4
ID: 2, Name: Bob, Severity: 3

Dequeued: Alice (ID: 1, Severity: 5)
Patient Queue (from highest to lowest priority):
ID: 4, Name: Diana, Severity: 4
ID: 2, Name: Bob, Severity: 3

After adding Eve:
Patient Queue (from highest to lowest priority):
ID: 5, Name: Eve, Severity: 6
ID: 4, Name: Diana, Severity: 4
ID: 2, Name: Bob, Severity: 3

Dequeued: Eve (ID: 5, Severity: 6)
Patient Queue (from highest to lowest priority):
ID: 4, Name: Diana, Severity: 4
ID: 2, Name: Bob, Severity: 3
```

# Library Class with BookNode Linked List.
```cpp
#include <iostream>
#include <string>

struct BookNode {
    int id;
    std::string title;
    std::string author;
    bool issued;
    BookNode* next;
};

class Library {
private:
    BookNode* head;

public:
    // Constructor
    Library() : head(nullptr) {}

    // Destructor: Frees all nodes in the linked list
    ~Library() {
        BookNode* current = head;
        while (current) {
            BookNode* temp = current;
            current = current->next;
            delete temp;
        }
    }

    // Add a new book to the end of the list
    void addBook(int id, std::string title, std::string author) {
        BookNode* newNode = new BookNode{id, title, author, false, nullptr};
        if (!head) {
            head = newNode;
        } else {
            BookNode* current = head;
            while (current->next) {
                current = current->next;
            }
            current->next = newNode;
        }
        std::cout << "Book added: " << title << std::endl;
    }

    // Issue a book by ID
    void issueBook(int id) {
        BookNode* current = head;
        while (current) {
            if (current->id == id) {
                if (!current->issued) {
                    current->issued = true;
                    std::cout << "Book issued: " << current->title << std::endl;
                } else {
                    std::cout << "Book already issued: " << current->title << std::endl;
                }
                return;
            }
            current = current->next;
        }
        std::cout << "Book with ID " << id << " not found." << std::endl;
    }

    // Return a book by ID
    void returnBook(int id) {
        BookNode* current = head;
        while (current) {
            if (current->id == id) {
                if (current->issued) {
                    current->issued = false;
                    std::cout << "Book returned: " << current->title << std::endl;
                } else {
                    std::cout << "Book was not issued: " << current->title << std::endl;
                }
                return;
            }
            current = current->next;
        }
        std::cout << "Book with ID " << id << " not found." << std::endl;
    }

    // Search for a book by title
    void searchBook(std::string title) {
        BookNode* current = head;
        while (current) {
            if (current->title == title) {
                std::cout << "Book found - ID: " << current->id << ", Title: " << current->title
                          << ", Author: " << current->author << ", Issued: " << (current->issued ? "Yes" : "No") << std::endl;
                return;
            }
            current = current->next;
        }
        std::cout << "Book with title '" << title << "' not found." << std::endl;
    }

    // Display all books
    void displayAll() {
        if (!head) {
            std::cout << "No books in the library." << std::endl;
            return;
        }
        BookNode* current = head;
        std::cout << "Library Books:" << std::endl;
        while (current) {
            std::cout << "ID: " << current->id << ", Title: " << current->title
                      << ", Author: " << current->author << ", Issued: " << (current->issued ? "Yes" : "No") << std::endl;
            current = current->next;
        }
    }
};

int main() {
    Library lib;

    // Add books
    lib.addBook(1, "1984", "George Orwell");
    lib.addBook(2, "To Kill a Mockingbird", "Harper Lee");
    lib.addBook(3, "The Great Gatsby", "F. Scott Fitzgerald");

    // Display all
    lib.displayAll();

    // Issue and return books
    lib.issueBook(1);
    lib.issueBook(1);  // Try issuing again
    lib.returnBook(1);
    lib.returnBook(1);  // Try returning again

    // Search
    lib.searchBook("1984");
    lib.searchBook("Nonexistent Book");

    // Display again
    lib.displayAll();

    // Destructor will clean up memory
    return 0;
}
```
INPUT/OUTPUT
```
Book added: 1984
Book added: To Kill a Mockingbird
Book added: The Great Gatsby
Library Books:
ID: 1, Title: 1984, Author: George Orwell, Issued: No
ID: 2, Title: To Kill a Mockingbird, Author: Harper Lee, Issued: No
ID: 3, Title: The Great Gatsby, Author: F. Scott Fitzgerald, Issued: No
Book issued: 1984
Book already issued: 1984
Book returned: 1984
Book was not issued: 1984
Book found - ID: 1, Title: 1984, Author: George Orwell, Issued: No
Book with title 'Nonexistent Book' not found.
Library Books:
ID: 1, Title: 1984, Author: George Orwell, Issued: No
ID: 2, Title: To Kill a Mockingbird, Author: Harper Lee, Issued: No
ID: 3, Title: The Great Gatsby, Author: F. Scott Fitzgerald, Issued: No
```

# BankAccount Class with Transaction Linked List.
```cpp

#include <iostream>
#include <string>

struct Transaction {
    std::string type;  // "Deposit" or "Withdraw"
    double amount;
    std::string date;
    Transaction* next;
};

class BankAccount {
private:
    int accountNo;
    std::string holderName;
    double balance;
    Transaction* historyHead;

public:
    // Constructor
    BankAccount(int accNo, std::string name, double initialBalance = 0.0)
        : accountNo(accNo), holderName(name), balance(initialBalance), historyHead(nullptr) {}

    // Destructor: Frees all transaction nodes
    ~BankAccount() {
        Transaction* current = historyHead;
        while (current) {
            Transaction* temp = current;
            current = current->next;
            delete temp;
        }
    }

    // Deposit money and add to history
    void deposit(double amount, std::string date) {
        balance += amount;
        addTransaction("Deposit", amount, date);
        std::cout << "Deposited $" << amount << " on " << date << ". New balance: $" << balance << std::endl;
    }

    // Withdraw money (if sufficient balance) and add to history
    void withdraw(double amount, std::string date) {
        if (amount > balance) {
            std::cout << "Insufficient balance. Cannot withdraw $" << amount << "." << std::endl;
            return;
        }
        balance -= amount;
        addTransaction("Withdraw", amount, date);
        std::cout << "Withdrew $" << amount << " on " << date << ". New balance: $" << balance << std::endl;
    }

    // Show transaction history
    void showHistory() const {
        if (!historyHead) {
            std::cout << "No transactions for account " << accountNo << "." << std::endl;
            return;
        }
        Transaction* current = historyHead;
        std::cout << "Transaction History for " << holderName << " (Account " << accountNo << "):" << std::endl;
        while (current) {
            std::cout << current->type << " $" << current->amount << " on " << current->date << std::endl;
            current = current->next;
        }
    }

    // Show current balance
    void showBalance() const {
        std::cout << "Account " << accountNo << " (" << holderName << ") Balance: $" << balance << std::endl;
    }

    // Getters for searching
    int getAccountNo() const { return accountNo; }
    std::string getHolderName() const { return holderName; }

private:
    // Helper to add a transaction to the history list
    void addTransaction(std::string type, double amount, std::string date) {
        Transaction* newTrans = new Transaction{type, amount, date, nullptr};
        if (!historyHead) {
            historyHead = newTrans;
        } else {
            Transaction* current = historyHead;
            while (current->next) {
                current = current->next;
            }
            current->next = newTrans;
        }
    }
};

int main() {
    const int NUM_ACCOUNTS = 3;
    BankAccount** accounts = new BankAccount*[NUM_ACCOUNTS];

    // Create accounts
    accounts[0] = new BankAccount(1001, "Alice", 1000.0);
    accounts[1] = new BankAccount(1002, "Bob", 500.0);
    accounts[2] = new BankAccount(1003, "Charlie", 2000.0);

    // Perform operations on accounts
    accounts[0]->deposit(500.0, "2023-10-01");
    accounts[0]->withdraw(200.0, "2023-10-02");
    accounts[1]->withdraw(600.0, "2023-10-03");  // Insufficient balance
    accounts[2]->deposit(1000.0, "2023-10-04");

    // Show balances
    for (int i = 0; i < NUM_ACCOUNTS; ++i) {
        accounts[i]->showBalance();
    }

    // Show history for one account
    accounts[0]->showHistory();

    // Search for an account by number
    int searchAcc = 1002;
    bool found = false;
    for (int i = 0; i < NUM_ACCOUNTS; ++i) {
        if (accounts[i]->getAccountNo() == searchAcc) {
            std::cout << "Found account: " << accounts[i]->getHolderName() << std::endl;
            accounts[i]->showHistory();
            found = true;
            break;
        }
    }
    if (!found) {
        std::cout << "Account " << searchAcc << " not found." << std::endl;
    }

    // Free memory: Delete each account (destructor handles transactions), then the array
    for (int i = 0; i < NUM_ACCOUNTS; ++i) {
        delete accounts[i];
    }
    delete[] accounts;

    return 0;
}
```
INPUT/OUTPUT
```
Deposited $500.00 on 2023-10-01. New balance: $1500.00
Withdrew $200.00 on 2023-10-02. New balance: $1300.00
Insufficient balance. Cannot withdraw $600.00.
Deposited $1000.00 on 2023-10-04. New balance: $3000.00
Account 1001 (Alice) Balance: $1300.00
Account 1002 (Bob) Balance: $500.00
Account 1003 (Charlie) Balance: $3000.00
Transaction History for Alice (Account 1001):
Deposit $500.00 on 2023-10-01
Withdraw $200.00 on 2023-10-02
Found account: Bob
Transaction History for Bob (Account 1002):
No transactions for account 1002.
```

# Student Class with Dynamic Course Registration.
```cpp
#include <iostream>
#include <string>

struct Course {
    std::string courseCode;
    std::string courseName;
    int credits;
};

class Student {
private:
    int roll;
    std::string name;
    Course* registeredCourses;
    int numCourses;
    int capacity;  // For dynamic array growth

public:
    // Constructor: Initializes with empty course list
    Student(int r, std::string nm) : roll(r), name(nm), numCourses(0), capacity(2) {
        registeredCourses = new Course[capacity];
    }

    // Destructor: Frees dynamic course array
    ~Student() {
        delete[] registeredCourses;
    }

    // Register courses: Input multiple courses and add to dynamic array
    void registerCourses() {
        int n;
        std::cout << "Enter number of courses to register for " << name << ": ";
        std::cin >> n;
        for (int i = 0; i < n; ++i) {
            if (numCourses == capacity) {
                // Grow array
                capacity *= 2;
                Course* newArray = new Course[capacity];
                for (int j = 0; j < numCourses; ++j) {
                    newArray[j] = registeredCourses[j];
                }
                delete[] registeredCourses;
                registeredCourses = newArray;
            }
            std::cout << "Enter course code: ";
            std::cin >> registeredCourses[numCourses].courseCode;
            std::cout << "Enter course name: ";
            std::cin.ignore();  // Handle newline
            std::getline(std::cin, registeredCourses[numCourses].courseName);
            std::cout << "Enter credits: ";
            std::cin >> registeredCourses[numCourses].credits;
            ++numCourses;
        }
    }

    // Drop a course by code
    void dropCourse(std::string code) {
        for (int i = 0; i < numCourses; ++i) {
            if (registeredCourses[i].courseCode == code) {
                // Shift elements left
                for (int j = i; j < numCourses - 1; ++j) {
                    registeredCourses[j] = registeredCourses[j + 1];
                }
                --numCourses;
                std::cout << "Dropped course: " << code << std::endl;
                return;
            }
        }
        std::cout << "Course " << code << " not found for " << name << std::endl;
    }

    // Show all registered courses
    void showCourses() const {
        std::cout << name << "'s courses:" << std::endl;
        if (numCourses == 0) {
            std::cout << "  No courses registered." << std::endl;
            return;
        }
        for (int i = 0; i < numCourses; ++i) {
            std::cout << "  " << registeredCourses[i].courseCode << " - " << registeredCourses[i].courseName
                      << " (" << registeredCourses[i].credits << " credits)" << std::endl;
        }
    }

    // Total credits
    int totalCredits() const {
        int total = 0;
        for (int i = 0; i < numCourses; ++i) {
            total += registeredCourses[i].credits;
        }
        return total;
    }

    // Check if student is registered in a course
    bool isRegisteredIn(std::string code) const {
        for (int i = 0; i < numCourses; ++i) {
            if (registeredCourses[i].courseCode == code) return true;
        }
        return false;
    }

    // Getters
    int getRoll() const { return roll; }
    std::string getName() const { return name; }
};

int main() {
    int N;
    std::cout << "Enter number of students: ";
    std::cin >> N;

    // Dynamic array of student pointers
    Student** students = new Student*[N];

    for (int i = 0; i < N; ++i) {
        int roll;
        std::string name;
        std::cout << "\nEnter roll and name for Student " << (i + 1) << ": ";
        std::cin >> roll >> name;
        students[i] = new Student(roll, name);
        students[i]->registerCourses();
    }

    // Display all students
    std::cout << "\nAll Students:" << std::endl;
    for (int i = 0; i < N; ++i) {
        students[i]->showCourses();
        std::cout << "Total Credits: " << students[i]->totalCredits() << std::endl;
        std::cout << "-------------------" << std::endl;
    }

    // Print students registered in a given course
    std::string courseCode;
    std::cout << "Enter course code to list registered students: ";
    std::cin >> courseCode;
    std::cout << "Students registered in " << courseCode << ":" << std::endl;
    bool found = false;
    for (int i = 0; i < N; ++i) {
        if (students[i]->isRegisteredIn(courseCode)) {
            std::cout << "  " << students[i]->getName() << " (Roll: " << students[i]->getRoll() << ")" << std::endl;
            found = true;
        }
    }
    if (!found) {
        std::cout << "  No students registered." << std::endl;
    }

    // Free memory
    for (int i = 0; i < N; ++i) {
        delete students[i];
    }
    delete[] students;

    return 0;
}
```
INPUT/OUTPUT
```
Enter number of students: 2

Enter roll and name for Student 1: 1 JAIRAJ
Enter number of courses to register for JAIRAJ: 2
Enter course code: 25570063
Enter course name: ENGLISH HONS
Enter credits: 5
Enter course code: MA102
Enter course name: Calculus
Enter credits: 8

Enter roll and name for Student 2: 2 PANSHUL
Enter number of courses to register for PANSHUL: 3
Enter course code: CS101
Enter course name: Programming Fundamentals
Enter credits: 6
Enter course code: PH103
Enter course name: Physics
Enter credits: 6
Enter course code: EN104
Enter course name: English
Enter credits: 4

All Students:
JAIRAJ's courses:
  25570063 - ENGLISH HONS (5 credits)
  MA102 - Calculus (8 credits)
Total Credits: 13
-------------------
PANSHUL's courses:
  CS101 - Programming Fundamentals (6 credits)
  PH103 - Physics (6 credits)
  EN104 - English (4 credits)
Total Credits: 16
-------------------
Enter course code to list registered students: CS101
Students registered in CS101:
  PANSHUL (Roll: 2)
```

# Create a struct DirNode: 
string name; bool isFile;
DirNode* child; DirNode*
sibling;Create a class DirectoryTree:
createFolder(path), createFile(path)
list(path)
deleteNode(path)
Implement using pointers (tree navigation) and free memory in destructor.
```cpp
#include <iostream>
#include <sstream>
#include <vector>
using namespace std;

struct DirNode {
    string name;
    bool isFile;
    DirNode* child;
    DirNode* sibling;

    DirNode(string n, bool f) : name(n), isFile(f), child(nullptr), sibling(nullptr) {}
};

class DirectoryTree {
private:
    DirNode* root;

    // split path
    vector<string> split(const string& path) {
        vector<string> parts;
        string temp;
        stringstream ss(path);
        while (getline(ss, temp, '/')) {
            if (!temp.empty())
                parts.push_back(temp);
        }
        return parts;
    }

    // find child by name
    DirNode* findChild(DirNode* parent, const string& name) {
        DirNode* cur = parent->child;
        while (cur) {
            if (cur->name == name)
                return cur;
            cur = cur->sibling;
        }
        return nullptr;
    }

    // add child node
    DirNode* addChild(DirNode* parent, string name, bool isFile) {
        DirNode* node = new DirNode(name, isFile);
        node->sibling = parent->child;
        parent->child = node;
        return node;
    }

    // recursive delete subtree
    void freeSubtree(DirNode* node) {
        if (!node) return;
        freeSubtree(node->child);
        freeSubtree(node->sibling);
        delete node;
    }

    // navigate to node by path
    DirNode* navigate(const string& path) {
        vector<string> parts = split(path);
        DirNode* cur = root;
        for (auto& p : parts) {
            cur = findChild(cur, p);
            if (!cur) return nullptr;
        }
        return cur;
    }

public:
    DirectoryTree() {
        root = new DirNode("root", false);
    }

    ~DirectoryTree() {
        freeSubtree(root);
    }

    void createFolder(string path) {
        vector<string> parts = split(path);
        DirNode* cur = root;

        for (auto& p : parts) {
            DirNode* next = findChild(cur, p);
            if (!next)
                next = addChild(cur, p, false);
            cur = next;
        }
    }

    void createFile(string path) {
        vector<string> parts = split(path);
        DirNode* cur = root;

        for (int i = 0; i < parts.size() - 1; i++) {
            DirNode* next = findChild(cur, parts[i]);
            if (!next)
                next = addChild(cur, parts[i], false);
            cur = next;
        }

        if (!findChild(cur, parts.back()))
            addChild(cur, parts.back(), true);
    }

    void list(string path) {
        DirNode* dir = (path == "/" ? root : navigate(path));
        if (!dir) {
            cout << "Path not found\n";
            return;
        }

        DirNode* cur = dir->child;
        while (cur) {
            cout << (cur->isFile ? "[F] " : "[D] ") << cur->name << endl;
            cur = cur->sibling;
        }
    }

    void deleteNode(string path) {
        vector<string> parts = split(path);
        if (parts.empty()) return;

        DirNode* parent = root;
        for (int i = 0; i < parts.size() - 1; i++) {
            parent = findChild(parent, parts[i]);
            if (!parent) return;
        }

        string target = parts.back();
        DirNode* cur = parent->child;
        DirNode* prev = nullptr;

        while (cur && cur->name != target) {
            prev = cur;
            cur = cur->sibling;
        }

        if (!cur) {
            cout << "Node not found\n";
            return;
        }

        if (prev)
            prev->sibling = cur->sibling;
        else
            parent->child = cur->sibling;

        cur->sibling = nullptr;
        freeSubtree(cur);
    }
};

int main() {
    DirectoryTree dt;

    dt.createFolder("/docs");
    dt.createFolder("/docs/projects");
    dt.createFile("/docs/projects/code.cpp");
    dt.createFile("/docs/readme.txt");

    cout << "\nList /docs:\n";
    dt.list("/docs");

    dt.deleteNode("/docs/readme.txt");

    cout << "\nAfter delete:\n";
    dt.list("/docs");

    return 0;
}
```
INPUT/OUTPUT
```
List /docs:
[D] projects
[F] readme.txt

After delete:
[D] projects
```
