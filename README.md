#mini projet on ATM
'''
1) set pin
2)check balance
3) withdraw
4)set pin
variables:  bal=0
            og_pin=None'''

# creat set pin function
bal=0
og_pin=None


def set_pin():
    global og_pin
    while True:
        print('=*'*30)
        if og_pin==None:
            pin1=int(input('Enter a 4 digit PIN : '))
            pin2=int(input('Confirm your PIN: '))
            if pin1==pin2:
                print('PIN Set Successfully')
                og_pin=pin2
                break
            else:
                print('Incorrect PIN')
        else:
            print('PIN is Already set')


def check_balance():
    pin = int(input('Enter a 4 digit PIN: '))
    if pin == og_pin:
        print('Available balance in your account is', bal, 'Rs')
    else:
        print('Incorrect PIN')


def deposit():
    global bal
    pin=int(input('Enter a 4 digit PIN : '))
    if pin==og_pin:
            amt=int(input('Enter The Amount to Deposit : '))
            bal+=amt
            print('Amount of ',amt, 'Rs. Deposited Successfully')
    else:
        print('Incorrect PIN OR PIN Not set')

def withdraw():
    global bal
    pin=int(input('Enter a 4 digit PIN : '))
    if pin==og_pin:
        amt=int(input('Enter The Amount to Withdraw : '))
        if amt<=bal:
            bal-=amt
            print('Amount of ',amt, 'Rs. Withdraw Successfully')
        else:
            print('Insuficiant Funds')
    else:
        print('Incorrect PIN OR PIN Not set')

def service():
    while True:
        print('=*'*60)
        print('-----WELCOME TO THIS ATM-------')
        print('Enter 1: Deposit')
        print('Enter 2: Withdraw')
        print('Enter 3: Check balance')
        print('Enter 4: Set PIN')
        print('Enter 5: Exit.')
        ch=int(input('Enter the Choice : '))
        if ch in (1,2,3,4,5):
            if ch==1:
                deposit()
            elif ch==2:
                withdraw()
            elif ch==3:
                check_balance()
            elif ch==4:
                set_pin()
            elif ch==5:
                print('-----Thank for using our ATM service------')
                break
            a=input('Do you want to continue(yes/no)?:')
            if a.lower() in 'yes':
                continue
            elif a.lower() in 'no':
                print('-----Thank for using our ATM service------')
                break
            else:
                print('Please enter correctly')
                break
        else:
            print('Invalid Choice.....Please try again!')


service()
