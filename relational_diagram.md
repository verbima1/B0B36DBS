## Person

Person(idPerson)

Name(person, first, last) \
FK: (person) ⊆ Person(idPerson)

Email(person, email)\
FK: (person) ⊆ Person(idPerson)

Address(person, street, city, postalCode)\
FK: (person) ⊆ Person(idPerson)


## Login

Login(person, login, password)\
FK: (person) ⊆ Person(idPerson)


## Employee

Employee(person, idEmployee)\
FK: (person) ⊆ Person(idPerson)

Phone(employee)\
FK: (employee) ⊆ Employee(idEmployee)

WorkPosition(employee, branch, name, description)\
FK: (employee) ⊆ Employee(idEmployee)
FK: (branch) ⊆ Branch(idBranch)


## Branch

Branch(bank, idBranch, name)\
FK: (bank) ⊆ Bank(code)

Address(branch, street, city, postalCode)\
FK: (branch) ⊆ Branch(idBranch)


## Bank

Bank(code, name)


## Entitlement

Module(idModule, name, description)

Permission(module, name)\
FK: (module) ⊆ Module(idModule)

Role(employee, idRole, name, description)\
FK: (employee) ⊆ Employee(idEmployee)

Entitlement(employee, role, module, name)\
FK: (employee) ⊆ Employee(idEmployee)\
FK: (role) ⊆ Role(idRole)\
FK: (module) ⊆ Module(idModule)


## Customer

Customer(idCustomer)\
FK: (person) ⊆ Person(idPerson)

Phone(customer)\
FK: (customer) ⊆ Customer(idCustomer)


## Support

Ticket(idNumber, date, time, name, description)

Support(ticket, customer, employee, rate)\
FK: (ticket) ⊆ Ticket(idNumber)\
FK: (customer) ⊆ Customer(idCustomer)\
FK: (employee) ⊆ Employee(idEmployee)