# CIMB Savings Account System (Decorator Pattern)

## Problem Description
CIMB is a digital bank that offers GSave and UpSave savings accounts. As with a typical Savings Account, it contains `accountNumber`, `accountName`, and a `balance` for that account.

### Account Specifications

* **Typical Savings Account**
    * **Interest Rate:** 1%
    * **Benefits:** "Standard Savings Account" (The benefits are the same as other banks).

* **GSave**
    * **Interest Rate:** 2.5%
    * **Benefits:** "Standard Savings Account" plus access to "GCash transfer".

* **UpSave**
    * **Interest Rate:** 4.0%
    * **Benefits:** "Standard Savings Account" plus "with Insurance".

---

## Development Requirements

Develop a **Decorator Pattern** approach that will implement the provided UML diagram.

### Constraints & Rules
1.  **Strict UML Adherence:** Follow the provided UML diagram structure.
<img width="800" height="539" alt="LabAssignment7_GivenUML" src="https://github.com/user-attachments/assets/9b9488de-b40c-4e66-82ff-738634e72648" />

2.  **Interface Requirement:** `BankAcountDecorator` must be an interface.
3.  **Method Restrictions:** You are **not allowed** to insert other methods except what is stated in the diagram (setters and getters are allowed).
4.  **Driver Class:** The content of your `Cimb.java` should **ONLY** contain the provided code (see below) with the exception of inserting your own package name.

---

## Expected Output:
<img width="785" height="743" alt="LabAssignment7_ExpectedOutput" src="https://github.com/user-attachments/assets/5869a9e3-7318-48fa-baea-1c240154f326" />

---

## Method Descriptions

The following methods must be implemented as described:

* **`showAccountType()`**
    * Either returns "Savings Account", "GSave", or "UpSave".
* **`getInterestRate()`**
    * Either returns **0.01** for Savings Account; **0.025** for GSave; **0.04** for UpSave.
* **`getBalance()`**
    * Returns the balance of the account set.
* **`showBenefits()`**
    * Either returns "Standard Savings Account" for Savings Account;
    * Benefits offered by savings account + "GSave Transfer";
    * Benefits offered by savings account + "With Insurance".
* **`computeBalanceWithInterest()`**
    * Returns new balance by computing the balance plus the interest depending on the interest rate.
* **`showInfo()`**
    * Returns details of account number, account name, and balance.

---

## Provided Driver Code (`Cimb.java`)

```java
public class Cimb {

	public static void main(String[] args) {
		
		SavingsAccount account = new SavingsAccount();
		
		account.setAccountNumber(1234);
		account.setAccountName("Juan Dela Cruz");
		account.setBalance(10000.0);
		
		System.out.println(account.showInfo());
		System.out.println("Account type: " + account.showAccountType());
		System.out.println("Interest rate: " + account.getInterestRate());
		System.out.println("New balance: " + account.computeBalanceWithInterest());
		System.out.println("Benefits: " + account.showBenefits());
		
		System.out.println("----------------------");
		
		GSave gSave = new GSave(account);
		System.out.println(gSave.showInfo());
		System.out.println("Account type: " + gSave.showAccountType());
		System.out.println("Interest rate: " + gSave.getInterestRate());
		System.out.println("New balance: " + gSave.computeBalanceWithInterest());
		System.out.println("Benefits: " + gSave.showBenefits());
		
		System.out.println("----------------------");
		
		UpSave upSave = new UpSave(account);
		System.out.println(upSave.showInfo());
		System.out.println("Account type: " + upSave.showAccountType());
		System.out.println("Interest rate: " + upSave.getInterestRate());
		System.out.println("New balance: " + upSave.computeBalanceWithInterest());
		System.out.println("Benefits: " + upSave.showBenefits());
	}
}
