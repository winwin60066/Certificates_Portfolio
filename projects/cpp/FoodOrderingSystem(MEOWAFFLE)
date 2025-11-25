#include <iostream> 
#include <iomanip>
#include <string>
#include <ctime>
#include <map>
using namespace std;

double batterPrice[3] = { 4.00, 4.50, 4.50 };
string paymentMethod[5] = { " ", "Cash", "TNG eWallet", "Debit card"," Credit card" };
int indexNumber; // For payment method
double change, cash;
int quantityOri = 0, quantityMatcha = 0, quantityCha = 0, totalQty = 0;
double totalOri = 0.00, totalMatcha = 0.00, totalCha = 0, totalPrice = 0, subtotal = 0;

// Structure class
struct Waffle { // To produce more than 1 waffle
    string batterSelected;
    string fillingSelected[2];
    int numOfFilling = 0; // For waffle index number
    double wafflePrice;
};

int OriBatter();
int MatchaBatter();
int ChaBatter();
double waffleBatter(struct Waffle* waffle, int orderIndexNumber); // OrderIndexNumber (in 1 order) = totalQty (for all order), both parameter
void waffleFilling(struct Waffle* waffle, int orderIndexNumber);
double applyDiscount(double price, double discountPercent);
void invoice(int invoiceNo, struct Waffle waffle[20], double change, double totalPrice, double subtotal, double discountValue, double servicecharge, double sst, int totalQty, int quantityOri, int quantityMatcha, int quantityCha);
void receipt(int invoiceNo, struct Waffle waffle[20], double change, double totalPrice, double subtotal, double discountValue, double servicecharge, double sst, int totalQty, double cash, double totalOri, double totalMatcha, double totalCha, int quantityOri, int quantityMatcha, int quantityCha, char returnMain);
void dReport();
void mReport();
void luckydraw();
void Qrcode();

///////

