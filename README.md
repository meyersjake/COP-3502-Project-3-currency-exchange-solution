# COP-3502-Project-3-currency-exchange-solution

Download Here: [COP 3502 Project 3 currency exchange solutionBackground
A Fortune 500 company that runs currency exchange kiosks in all the major airports
around the world has recently viewed your programming work. They were very
impressed and now have a special job for you. The currency conversion software they
currently have is long obsolete and no longer runs efficiently in their exchange machines.
This is partly because the last group of people to write the code did not build the
program’s functionality into separate methods but rather jammed all their code into the
main() method, which later proved to be a total disaster. Your assignment is to write
an all­new version of the program that uses methods so that they can get their exchange
booths back up and running and avoid losing customers. The kiosks allow the user to
deposit money into their account (this is a temporary account that only exists until the
user is finished with all his/her conversions), view the remaining U.S. dollar balance in
the user’s account, and withdraw arbitrary amounts in any currency that the machine
supports.
Your Assignment
Your task is to write a Java program for the kiosk machines that can perform the tasks
described above at the user’s request. The task begins by printing a quick welcome
message, displaying a table of currency values, and then proceeding to the main menu.
At that point, the customer can
A) Have their remaining balance displayed,
B) Deposit a certain amount of one currency into their account and convert it into
U.S. dollars,
C) Withdraw a certain amount from their remaining balance in a particular
currency, or
D) End their transaction which will give them back all of their remaining balance
in U.S. dollars. Upon completion of A, B, or C, the program will return to the main menu
(loop).
IMPORTANT: Since this company is a U.S.­based firm, options B) will automatically
convert any deposit currency into US dollars i.e. The account only holds a U.S dollar
balance. When the user withdraws a certain amount of their remaining balance in a
particular currency except USD, the amount will be converted from U.S. dollar balance
plus 0.5% of total withdrawal amount as convenience fee.
Example:
The user has a $10 U.S. dollar balance in their account. If they want to withdraw 0.89
Euros from the account, the total amount withdrawn from the account is calculated as:
amount = 0.89 / 0.89 * (1+0.005) = $1.005 USD.
His/her remaining balance will be $8.995 USD
ALL currency values will be stored as type double. There should be a balance variable
in the class to store the balance of the account. Deposit/Withdraw amount should always
be positive numbers. For simplicity, when withdrawing and depositing from/to the
account, the value of the remaining balance should be rounded up to 2 significant digits
both when displayed and saved. Round up is NOT required in conversions. The way to
round up to a specific significant digit can be found in previous Labs. Please use the code
below to update the balance so that it has 2 digits after the decimal. This should only be
used in Options B) and C)
private static boolean updateBalance(double newBalance)
{
balance = Math.round(newBalance * 100) / 100.0;
if (balance >= 0) {
return true;
} else
return false;
}
The currency conversion table (methods of conversion will be discussed later) that you
are required to use is displayed below. DO NOT use any other conversion table found
online as the values of these currencies are likely to change.
US Dollar 1.00
Euro 0.89
British Pound 0.78
Indian Rupee 66.53
Australian Dollar 1.31
Canadian Dollar 1.31
Singapore Dollar 1.37
Swiss Franc 0.97
Malaysian Ringgit 4.12
Japanese Yen 101.64
Chinese Yuan Renminbi 6.67
Mandatory Methods
For your convenience, we created a skeleton source file for you(including all the
mandatory methods), please use the skeleton file to start your project. KEEP the
balance variable, getBalance()and updateBalance() methods unchanged.
The following are a list of MANDATORY methods that you must use/implement in
your program. The functionality found in these methods may not be created
anywhere else in the program! We will only grade your methods. Not creating
the methods exactly as described below will cause you to lose points as well as
make your code disorganized and hard to understand. The methods will be tested
using test cases. Some test cases are corner cases such as negative amount, divide by
zero etc. When implementing these methods, considering the potential corner cases
carefully. You may create additional methods, however, you MUST have the methods
listed below.
7 Mandatory methods:
/**
* Prints the conversion table at the start of the program (see the
output examples).
*/
public static void printConversionTable()
/**
* Prints the main menu (see output examples), allows the user to make a
selection from available operations
*
* @param input the Scanner object you created at the beginning of the
main method. Any value other than the 4 valid selections should generate
an invalid value prompt. Print the list again and prompt user to select
a valid value from the list.
* @return an integer from 1‐4 inclusive representing the user’s
selection.
*/
public static int mainMenuOptionSelector(Scanner input)
/**
* Prints the currency menu (see output examples), allows the user to
make a selection from available currencies
*
* @param input the Scanner object you created at the beginning of
the main method. Any value other than the 11 valid valid currency types
should generate an invalid value prompt. Print the list again and prompt
user to select a valid value from the list. the currency type will be
the same as the type number used in {@link #convertCurrency(double, int,
boolean)}
* @return an integer from 1‐11 inclusive representing the user’s
selection.
*/
public static int currencyMenuOptionSelector(Scanner input)
/**
* Convert the value amount between U.S. dollars and a specific currency.
*
* @param amount The amount of the currency to be converted.
* @param currencyType The integer currencyType works as follows:
* 1 for usd (U.S. Dollars)
* 2 for eur (Euros)
* 3 for bri (British Pounds)
* 4 for inr (Indian Rupees)
* 5 for aus (Australian Dollars)
* 6 for cnd (Canadian Dollars)
* 7 for sid (Singapore Dollars)
* 8 for swf (Swiss Francs)
* 9 for mar (Malaysian Ringgits)
* 10 for jpy (Japanese Yen)
* 11 for cyr (Chinese Yuan Renminbi)
* @param isConvertToUSD Tells the direction of the conversion. If the
value is true, then the conversion is from a foreign currency to USD. If
the value is false, then the conversion is from USD to the foreign
currency
* @return the converted amount
*/
public static double convertCurrency(double amount, int currencyType,
boolean isConvertToUSD)
/**
* deposit the amount of a specific currency to the account
*
* @param amount the amount to be deposited.
* @param currencyType the currency type will be the same as the type
number used
* in the convertCurrency(double, int, boolean)
method. An Invalid
* type will result in a deposit failure.
* @return if deposit succeeds (positive amount ‐
not zero),
* the method will return * true. otherwise,
return false
*/
public static boolean deposit(double amount, int currencyType)
/**
* withdraw the value amount with a specific currency from the account.
The withdraw amount should never exceed the current account balance, or
the withdrawal will fail. If the currency is other than USD, a 0.5%
convenience fee will be charged
*
* @param amount the amount to be withdrawn.
* @param currencyType the currency type will be the same as the type
number used
* in the convertCurrency(double, int, boolean)
method. An invalid
* type will result a withdraw failure.
* @return if withdraw succeed, will return true. If failed, return false
*/
public static boolean withdraw (double amount, int currencyType)
/**
* Displays message at the end of the withdraw, deposit, and
endTransaction stating
* how much the user just withdrew/deposited and what type (this will be
used in both features B, C and D of the main menu).
*
* @param amount the amount of currency withdrew/deposited
* @param currencyType the currency type will be the same as the type
number used
* in {@link #convertCurrency(double, int, boolean)}
* @param isDeposit if true log the deposit transaction, false log the
withdraw transaction
* @return Return the formatted log message as following examples:
* You successfully withdrew 10.0 U.S.
Dollars
* You successfully deposited 30.0 Japanese
Yen
*
* Invalid input like invalid currencyType or
negative amount,
* will return a “Logging Error”
*/
public static String logTransaction(double amount, int currencyType,
boolean isDeposit)
Submission Requirements
Read the description for each mandatory method carefully
● Name the class “CurrencyExchange”. All Mandatory methods should
reside in the CurrencyExchange Class. The source file should be named as
“CurrencyExchange.java”. Please use the EXACT class name and source file
name, or you will have a ZERO grade.
● Zip the java file WITHOUT any folder hierarchy in a zip file. (or you will
get a zero grade)
● Name the zip file project3_uflid.zip where uflID is the alphanumeric portion of
your UF email account that comes before the @ufl.edu part.
● Submit using Canvas
If you submit the .java file without zipping, your project will not be graded.
If your file is not named project3_uflid.zip, your project will not be graded.
If you do not name the Project and class exactly as specified, your project will not be
graded.
Please only create one Scanner object to read input, otherwise, the autograder will not be
able to provide input.
It is highly recommended that you test your program piece by piece before assembling
your final code. You will have a much easier time if you build your program piece by
piece rather than trying to write the entire program. Pay very close attention to the order
that you give inputs to the sample program. Your output should not differ in any
way from the sample output. Using additional prompts, words, abbreviations, etc may
result in the grading program taking unnecessary points off.
Grading
● 100% of your program will be graded on its ability to generate proper output
and using all of the mandatory methods.
Sample Run ­ 1 (user input is in
red)
Welcome to Currency Exchange 2.0
Current rates are as follows:
1 ­ U.S. Dollar ­ 1.00
2 ­ Euro ­ 0.89
3 ­ British Pound ­ 0.78
4 ­ Indian Rupee ­ 66.53
5 ­ Australian Dollar ­ 1.31
6 ­ Canadian Dollar ­ 1.31
7 ­ Singapore Dollar ­ 1.37
8 ­ Swiss Franc ­ 0.97
9 ­ Malaysian Ringgit ­ 4.12
10 ­ Japanese Yen ­ 101.64
11 ­ Chinese Yuan Renminbi ­ 6.67
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
2
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
8
Please enter the deposit amount:
2.91
You successfully deposited 2.91 Swiss Francs
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
1
Your current balance is: 3.0
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
3
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
1
Please enter the withdrawal amount:
1
You successfully withdrew 1.0 U.S. dollars
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
1
Your current balance is: 2.0
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
3
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
8
Please enter the withdrawal amount:
0.97
You successfully withdrew 0.97 Swiss Francs
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
1
Your current balance is: 1.0
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
4
You successfully withdrew 1.0 U.S. Dollars
Goodbye
Sample Run ­ 2 (user input is in
red)
Welcome to Currency Exchange 2.0
Current rates are as follows:
1 ­ U.S. Dollar ­ 1.00
2 ­ Euro ­ 0.89
3 ­ British Pound ­ 0.78
4 ­ Indian Rupee ­ 66.53
5 ­ Australian Dollar ­ 1.31
6 ­ Canadian Dollar ­ 1.31
7 ­ Singapore Dollar ­ 1.37
8 ­ Swiss Franc ­ 0.97
9 ­ Malaysian Ringgit ­ 4.12
10 ­ Japanese Yen ­ 101.64
11 ­ Chinese Yuan Renminbi ­ 6.67
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
2
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
10
Please enter the deposit amount:
203.28
You successfully deposited 203.28 Japanese Yen
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
1
Your current balance is: 2.0
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
3
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
1
Please enter the withdrawal amount:
1
You successfully withdrew 1.0 U.S. dollars
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
1
Your current balance is: 1.0
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
0
Input failed validation. Please try again.
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
5
Input failed validation. Please try again.
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
4
You successfully withdrew 1.0 U.S. dollars
Goodbye
Sample Run ­ 3 (user input is in
red)
Welcome to Currency Exchange 2.0
Current rates are as follows:
1 ­ U.S. Dollar ­ 1.00
2 ­ Euro ­ 0.89
3 ­ British Pound ­ 0.78
4 ­ Indian Rupee ­ 66.53
5 ­ Australian Dollar ­ 1.31
6 ­ Canadian Dollar ­ 1.31
7 ­ Singapore Dollar ­ 1.37
8 ­ Swiss Franc ­ 0.97
9 ­ Malaysian Ringgit ­ 4.12
10 ­ Japanese Yen ­ 101.64
11 ­ Chinese Yuan Renminbi ­ 6.67
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
2
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
0
Input failed validation. Please try again.
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
12
Input failed validation. Please try again.
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
11
Please enter the deposit amount:
6.67
You successfully deposited 6.67 Chinese Yuan Renminbi
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
1
Your current balance is: 1.0
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
3
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
1
Please enter the withdrawal amount:
1.01
Error: Insufficient funds.
Logging Error
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
3
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
1
Please enter the withdrawal amount:
1
You successfully withdrew 1.0 U.S. dollars
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
4
Your remaining balance is 0.0 U.S. Dollars
Goodbye
Sample Run ­ 4 (user input is in
red)
Welcome to Currency Exchange 2.0
Current rates are as follows:
1 ­ U.S. Dollar ­ 1.00
2 ­ Euro ­ 0.89
3 ­ British Pound ­ 0.78
4 ­ Indian Rupee ­ 66.53
5 ­ Australian Dollar ­ 1.31
6 ­ Canadian Dollar ­ 1.31
7 ­ Singapore Dollar ­ 1.37
8 ­ Swiss Franc ­ 0.97
9 ­ Malaysian Ringgit ­ 4.12
10 ­ Japanese Yen ­ 101.64
11 ­ Chinese Yuan Renminbi ­ 6.67
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
2
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
1
Please enter the deposit amount:
­100
Logging Error
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
2
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
1
Please enter the deposit amount:
0
Logging Error
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
3
Please select the currency type:
1. U.S. Dollars
2. Euros
3. British Pounds
4. Indian Rupees
5. Australian Dollars
6. Canadian Dollars
7. Singapore Dollars
8. Swiss Francs
9. Malaysian Ringgits
10. Japanese Yen
11. Chinese Yuan Renminbi
1
Please enter the withdrawal amount:
­100
Logging Error
Please select an option from the list below:
1. Check the balance of your account
2. Make a deposit
3. Withdraw an amount in a specific currency
4. End your session (and withdraw all remaining
currency in U.S. Dollars)
4
Your remaining balance is 0.0 U.S. Dollars
Goodbye](https://jarviscodinghub.com/assignment/cop-3502-project-3-currency-exchange-solution/)

For Custom/Original Work email jarviscodinghub@gmail.com/whatsapp +1(541)423-7793

