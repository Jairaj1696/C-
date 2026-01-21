# C++ CODES 
1.// Online C++ compiler to run C++ program online
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