// Tng qr code
void Qrcode() {
    cout << ":-------------------------------:        .----.                          :----.   .----.   .----:   .--------------------------------.\n"
        << "=@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@*        -@@@@-                          =@@@@.   :@@@@:   :@@@@=   :@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@.\n"
        << "=@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@*        -@@@@-                          =@@@@.   :@@@@:   :@@@@=   :@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@.\n"
        << "=@@@@:                     .@@@@*   .@@@@#        -@@@@=        *@@@@.   =@@@@.   :@@@@:   :@@@@=   :@@@@+                      %@@@@.\n"
        << "=@@@@:                     .@@@@*   .@@@@#        -@@@@=        *@@@@.   =@@@@.   :@@@@:   :@@@@=   :@@@@+                      %@@@@.\n"
        << "=@@@@:   .-------------.   .@@@@*   .@@@@%--------=####-   .----*####.   =@@@@----=@@@@:   :@@@@=   :@@@@+    -------------:    %@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*   .@@@@@@@@@@@@@#        :@@@@=        =@@@@@@@@@@@@@:   :@@@@=   :@@@@+    %@@@@@@@@@@@@#    %@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*   .@@@@@@@@@@@@@#        :@@@@=        =@@@@@@@@@@@@@:   :@@@@=   :@@@@+    %@@@@@@@@@@@@#    %@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*   ...............    @@@%.....    %@@@.............%@@@@@@@@=   :@@@@+    %@@@@@@@@@@@@#    %@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*                      @@@%.        @@@@            .%@@@@@@@@=   :@@@@+    %@@@@@@@@@@@@#    %@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*        .:::::::::    +%%%#.   .::::#%%%+:::::::::::::#%%%%%%%%=   :@@@@+    %@@@@@@@@@@@@#    %@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*        -@@@@@@@@#             *@@@@.   =@@@@@@@@@@@@@:            :@@@@+    %@@@@@@@@@@@@#    %@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*        -@@@@@@@@#             *@@@@.   =@@@@@@@@@@@@@:            :@@@@+    %@@@@@@@@@@@@#    %@@@@.\n"
        << "=@@@@:   ...............   .@@@@*        -@@@@-....    *@@@@@@@@=....@@@@@@@@@....:@@@@@@@@%        :@@@@+    ..............    %@@@@.\n"
        << "=@@@@:                     .@@@@*        -@@@@-        *@@@@@@@@=    @@@@@@@@@.   :@@@@@@@@%        :@@@@+                      %@@@@.\n"
        << "=@@@@-......................@@@@*   .....-@@@@-....    *@@@@@@@@=....%@@@@@@@@.   :@@@@@@@@%.....   :@@@@+......................%@@@@.\n"
        << "=@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@*   .@@@@#    #@@@#    *@@@%.   *@@@@.   =@@@@.   :@@@@:   :@@@@=   :@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@.\n"
        << "=@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@*   .@@@@#    #@@@#    *@@@%.   *@@@@.   =@@@@.   :@@@@:   :@@@@=   :@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@.\n"
        << "                                                                     @@@@*        :@@@@@@@@%                                          \n"
        << "                                                                     @@@@*        :@@@@@@@@%                                          \n"
        << "              :::::.   ::::::::::::::    .::::.        :::::.        @@@@*::::.   :@@@@@@@@%    .::::                  :::::::::.     \n"
        << "              %@@@@.   *@@@@@@@@@@@@@    -@@@@-        *@@@%.        @@@@@@@@@.   :@@@@@@@@%    *@@@%                  %@@@@@@@@:     \n"
        << "              %@@@@.   *@@@@@@@@@@@@@    -@@@@-        *@@@%.        @@@@@@@@@.   :@@@@@@@@%    *@@@%                  %@@@@@@@@:     \n"
        << "         -@@@@@@@@@.                     -@@@@@@@@#    @@@%.        @@@@            .%@@@@@@@@=   :@@@@+    %@@@*                   \n"
        << "         -@@@@@@@@@.                     -@@@@@@@@#    @@@%.        @@@@            .%@@@@@@@@=   :@@@@+    %@@@*                   \n"
        << "         -@@@@@@@@@.   :--------:   .----+@@@@%###----#@@@%.   :----@@@@---------   .%@@@@####+----####=    %@@@*-------------.     \n"
        << "         -@@@@@@@@@.   @@@@@@@@   .@@@@@@@@@-   -@@@@@@@@%.   *@@@@@@@@@@@@@@@@@%   .%@@@%    *@@@%         %@@@@@@@@@@@@@@@@@:     \n"
        << "         -@@@@@@@@@.   @@@@@@@@   .@@@@@@@@@-   -@@@@@@@@%.   *@@@@@@@@@@@@@@@@@%   .%@@@%    *@@@%         %@@@@@@@@@@@@@@@@@:     \n"
        << "     %@@@#    %@@@@@@@@=        =@@@@@@@@#                                        :@@@@@@@@%        :@@@@+        =@@@@@@@@#    %@@@@.\n"
        << "     %@@@#    %@@@@@@@@=        =@@@@@@@@#                                        :@@@@@@@@%        :@@@@+        =@@@@@@@@#    %@@@@.\n"
        << ":----###----########-   .----+@@@@####+    :--------.   .---------.   :----.   :@@@@####----.   .####+----.   -########+    *####.\n"
        << "=@@@@:   -@@@@:            .@@@@@@@@@         #@@@@@@@@=   :@@@@@@@@@.   =@@@@.   :@@@@:   :@@@@=        +@@@@:                       \n"
        << "=@@@@:   -@@@@:            .@@@@@@@@@         #@@@@@@@@=   :@@@@@@@@@.   =@@@@.   :@@@@:   :@@@@=        +@@@@:                       \n"
        << "         -@@@@:    @@@@=            .@@@@#        -@@@@@@@@@@@@@@@@@@@@@@*            .%@@@@@@@@@@@@%         %@@@*             %@@@@.\n"
        << "         -@@@@:    @@@@=            .@@@@#        -@@@@@@@@@@@@@@@@@@@@@@*            .%@@@@@@@@@@@@%         %@@@*             %@@@@.\n"
        << "         -@@@@:    #%%%-   .----:   .@@@@#----.   :%%%%@@@@@@@@@%%%%%#%%%+----:---:----#%%%#%%%%#%%%#----:    #%%%+        .----#%%%%.\n"
        << "         -@@@@:            .@@@@*   .@@@@@@@@@-        *@@@@@@@@=        =@@@@@@@@@@@@@:            :@@@@+                 -@@@@:     \n"
        << "         -@@@@:            .@@@@*   .@@@@@@@@@-        *@@@@@@@@=        =@@@@@@@@@@@@@:            :@@@@+                 -@@@@:     \n"
        << "     #@@@@@@@@@@@@@@@@@-   .....=@@@@@@@@#.....   -@@@@@@@@%....@@@@@@@@........:@@@@:   :@@@@@@@@@@@@@@@@@@@@@@+        -@@@@:     \n"
        << "     %@@@@@@@@@@@@@@@@@=        =@@@@@@@@#        -@@@@@@@@%.   @@@@@@@@        :@@@@:   :@@@@@@@@@@@@@@@@@@@@@@*        -@@@@:     \n"
        << ".....%@@@@@@@@@@@@@%@@@=........+@@@@@@@@*    ....-@@@@%@@@%:...@@@@@@@@+        :@@@%:   :@@@@@@@@@@@@@%@@@@@@@@........-@@@@:.....\n"
        << "=@@@@@@@@@@@@@@@@@@.   *@@@@@@@@@@@@@         #@@@#        :@@@@@@@@@.                     :@@@@@@@@%         %@@@@@@@@@@@@@@@@@@@@@@.\n"
        << "=@@@@@@@@@@@@@@@@@@.   *@@@@@@@@@@@@@         #@@@#        :@@@@@@@@@.                     :@@@@@@@@%         %@@@@@@@@@@@@@@@@@@@@@@.\n"
        << ".........-@@@@@@@@@@@@@=.............@@@@#    #@@@#        :@@@@=....@@@@@@@@@.            .........:@@@@+    %@@@@@@@@:..............\n"
        << "         -@@@@@@@@@@@@@=            .@@@@#    #@@@#        :@@@@=    @@@@@@@@@.                     :@@@@+    %@@@@@@@@:              \n"
        << ".........-@@@@@@@@@@@@@-   ..........@@@@#....#@@@#.....   :@@@@=    %@@@@@@@@.   ......   ......   :@@@@+....%@@@@@@@@:              \n"
        << "=@@@@@@@@#    %@@@@.       .@@@@@@@@@@@@@@@@@@@@@@@@@@@=   :@@@@=                 :@@@@:   :@@@@=   :@@@@@@@@@@@@@@@@@@:              \n"
        << "=@@@@@@@@#    %@@@@.       .@@@@@@@@@@@@@@@@@@@@@@@@@@@=   :@@@@=                 :@@@@:   :@@@@=   :@@@@@@@@@@@@@@@@@@:              \n"
        << "=@@@@@@@@#    %@@@@.                .@@@@#    #@@@@@@@@@@@@@@@@@@@@@@.            :@@@@@@@@%             +@@@@@@@@@@@@@:              \n"
        << "=@@@@@@@@#    %@@@@.                .@@@@#    #@@@@@@@@@@@@@@@@@@@@@@.            :@@@@@@@@%             +@@@@@@@@@@@@@:              \n"
        << "=%%%%%%%%*    #%%%%::::::::::::::::::@@@@#    %%%%%%%%@@@@@@@@@%%%%%-::::::::::::-@@@@%%%%#:::::::::::::@@@@@@@@@@@@@:   .:::::::::.\n"
        << "                   @@@@@@@@@@@@@@@@@@@@@@#             *@@@@@@@@=    @@@@@@@@@@@@@@@@@@:   :@@@@@@@@@@@@@@@@@@@@@@@@@@@:   -@@@@@@@@@.\n"
        << "                   @@@@@@@@@@@@@@@@@@@@@@#             *@@@@@@@@=    @@@@@@@@@@@@@@@@@@:   :@@@@@@@@@@@@@@@@@@@@@@@@@@@:   -@@@@@@@@@.\n"
        << "                                              #@@@#    @@@%.   *@@@@.        @@@@%   .%@@@@@@@@=             %@@@    %@@@#          \n"
        << "                                              #@@@#    @@@%.   *@@@@.        @@@@%   .%@@@@@@@@=             %@@@    %@@@#          \n"
        << ".-------------------------------:   .----:    ###----#@@@%----#@@@@---------####*   .%@@@@@@@@=   .----:    %@@@*    ###          \n"
        << "=@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@*   .@@@@#        -@@@@@@@@@@@@@@@@@@@@@@@@@@@.       .%@@@@@@@@=   :@@@@+    %@@@*                   \n"
        << "=@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@*   .@@@@#        -@@@@@@@@@@@@@@@@@@@@@@@@@@@.       .%@@@@@@@@=   :@@@@+    %@@@*                   \n"
        << "=@@@@:                     .@@@@*   .@@@@@@@@@-   -@@@@=                 =@@@@@@@@%        :@@@@=             %@@@@@@@@:        %@@@@.\n"
        << "=@@@@:                     .@@@@*   .@@@@@@@@@-   -@@@@=                 =@@@@@@@@%        :@@@@=             %@@@@@@@@:        %@@@@.\n"
        << "=@@@@:   .-------------.   .@@@@*   .#########:   :####-                 =@@@@####*   .:---=@@@@+-------------@@@@@@@@@=---:    %@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*                                        =@@@@.       .%@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#    %@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*                                        =@@@@.       .%@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#    %@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*   .@@@@@@@@@-   -@@@@@@@@@@@@@@@@@@@@@@*....@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@:...=@@@@:...-@@@@@@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*   .@@@@@@@@@-   -@@@@@@@@@@@@@@@@@@@@@@*    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@:   =@@@@:   -@@@@@@@@@.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*   .%%%%%@@@@-   :%%%%@@@@@%%%%@@@@@%%%%+    @@@@@%%%%%%%%%@@@@%%%%%@@@@%%%%%.   =@@@@:   :%%%%%%%%%.\n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*        -@@@@-        *@@@%.   *@@@@.        @@@@%        :@@@@=   :@@@@+        =@@@@:              \n"
        << "=@@@@:   -@@@@@@@@@@@@@=   .@@@@*        -@@@@-        *@@@%.   *@@@@.        @@@@%        :@@@@=   :@@@@+        =@@@@:              \n"
        << "=@@@@:   ...............   .@@@@*        -@@@@-        *@@@%.   *@@@@@@@@+    .....        :@@@@=   .....+@@@@.   =@@@@@@@@#          \n"
        << "=@@@@:                     .@@@@*        -@@@@-        @@@%.   *@@@@@@@@                 :@@@@=        +@@@@:   =@@@@@@@@#          \n"
        << "=@@@@-......................@@@@*        -@@@@-....    @@@%....@@@@@@@@+    .............:@@@@=........+@@@@:   =@@@@@@@@#    ......\n"
        << "=@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@*        -@@@@@@@@#        :@@@@@@@@@.        @@@@@@@@@@@@@%    *@@@@@@@@@@@@@:        %@@@#    %@@@@.\n"
        << "=@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@*        -@@@@@@@@#        :@@@@@@@@@.        @@@@@@@@@@@@@%    *@@@@@@@@@@@@@:        %@@@#    %@@@@.\n"
        << ".................................        ..........        ...........        ..............    ...............        .....    ......\n";
}

