# Validations OfflineApp

## Legend
  - \* -> required,
  - \+ -> optional,
  - <  -> less than,
  - <= ->less than or equal,
  - =  -> equals



## SUBSECTIONS
#### INCOME
		typeOfIncome string * <20
		annualIncome number * >=0
		employerName string * <50
		employerPhone string *   [+XXX (XXX)-XXX-XXXX]   <=19
#### BASIC
		name string *  <=120     (first (50) + middle (20) + last (50))=120
		dob date * [yyyy-mm-dd] >18 years old
		apply boolean *
		sex string * [M or F]  =1
		ssn string + [XXX-XX-XXXX]  <=11
		migratoryStatus string * <10
		phone str *   [+XXX (XXX)-XXX-XXXX]   <=19
		email str *  <=62
		address str * <=95
		city str * <=35
		state str * <=2    -> example FL AZ etc...
		residenceCardNumber str + <=13
#### OTHERS
		totalMembers number * <20 >=1
		applyingForCoverage boolean * 
		annualHouseholdIncome number * >=0

		planSelected string * 
		monthlyPayment number * >=0
		cardNumber string * <=19
		cardCvv string * >=3 <=4
		cardFirstName string * <=50
		cardMiddleName string + <=50
		cardLastName string * <=50

### Members 
		relation * <15
		BASIC (but ssn only needs to be >0 years old)
		#if (relation === "spouse") {check for INCOME}

## Regular Expressions
```
    - name: /.*[^ ]+.*/g,
   
    - phone: /^\+?(\d{0,3})?[-. (]*(\d{3})[()-. ]*(\d{3})[()-. ]*(\d{4})$/,
   
    - ssn: /^[-. ]*(\d{3})[-. ]*(\d{2})[-. ]*(\d{4})[-. ]*$/,
   
    - card_number:  /^(?:[ -]*(?<visa>4\d{12}\d{3}?)|(?<mastercard>5[1-5]\d{14})|(?<discover>6(?:011|5\d{2})\d{12})|(?<amex>3[47]\d{13})|(?<diners>3(?:0[0-5]|[68]\d)\d{11})|(?<jcb>(?:2131|1800|35\d{3})\d{11})[ -]*)$/,

    - card_expiration: /^[^\d]*(0?\d|1[0-2])[/\- ]+(\d{4}|\d{2})[^\d]*$/,
    - card_cvv: /^[^\d]*(\d{3,4})[^\d]*$/,
```