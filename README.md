# Challenge-02
Challenge 2
## Updates Overview
I updated the existing Lender Software to prompt the user to save the qualifying loans as a new CSV file to allow the user to share his or her results as a spreadsheet.

## What Changed?
### 1. Add code to allow the user to save their results as a csv file.
This code will prompt the user to save the results as a CSV file. If there are no qualifying loans, the program will notify the user and exit.

'''python
def save_qualifying_loans(qualifying_loans):
    answer = questionary.confirm("Would you like to save the loans in a CSV File?").ask()
    if answer == True:
        save_csv_path = questionary.text("Enter the path to save the csv file").ask
        save_csv_path = Path(save_csv_path)
        header = ["Lender, Max Loan Amount, Max LTV, Max DIT, Min Credit Score, Interest Rate"]
        save_csv(save_csv_path, qualifying_loans, header)
    else:
        sys.exit
'''

### 2. Improved usability 
Will prompt the user to either save or opt of saving their CSV file.
(See code above)

### 3. Test and Debug the software
This will ensure more stability in the software.
'''python
def test_save_csv():
    qualifying_loans = "test"
    csvoutpath = Path("./data/output/qualifying_loans.csv")

    fileio.save_csv(
        csvoutpath,
        qualifying_loans,
        [
            "lender",
            "max_loan_amount",
            "max_loan_to_value",
            "max_debt_to_income",
            "min_credit_score",
            "interest_rate",
        ]
    )
    assert csvoutpath.exists()
    '''