// Quantity for batter(qty plus when customer decide to continue next order)
int OriBatter() {
    quantityOri += 1;
    return quantityOri;
}
int MatchaBatter() {
    quantityMatcha += 1;
    return quantityMatcha;
}
int ChaBatter() {
    quantityCha += 1;
    return quantityCha;
}

// Choose waffle batter
double waffleBatter(struct Waffle* waffle, int orderIndexNumber) {  //2nd step, jump from int main();
    int batter;
    string batterFlavour[3] = { "Original", "Matcha", "Charcoal" };
    double batterPrice[3] = { 4.00,4.50,4.50 };

    // Clear screen after selected 'Waffle Menu' from main menu
    system("CLS");

    // Display Menu table for Batter
    cout << "\nWaffle Batter Menu ^o.o^" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(9) << "+" << setw(1) << "+" << endl;
    cout << left << setfill(' ') << setw(5) << "|Bil" << setw(15) << "|Waffle Batter" << setw(9) << "|Price" << "|" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(9) << "+" << setw(1) << "+" << endl;
    cout << left << setfill(' ') << setw(5) << "|1." << setw(15) << "|Original" << setw(9) << "|RM 4.00" << "|" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(9) << "+" << setw(1) << "+" << endl;
    cout << left << setfill(' ') << setw(5) << "|2." << setw(15) << "|Matcha" << setw(9) << "|RM 4.50" << "|" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(9) << "+" << setw(1) << "+" << endl;
    cout << left << setfill(' ') << setw(5) << "|3." << setw(15) << "|Charcoal" << setw(9) << "|RM 4.50" << "|" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(9) << "+" << setw(1) << "+" << endl;

    // Ask for placing order
    cout << "\nEnter your option's number: ";
    cin >> batter;
    // If Invalid order
    while (batter < 1 || batter > 3) {
        cout << "\nInvalid, please enter again! ^>.<^\n";
        cout << "\nEnter your option's number: ";
        cin >> batter;
    }
    // batterFlavour[batter - 1] = batterFlavour[1//2//3] = which flavour
    // The .batterSelected = to name what batter under the first order of waffle
    waffle[orderIndexNumber].batterSelected = batterFlavour[batter - 1];

    // Display chosen batter
    cout << "\nWaffle Batter Flavor > ";
    cout << batterFlavour[batter - 1] << "!^o.o^ \n"; //Array start with 0

    // The .batterPrice = to put the price of the batter under the first order of waffle
    waffle[orderIndexNumber].wafflePrice = batterPrice[batter - 1];

    // Function to increase 1 for the batter selected
    if (batterFlavour[batter - 1] == batterFlavour[0]) {
        OriBatter();
    }
    else if (batterFlavour[batter - 1] == batterFlavour[1]) {
        MatchaBatter();
    }
    else if (batterFlavour[batter - 1] == batterFlavour[2]) {
        ChaBatter();
    }

    // Enter to choose filling
    waffleFilling(waffle, orderIndexNumber);

    // Return value of price to main = for calculation for subtotal
    return batterPrice[batter - 1];
}
// Choose filling + pass value (name of filling)
void waffleFilling(struct Waffle* waffle, int orderIndexNumber) {
    int filling; //action to choose which filling
    char askFilling; //ask for second filling
    string fillingFlavour[5] = { "Chocolate", "Peanut", "Strawberry", "Matcha", "Butter" };


    // Display menu for filling
    cout << "\nWaffle Filling Menu ^o.o^" << endl;

    // Menu teble for filling
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(1) << "+" << endl;
    cout << left << setfill(' ') << setw(5) << "|Bil" << setw(15) << "|Waffle Filling" << "|" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(1) << "+" << endl;
    cout << left << setfill(' ') << setw(5) << "|1." << setw(15) << "|Chocolate" << "|" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(1) << "+" << endl;
    cout << left << setfill(' ') << setw(5) << "|2." << setw(15) << "|Peanut" << "|" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(1) << "+" << endl;
    cout << left << setfill(' ') << setw(5) << "|3." << setw(15) << "|Strawberry" << "|" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(1) << "+" << endl;
    cout << left << setfill(' ') << setw(5) << "|4." << setw(15) << "|Matcha" << "|" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(1) << "+" << endl;
    cout << left << setfill(' ') << setw(5) << "|5." << setw(15) << "|Butter" << "|" << endl;
    cout << left << setfill('-') << setw(5) << "+" << setw(15) << "+" << setw(1) << "+" << endl;

    // Place order of filling for waffle
    cout << "\nEnter your first filling's number: ";
    cin >> filling;

    // Inavlid choice, re-enter until valid
    while (filling < 1 || filling > 5) {
        cout << "\nInvalid, please enter again! ^>.<^\n";
        cout << "\nEnter your first filling's number: ";
        cin >> filling;
    }
    // Display chosen flavour 
    cout << "\nWaffle Filling Flavor > ";
    cout << fillingFlavour[filling - 1] << "!^o.o^ \n";
    waffle[orderIndexNumber].fillingSelected[0] = fillingFlavour[filling - 1];
    waffle[orderIndexNumber].numOfFilling++;

    do {
        // Ask if want go on for second filing
        cout << "\nDo you want a second filling? (Y/N): ";
        cin >> askFilling;
        askFilling = toupper(askFilling);  // Convert input to uppercase

        if (askFilling == 'Y') {
            // Second filling start if yes
            do {
                // Which flavour customer want
                cout << "\nEnter your second filling's number: ";
                cin >> filling;

                // Return value to main, and continue process at wafflerBatter(); (4th step)
                if (filling < 1 || filling > 5) {
                    //Invalid choice
                    cout << "\nInvalid choice, please enter again! ^>.<^" << endl;
                }
                else {
                    waffle[orderIndexNumber].fillingSelected[1] = fillingFlavour[filling - 1];
                    waffle[orderIndexNumber].numOfFilling++;
                    cout << "\nWaffle Filling Flavor > " << fillingFlavour[filling - 1] << "! ^>.o^ " << endl;
                }
            } while (filling < 1 || filling > 5); // Repeat until valid input
        }
        else if (askFilling == 'N') {
            break; // Exit loop
        }
        else {
            cout << "\nInvalid input, please enter again! ^>.<^" << endl;
        }
    } while (askFilling != 'N' && askFilling != 'Y'); // If not N or Y loop until get one of them

    // Display conclusion what you order for filling
    if (waffle[orderIndexNumber].numOfFilling == 1) { // Display 1 filling flavour
        cout << "\nYour chosen waffle filling is " << waffle[orderIndexNumber].fillingSelected[0];
    }
    else { // Display 2 filling flavour
        cout << "\nYour chosen waffle filling is " << waffle[orderIndexNumber].fillingSelected[0] << " and " << waffle[orderIndexNumber].fillingSelected[1];
    }
    cout << "! Enjoy! ^>.o^ \n";
}
// For promocode
double applyDiscount(double price, double discountPercent) {
    double discountValue = price * discountPercent / 100; \
        return discountValue;
}

