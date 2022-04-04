## Person

Person(*idPerson*)

Name(*person*, first, last) \
FK: (person) ⊆ Person(idPerson)

Email(*person*, email)\
FK: (person) ⊆ Person(idPerson)

Address(*person*, street, city, postalCode)\
FK: (person) ⊆ Person(idPerson)
___

## Login

Login(*person*, login, password)\
FK: (person) ⊆ Person(idPerson)
___

## Employee

Employee(*person*, idEmployee)\
FK: (person) ⊆ Person(idPerson)

Phone(*employee*)\
FK: (employee) ⊆ Employee(idEmployee)

WorkPosition(*employee*, *branch*, name, description)\
FK: (employee) ⊆ Employee(idEmployee)
FK: (branch) ⊆ Branch(idBranch)
___

## Branch

Branch(*bank*, *idBranch*, name)\
FK: (bank) ⊆ Bank(code)

Address(*branch*, street, city, postalCode)\
FK: (branch) ⊆ Branch(idBranch)
___

## Bank

Bank(*code*, name)
___

## Entitlement

Module(*idModule*, name, description)

Permission(*module*, name)\
FK: (module) ⊆ Module(idModule)

Role(*employee*, idRole, name, description)\
FK: (employee) ⊆ Employee(idEmployee)

Entitlement(*employee*, role, module, name)\
FK: (employee) ⊆ Employee(idEmployee)\
FK: (role) ⊆ Role(idRole)\
FK: (module) ⊆ Module(idModule)
___

## Customer

Customer(*idCustomer*)\
FK: (person) ⊆ Person(idPerson)

Phone(*customer*)\
FK: (customer) ⊆ Customer(idCustomer)
___

## Support

Ticket(*idNumber*, date, time, name, description)

Support(*ticket*, *customer*, *employee*, rate)\
FK: (ticket) ⊆ Ticket(idNumber)\
FK: (customer) ⊆ Customer(idCustomer)\
FK: (employee) ⊆ Employee(idEmployee)
___

##  Account

Account(*customer*, *idNumber*, currency)\
FK: (customer) ⊆ Customer(idCustomer)

Type(*accountNumber*, Personal, Real, Nominal)\
FK: (accountnumber) ⊆ Account(idNumber)
___

##  Transaction

Transaction(*idNumber*, *accountFrom*, *accountTo*)\
FK: (accountFrom) ⊆ Account(idNumber)\
FK: (accountTo) ⊆ Account(idNumber)
___

##  Loan

Loan(*idNumber*, *customer*, *branch*, amount, interest)
FK: (customer) ⊆ Customer(idCustomer)
FK: (branch) ⊆ Branch(idBranch)

Payment(*idNumber*, *loan*, amount, date)
FK: (loan) ⊆ Loan(idNumber)
___