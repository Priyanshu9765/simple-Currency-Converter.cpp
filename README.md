
//---simple Cureency Converter---

#include <iostream>
#include <unordered_map>
#include <string>
#include <iomanip> // for std::setprecision

using namespace std;

// Function to convert currency
double convertCurrency(double amount, double rate) {
    return amount * rate;
}

int main() {
    unordered_map<string, double> exchangeRates;

    // Initialize exchange rates (These are example rates and might not reflect real-world values)
    exchangeRates["USD"] = 1.0;        // Base currency
    exchangeRates["EUR"] = 0.85;       // 1 USD = 0.85 EUR
    exchangeRates["GBP"] = 0.75;       // 1 USD = 0.75 GBP
    exchangeRates["INR"] = 74.10;      // 1 USD = 74.10 INR
    exchangeRates["JPY"] = 110.25;     // 1 USD = 110.25 JPY
    exchangeRates["AUD"] = 1.35;       // 1 USD = 1.35 AUD
    exchangeRates["CAD"] = 1.25;       // 1 USD = 1.25 CAD

    string fromCurrency, toCurrency;
    double amount, convertedAmount;

    cout << "Available currencies: USD, EUR, GBP, INR, JPY, AUD, CAD" << endl;

    // Get user input
    cout << "Enter the currency you want to convert from: ";
    cin >> fromCurrency;

    // Check if the fromCurrency is valid
    if (exchangeRates.find(fromCurrency) == exchangeRates.end()) {
        cout << "Invalid currency code." << endl;
        return 1;
    }

    cout << "Enter the currency you want to convert to: ";
    cin >> toCurrency;

    // Check if the toCurrency is valid
    if (exchangeRates.find(toCurrency) == exchangeRates.end()) {
        cout << "Invalid currency code." << endl;
        return 1;
    }

    cout << "Enter the amount to convert: ";
    cin >> amount;

    // Convert from fromCurrency to USD, then from USD to toCurrency
    double amountInUSD = amount / exchangeRates[fromCurrency];
    convertedAmount = convertCurrency(amountInUSD, exchangeRates[toCurrency]);

    // Display the converted amount with 2 decimal places
    cout << fixed << setprecision(2);
    cout << amount << " " << fromCurrency << " = " << convertedAmount << " " << toCurrency << endl;

    return 0;
}