void invoice(int invoiceNo, struct Waffle waffle[20], double change, double totalPrice, double subtotal, double discountValue, double servicecharge, double sst, int totalQty, int quantityOri, int quantityMatcha, int quantityCha) {
    srand(time(NULL));
    invoiceNo = rand() % 1000 + 20000; // Random invoice number

    // Header
    cout << setw(67) << setfill('*') << "" << endl;
    cout << setw(34) << setfill(' ') << right << "MEOWAFFLE" << setw(31) << "" << right << endl;
    cout << setw(47) << setfill(' ') << right << "JALAN GENTING KLANG, SETAPAK, 53300" << setw(18) << "" << right << endl;
    cout << setw(46) << setfill(' ') << right << "WILAYAH PERSEKUTUAN KUALA LUMPUR" << setw(19) << "" << right << endl;
    cout << setw(39) << setfill(' ') << right << "TEL: 03 - 12345678" << setw(26) << "" << right << endl;
    cout << setw(65) << setfill(' ') << "" << endl;
    cout << setw(67) << setfill('*') << "" << endl;
    cout << setfill(' ') << "Invoice No: " << invoiceNo << setw(48) << right << __DATE__ << endl;

    // Customer order details
    for (int i = 0; i < totalQty; i++) { // Display batter and filling, totalQty = total ordered
        if (waffle[i].numOfFilling == 1) { // Display 1 filling 
            cout << setw(2) << (i + 1) << ". " << left << setw(10) << waffle[i].batterSelected
                << "(" << waffle[i].fillingSelected[0] << ")" << setw(37) << right
                << "RM " << setw(4) << fixed << setprecision(2) << waffle[i].wafflePrice << endl;
        }
        else { // Display 2 filling
            cout << setw(2) << (i + 1) << ". " << left << setw(10) << waffle[i].batterSelected
                << "(" << waffle[i].fillingSelected[0] << " + " << waffle[i].fillingSelected[1] << ")"
                << setw(23) << right << "RM " << setw(4) << fixed << setprecision(2) << waffle[i].wafflePrice << endl;
        }
    }
    // Subtotal and charges
    cout << setw(67) << setfill('*') << "" << endl;
    cout << setfill(' ') << "Subtotal" << setw(53) << right << "RM " << setw(4) << fixed << setprecision(2) << subtotal << endl;
    cout << "Discount" << setw(53) << right << "- RM " << setw(4) << fixed << setprecision(2) << discountValue << endl;
    cout << "Service Charge (5%)" << setw(42) << right << "+ RM " << setw(4) << fixed << setprecision(2) << servicecharge << endl;
    cout << "Tax (SST 8%)" << setw(49) << right << "+ RM " << setw(4) << fixed << setprecision(2) << sst << endl;

    // Total payable
    cout << setw(67) << setfill('*') << "" << endl;
    cout << setfill(' ') << "Total item(s): " << totalQty << endl;
    cout << "Total payable: " << setw(46) << right << "RM " << setw(4) << fixed << setprecision(2) << totalPrice << endl;
    cout << setw(67) << setfill('*') << "" << endl;
}

