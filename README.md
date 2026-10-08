# c-project
#include <iostream>
#include <string>
using namespace std;

class Supplier
{
public:
    int id, quantity;
    string name, phone, product;
    float price;

    void input()
    {
        cout << "\nSupplier ID: ";
        cin >> id;
        cin.ignore();

        cout << "Supplier Name: ";
        getline(cin, name);

        cout << "Phone: ";
        getline(cin, phone);

        cout << "Product: ";
        getline(cin, product);

        cout << "Price: ";
        cin >> price;

        cout << "Quantity: ";
        cin >> quantity;
    }

    void show()
    {
        cout << "\nID: " << id;
        cout << "\nName: " << name;
        cout << "\nPhone: " << phone;
        cout << "\nProduct: " << product;
        cout << "\nPrice: " << price;
        cout << "\nQuantity: " << quantity;
        cout << "\nTotal: " << price * quantity << "\n";
    }
};

int main()
{
    Supplier s[20];
    int n = 0, choice, id;

    do
    {
        cout << "\n\n===== SUPPLIER MANAGEMENT =====";
        cout << "\n1. Add Supplier";
        cout << "\n2. Show Suppliers";
        cout << "\n3. Search Supplier";
        cout << "\n4. Delete Supplier";
        cout << "\n5. Exit";
        cout << "\nEnter choice: ";
        cin >> choice;

        if(choice == 1)
        {
            if(n < 20)
            {
                s[n].input();
                n++;
                cout << "\nSupplier added successfully!";
            }
            else
                cout << "\nSupplier limit reached!";
        }

        else if(choice == 2)
        {
            if(n == 0)
                cout << "\nNo suppliers found.";
            else
                for(int i = 0; i < n; i++)
                    s[i].show();
        }

        else if(choice == 3)
        {
            bool found = false;
            cout << "\nEnter Supplier ID: ";
            cin >> id;

            for(int i = 0; i < n; i++)
            {
                if(s[i].id == id)
                {
                    s[i].show();
                    found = true;
                    break;
                }
            }

            if(!found)
                cout << "\nSupplier not found.";
        }

        else if(choice == 4)
        {
            bool found = false;
            cout << "\nEnter Supplier ID: ";
            cin >> id;

            for(int i = 0; i < n; i++)
            {
                if(s[i].id == id)
                {
                    for(int j = i; j < n - 1; j++)
                        s[j] = s[j + 1];

                    n--;
                    found = true;
                    cout << "\nSupplier deleted!";
                    break;
                }
            }

            if(!found)
                cout << "\nSupplier not found.";
        }

        else if(choice == 5)
            cout << "\nThank you!";

        else
            cout << "\nInvalid choice!";

    } while(choice != 5);

    return 0;
}