void receipt(int invoiceNo, struct Waffle waffle[20], double change, double totalPrice, double subtotal, double discountValue, double servicecharge, double sst, int totalQty, double cash, double totalOri, double totalMatcha, double totalCha, int quantityOri, int quantityMatcha, int quantityCha, char returnMain) {//get parameter from int main//waffleBatter();
    srand(time(NULL)); // Use the current time as the seed for random number generation to ensure different results on each run
    invoiceNo = rand() % 1000 + 20000; // Random invoice number
    // Header
    cout << "\n" << setw(67) << setfill('*') << "" << endl;
    cout << setw(34) << setfill(' ') << right << "MEOWAFFLE" << setw(31) << "" << right << endl;
    cout << setw(47) << setfill(' ') << right << "JALAN GENTING KLANG, SETAPAK, 53300" << setw(18) << "" << right << endl;
    cout << setw(46) << setfill(' ') << right << "WILAYAH PERSEKUTUAN KUALA LUMPUR" << setw(19) << "" << right << endl;
    cout << setw(39) << setfill(' ') << right << "TEL: 03 - 12345678" << setw(26) << "" << right << endl;
    cout << setw(65) << setfill(' ') << "" << endl;
    cout << setw(67) << setfill('*') << "" << endl;
    cout << setfill(' ') << "Invoice No: " << invoiceNo << setw(48) << right << __DATE__ << endl;
    // Customer order details
    for (int i = 0; i < totalQty; i++) {  // Display batter and filling
        if (waffle[i].numOfFilling == 1) { // Display 1 filling
            cout << setw(2) << (i + 1) << ". " << left << setw(10) << waffle[i].batterSelected
                << "(" << waffle[i].fillingSelected[0] << ")" << setw(37) << right
                << "RM " << setw(4) << fixed << setprecision(2) << waffle[i].wafflePrice << endl;
        }
        else { // Display 2 filling
            cout << setw(2) << (i + 1) << ". " << left << setw(10) << waffle[i].batterSelected
                << "(" << waffle[i].fillingSelected[0] << " + " << waffle[i].fillingSelected[1] << ")"
                << setw(23) << right << "RM " << setw(4) << fixed << setprecision(2) << waffle[i].wafflePrice << endl;
        }
    }
    // Subtotal and charges
    cout << setw(67) << setfill('*') << "" << endl;
    cout << setfill(' ') << "Subtotal" << setw(53) << right << "RM " << setw(4) << fixed << setprecision(2) << subtotal << endl;
    cout << "Discount" << setw(53) << right << "- RM " << setw(4) << fixed << setprecision(2) << discountValue << endl;
    cout << "Service Charge (5%)" << setw(42) << right << "+ RM " << setw(4) << fixed << setprecision(2) << servicecharge << endl;
    cout << "Tax (SST 8%)" << setw(49) << right << "+ RM " << setw(4) << fixed << setprecision(2) << sst << endl;
    // Total payable
    cout << setw(67) << setfill('*') << "" << endl;
    cout << setfill(' ') << "Total item(s): " << totalQty << endl;
    cout << "Total payable: " << setw(46) << right << "RM " << setw(4) << fixed << setprecision(2) << totalPrice << endl;
    cout << setw(67) << setfill('*') << "" << endl;
    // Payment method chosen just now
    cout << setfill(' ') << setw(18) << "Payment method\t\t: " << paymentMethod[indexNumber] << setw(36) << endl;

    if (paymentMethod[indexNumber] == "Cash") {
        cout << setw(14) << "Payment amount\t\t: RM " << setw(5) << fixed << setprecision(2) << cash << setw(29) << endl;
        cout << setw(14) << "Change\t\t\t: RM " << setw(5) << fixed << setprecision(2) << change << setw(29) << endl;
    }
    else {
        cout << setw(22) << "Payment amount\t\t: RM " << setw(5) << fixed << setprecision(2) << totalPrice << setw(29) << endl;
        cout << setw(15) << "Change\t\t\t: RM 0.00" << setw(26) << endl;
    }
    cout << setw(67) << setfill('*') << "" << endl;
}
// Lucky draw
void luckydraw() {
    char luckydraw, confirm;
    int luckynum;
    srand(time(NULL)); // Create a random seed
    do {
        cout << "\nWould you like to play a lucky draw? (Y/N) > ";
        cin >> luckydraw;
        luckydraw = toupper(luckydraw);
        if (luckydraw == 'Y') {
            system("CLS");
            cout << "Rules of play:\n1. Enter a number between (1 - 10) you guess.\n2. After entering the number, the system will display a random number.\n3. If your number is the same as the system's number > Congrats! You can redeem a Meowaffle keychain/a free waffle at the counter!^>.o^\n";
            cout << "4. If your number is not the same as the system's number > Thanks for joining us! Orz\n";
            do {
                cout << "\nAre you ready? (Y/N) > ";
                cin >> confirm;
                confirm = toupper(confirm);
                if (confirm == 'Y') {
                    do {
                        cout << "\nEnter your lucky number > ";
                        cin >> luckynum;
                        int systemNumber = rand() % 10 + 1; // Create a random number between 0 and 10 as system number
                        if (luckynum < 1 || luckynum > 11) {
                            cout << "\nOnly enter number between 1 - 10! Please enter again! ^>.<^\n";
                        }
                        else if (luckynum == systemNumber) { // Lucky
                            cout << "\nSystem number: " << systemNumber << endl;
                            cout << "\nCongratulations! You can redeem a Meowaffle keychain/a waffle at the counter! ^>.o^";
                        }
                        else {
                            cout << "\nSystem number: " << systemNumber << endl; // Unlucky
                            cout << "\nThanks for purchasing at MEOWAFFLE! See you next time! ^o.o^\n";
                        }
                    } while (luckynum < 1 || luckynum > 11);
                }
                else if (confirm == 'N') {
                    cout << "\nTake a breath! ^o.o^\n";
                }
                else if (confirm != 'Y' && confirm != 'N') { // Invalid
                    cout << "\nInvalid input, please enter again.^>.<^\n";
                }
            } while (confirm != 'Y'); // Continue asking if the customer is ready(Y)
        }
        else if (luckydraw == 'N') {
            cout << "Thanks for purchasing at MEOWAFFLE! See you next time! ^o.o^\n";
        }
        else if (luckydraw != 'Y' && luckydraw != 'N') { // Invalid
            cout << "\nInvalid input, please enter again! ^>.<^\n\n";
        }
    } while (luckydraw != 'Y' && luckydraw != 'N');
}

// Daily report
void dReport() {
    const double priceWaffle[3] = { 4.00,4.50,4.50 };
    double totalOri = quantityOri * priceWaffle[0]; // Quantity is use for the user input, quanty is use for random number
    double totalMatcha = quantityMatcha * priceWaffle[1];
    double totalCha = quantityCha * priceWaffle[2];

    cout << "\nMEOWAFFLE's DAILY REPORTS ^o.o^" << endl;
    // Display header and the report table
    cout << '+' << setfill('-') << setw(9);
    cout << '+' << setfill('-') << setw(21);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(12) << "" << '+' << endl;
    cout << '|' << left << setfill(' ') << setw(8) << "Bill";
    cout << '|' << setw(20) << "Waffle";
    cout << '|' << setw(12) << "Quantity";
    cout << '|' << setw(12) << "Unit Price";
    cout << '|' << setw(12) << "Total" << "|" << endl;
    cout << right << '+' << setfill('-') << setw(9);
    cout << '+' << setfill('-') << setw(21);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << endl;
    // Original
    cout << left << '|' << setfill(' ') << setw(8) << "1.";
    cout << '|' << setfill(' ') << setw(20) << "Original";
    cout << '|' << setfill(' ') << setw(12) << quantityOri;
    cout << '|' << setfill(' ') << setw(12) << fixed << setprecision(2) << priceWaffle[0];
    cout << '|' << setfill(' ') << "RM " << fixed << setprecision(2) << setw(9) << totalOri << '|' << endl;
    // Matcha
    cout << left << '|' << setfill(' ') << setw(8) << "2.";
    cout << '|' << setfill(' ') << setw(20) << "Matcha";
    cout << '|' << setfill(' ') << setw(12) << quantityMatcha;
    cout << '|' << setfill(' ') << setw(12) << priceWaffle[1];
    cout << '|' << setfill(' ') << "RM " << fixed << setprecision(2) << setw(9) << quantityMatcha << '|' << endl;
    // Charcoal
    cout << left << '|' << setfill(' ') << setw(8) << "3.";
    cout << '|' << setfill(' ') << setw(20) << "Charcoal";
    cout << '|' << setfill(' ') << setw(12) << quantityCha;
    cout << '|' << setfill(' ') << setw(12) << priceWaffle[2];
    cout << '|' << setfill(' ') << "RM " << fixed << setprecision(2) << setw(9) << quantityCha << '|' << endl;

    cout << right << '+' << setfill('-') << setw(9);
    cout << '+' << setfill('-') << setw(21);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << endl;

    // Total Price
    double totalPrice = totalOri + totalMatcha + totalCha; // Total price calculation
    cout << '|' << left << setfill(' ') << setw(52) << "Total Price > ";
    cout << setw(12) << right << "RM " << setw(3) << fixed << setprecision(2) << totalPrice << setw(1) << '|' << endl;
    cout << right << setw(70) << setfill('-') << '+';
}

// Monthly report
void mReport() {
    const double priceWaffle[3] = { 4.00,4.50,4.50 };
    srand(time(NULL)); // Use the current time as the seed for random number generation to ensure different results on each run

    // Provide random number for waffle quantity
    int quantyOri = rand() % 501 + 1500; // Quanty for random number, only exist in Mreport only, quantity is used for user input
    int quantyMatcha = rand() % 501 + 1500;
    int quantyCha = rand() % 501 + 1500;
    double totalOri = quantyOri * priceWaffle[0];
    double totalMatcha = quantyMatcha * priceWaffle[1];
    double totalCha = quantyCha * priceWaffle[2];

    cout << "\nMEOWAFFLE's MONTHLY REPORTS ^o.o^" << endl;
    // Header
    cout << '+' << setfill('-') << setw(9);
    cout << '+' << setfill('-') << setw(21);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(12) << "" << '+' << endl;
    cout << '|' << left << setfill(' ') << setw(8) << "Bill";
    cout << '|' << setw(20) << "Waffle";
    cout << '|' << setw(12) << "Quantity";
    cout << '|' << setw(12) << "Unit Price";
    cout << '|' << setw(12) << "Total" << "|" << endl;
    cout << right << '+' << setfill('-') << setw(9);
    cout << '+' << setfill('-') << setw(21);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << endl;

    // Original
    cout << left << '|' << setfill(' ') << setw(8) << "1.";
    cout << '|' << setfill(' ') << setw(20) << "Original";
    cout << '|' << setfill(' ') << setw(12) << quantyOri;
    cout << '|' << setfill(' ') << setw(12) << fixed << setprecision(2) << priceWaffle[0];
    cout << '|' << setfill(' ') << "RM " << fixed << setprecision(2) << setw(9) << totalOri << '|' << endl;
    // Matcha
    cout << left << '|' << setfill(' ') << setw(8) << "2.";
    cout << '|' << setfill(' ') << setw(20) << "Matcha";
    cout << '|' << setfill(' ') << setw(12) << quantyMatcha;
    cout << '|' << setfill(' ') << setw(12) << priceWaffle[1];
    cout << '|' << setfill(' ') << "RM " << fixed << setprecision(2) << setw(9) << totalMatcha << '|' << endl;
    // Charcoal
    cout << left << '|' << setfill(' ') << setw(8) << "3.";
    cout << '|' << setfill(' ') << setw(20) << "Charcoal";
    cout << '|' << setfill(' ') << setw(12) << quantyCha;
    cout << '|' << setfill(' ') << setw(12) << priceWaffle[2];
    cout << '|' << setfill(' ') << "RM " << fixed << setprecision(2) << setw(9) << totalCha << '|' << endl;

    cout << right << '+' << setfill('-') << setw(9);
    cout << '+' << setfill('-') << setw(21);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << setfill('-') << setw(13);
    cout << '+' << endl;

    // Total Price
    double totalPrice = totalOri + totalMatcha + totalCha; // Total price calulation
    cout << '|' << left << setfill(' ') << setw(52) << "Total Price > ";
    cout << setw(8) << right << "RM " << setw(3) << fixed << setprecision(2) << totalPrice << setw(1) << '|' << endl;
    cout << right << setw(70) << setfill('-') << '+';
}

int main() {
    struct Waffle waffle[20]; // Set that Waffle got maximum 20 order
    int startopt; // For starting option
    char continueOrder; // Action
    double totalPrice = 0.00, servicecharge = 0, sst = 0, subtotal = 0; // Calculation for price
    int totalQty = 0; // The total number ordered 
    char report, feedback, returnMain = 0; // Action
    int cvv, expired, invoiceNo = 0; // Payment method
    string holder_name, credit, debit;
    do { // To let customer select to return back to here(returnMain)
        // Logo
        cout << "\n /\\_/\\       **   **  *****  *******  **             **       **        ******  ******  **        *****         /\\_/\\  " << endl;
        cout << "( o.o )      *** ***  *      *     *   **           **      **  **      *       *       **        *            ( @.@ ) " << endl;
        cout << " > ^ <       ** * **  *****  *     *    **    *    **      **    **     ******  ******  **        *****         > ^ < " << endl;
        cout << "             **   **  *      *     *     **  ***  **      **********    *       *       **        *" << endl;
        cout << "             **   **  *****  *******       *** ***       **        **   *       *       *******   *****" << endl;

        // Starting menu
        cout << "\nWelcome To Meowaffle!!! ^o.o^\n\nNow we are doing promotion! [p.s. promocode at the official website] \nIf you spend RM10 or above you can get a chance to participate lucky draw!! ^>.o^\n[REWARDS: a MEOWAFFLE keychain or a free waffle]" << endl;
        cout << "----------------------------------------------------------------------------------------" << endl;
        cout << "1.Waffle menu\n2.Reporting\n3.Exit\n\n";


        do { // Let user to purchase multi-order
            cout << "Enter a number to access the page you want! ^o.o^ > ";
            cin >> startopt;
            if (startopt == 1) {

                do {
                    subtotal += waffleBatter(waffle, totalQty); // Display batter menu 
                    totalQty++;// 1 batter waffle + 1 pr 2 filling = quantity 1(each order one waffle)
                    cout << "\nDo you want to continue order? (Y/N): "; // Ask if wanna continue order
                    cin >> continueOrder;
                    continueOrder = toupper(continueOrder); // Convert the input to uppercase

                    if (continueOrder != 'Y' && continueOrder != 'N') { // Invalid choice
                        cout << "\nInvalid input, please enter again! ^>.<^" << endl;
                        cout << "\nDo you want to continue order? (Y/N): ";
                        cin >> continueOrder;
                        continueOrder = toupper(continueOrder);
                    }
                    else if (continueOrder == 'N') {
                        cout << "\nThanks for purchasing! ^o.o^" << endl;
                    }
                } while (continueOrder == 'Y'); // If yes loop again

                cout << "\nTotal Price is " << "RM " << fixed << setprecision(2) << subtotal << endl;; //Let customer know how much money estimated have to pay
                servicecharge = subtotal * 0.05; // 5% service charge
                sst = subtotal * 0.08; // 8% sst 

                // Store promo code in map as a key
                map<string, double> promoCodelist = {
                {"CRAVIN25",25.0},
                {"MEOWMEOW50",50.0 },
                {"MATCHA10",10.0}
                };
                double discountValue, discountPercent = 0.0;
                string promoCode;
                // Ask user to key in promocode
                cout << "\n[If you don't have promocode just enter any input]\nEnter promo code: ";
                cin >> promoCode;

                if (promoCodelist.find(promoCode) != promoCodelist.end()) {
                    discountPercent = promoCodelist[promoCode];
                    cout << "\nPromo code applied!!! Discount " << discountPercent << "%." << endl;
                }
                else
                    cout << "\nInvalid promocode.No Promo code applied. ^>.<^" << endl;
                // Calculation for price after discount
                cout << "\nOriginal price: RM " << fixed << setprecision(2) << subtotal << endl;
                discountValue = applyDiscount(subtotal, discountPercent);
                cout << "\nRM " << fixed << setprecision(2) << discountValue << " has been deducted!! ^>.o^\n" << endl;
                totalPrice = subtotal + sst + servicecharge - discountValue;
                // Invoice
                invoice(invoiceNo, waffle, change, totalPrice, subtotal, discountValue, servicecharge, sst, totalQty, quantityOri, quantityMatcha, quantityCha);

                // Payment method
                cout << "\n--------------PAYMENT METHOD--------------" << endl;
                cout << "1.Cash\n2.TNG eWallet\n3.Debit card\n4.Credit card" << endl;
                cout << "Please select one of the payment method: ";
                cin >> indexNumber;

                switch (indexNumber) {
                    cout << "\nSelected payment: " << paymentMethod[indexNumber] << endl;
                case 1:
                    cout << "\nType pay in amount: RM ";
                    cin >> cash;
                    change = cash - totalPrice; // Calculate change
                    cout << "\nChange: RM " << change << endl;
                    break;
                case 2:
                    cout << "\nScan QR CODE to pay: ";
                    cout << "\n";
                    Qrcode();
                    cout << "\n\nPay to +60-1133459278 ; scroll up if you want to pay with QR code! ^o.o^\n\n ";
                    break;
                case 3:
                    cout << "\nEnter your Debit Card Number: ";
                    cin.ignore();
                    getline(cin, credit);
                    cout << "\nEnter Card Holder Name: ";
                    cin.ignore();
                    getline(cin, holder_name);
                    cout << "\nEnter expired date (MM/YY) [without /]: ";
                    cin >> expired;
                    cout << "\nEnter CVV: ";
                    cin >> cvv;
                    break;
                case 4:
                    cout << "\nEnter your Credit Card Number: ";
                    cin.ignore();
                    getline(cin, debit);
                    cout << "\nEnter Card Holder Name: ";
                    cin.ignore();
                    getline(cin, holder_name);
                    cout << "\nEnter expired date (MM/YY) [without /] : ";
                    cin >> expired;
                    cout << "\nEnter CVV: ";
                    cin >> cvv;
                    break;
                default:
                    cout << "\nInvalid input, please enter again! ^>.<^\n";
                }
                // Receipt
                receipt(invoiceNo, waffle, change, totalPrice, subtotal, discountValue, servicecharge, sst, totalQty, cash, totalOri, totalMatcha, totalCha, quantityOri, quantityMatcha, quantityCha, returnMain);

                // Feedback
                do {
                    cout << "\n[FEEDBACK SURVEY]\n";
                    cout << "How about your experience with MEOWAFFLE?! ^>.o^\n";
                    cout << "[A] Excellent\n";
                    cout << "[B] Good\n";
                    cout << "[C] Neutral\n";
                    cout << "[D] Bad\n";
                    cout << "[E] Worst\n";
                    cout << "Enter your feedback option > ";
                    cin >> feedback;
                    feedback = toupper(feedback);

                    switch (feedback) {
                    case 'A':
                        cout << "\nThank you! We're glad that you felt excellent!! ^>.o^\n";
                        break;
                    case 'B':
                        cout << "\nThank you! We're happy that you felt good!! ^>.o^\n";
                        break;
                    case 'C':
                        cout << "\nThank you for your feedback. We'll do our best to do better! ^o.o^\n";
                        break;
                    case 'D':
                        cout << "\nSorry for the inconvenience. Thank you for the honest feedback. ^>.<^\n";
                        break;
                    case 'E':
                        cout << "\nWe apologize for the bad experience. We'll ensure this won't be happen again. ^Q.Q^\n";
                        break;
                    default:
                        cout << "\nInvalid input, please enter again! ^>.<^\n";
                    }

                } while (feedback != 'A' && feedback != 'B' && feedback != 'C' && feedback != 'D' && feedback != 'E');

                if (totalPrice >= 10) {
                    luckydraw();
                    cout << "\nThanks for purchasing at MEOWAFFLE!! ^>.o^\n";
                    cout << "\nDo you want to return back to main menu? ^o.o^";
                    do {
                        cout << "\n\nEnter 'R' return to main menu > ";
                        cin >> returnMain;
                        returnMain = toupper(returnMain);

                        if (returnMain != 'R') { // Invalid choice
                            cout << "\nInvalid input, please enter again! ^>.<^" << endl;
                        }
                    } while (returnMain != 'R');
                }
                else if (totalPrice < 10) {
                    cout << "\nThanks for purchasing at MEOWAFFLE!!\n";
                    cout << "\nDo you want to return back to main menu? ^o.o^";
                    do {
                        cout << "\n\nEnter 'R' return to main menu > ";
                        cin >> returnMain;
                        returnMain = toupper(returnMain);

                        if (returnMain != 'R') { // Invalid choice
                            cout << "\nInvalid input, please enter again! ^>.<^" << endl;
                        }
                    } while (returnMain != 'R');
                }
            }
            // Reporting
            else if (startopt == 2) {
                system("CLS");
                cout << "\nDo you want to check daily or monthly report? ^o.o^\n\n['D'-daily report ; 'M'-monthly report]\n\nEnter your option > ";
                cin >> report;
                do {
                    report = toupper(report);

                    if (report != 'D' && report != 'M') {
                        cout << "\nInvalid input, please enter again! ^>.<^\n" << endl;
                    }
                    else if (report == 'D') {
                        dReport(); // Switch to daily report
                        cout << "\nDo you want to return back to main menu?";
                        do {
                            cout << "\nEnter 'R' return to main menu > ";
                            cin >> returnMain;
                            returnMain = toupper(returnMain);

                            if (returnMain != 'R') { // Invalid choice
                                cout << "\nInvalid input, please enter again! ^>.<^" << endl;
                            }
                        } while (returnMain != 'R');
                    }
                    else if (report == 'M') {
                        mReport(); // Switch to monthly report
                        cout << "\nDo you want to return back to main menu?";
                        do {
                            cout << "\nEnter 'R' return to main menu > ";
                            cin >> returnMain;
                            returnMain = toupper(returnMain);

                            if (returnMain != 'R') { // Invalid choice
                                cout << "\nInvalid input, please enter again! ^>.<^" << endl;
                            }
                        } while (returnMain != 'R');
                    }
                } while (report != 'D' && report != 'M');
            }
            // Exit, terminate program
            else if (startopt == 3) {
                return 0;
            }
            else if (startopt < 1 || startopt > 3) {
                cout << "\nInvalid option, please enter again! ^>.<^" << endl;
            }
        } while (startopt != 1 && startopt != 2 && startopt != 3);
    } while (returnMain == 'R');
    return 0;
}
