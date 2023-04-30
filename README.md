# elite-102-day-1
import mysql.connector

connection = mysql.connector.connect(
 user = 'root',
 database = 'example1',
 password = 'nujabes'
)

cursor = connection.cursor()

intro = input(f"welcome to project bank account, what would you like to do?\n 1.create account\n 2.login\n")

if intro == "1":
 #new account
 #done
 new_name = input("eneter a name\n")
 new_pin = int(input("enter a pin\n"))
 new_account = (f"INSERT INTO bank_account (id, name, money) VALUES ('{new_pin}', '{new_name}', '0')")
 cursor.execute(new_account)
 connection.commit()
 print("account made successfully")

elif intro == '2':
 #Options for user
 pin = int(input("enter your pin number\n"))
 Main = input("what would you like to do?\n 1.check balance\n 2.deposit\n 3.withdraw\n 4.delete account\n 5.modify account\n")

 if Main == '1':
  #check balance
  #done
  testquery = (f"SELECT money FROM bank_account where id = '{pin}'")
  cursor.execute(testquery)

  for item in cursor:
   print(item)


 elif Main == '2':
  #deposit
  #done
  deposit = int(input("how much money do you want to deposit?\n"))
  deposit2 = (f"UPDATE bank_account SET money = money + '{deposit}' where id = '{pin}'")
  cursor.execute(deposit2)
  connection.commit()
  print("deposit successful")
 
 elif Main == '3':
  #withdraw
  #done
  withdraw = int(input("how much do you want to withdraw?\n"))
  withdraw2 = (f"UPDATE bank_account SET money = money - '{withdraw}' where id = '{pin}'")
  cursor.execute(withdraw2)
  connection.commit()
  print("withdraw successful")
 
 elif Main == '4':
  #delete account
  #done
  delete_account = (f"DELETE FROM bank_account where id = '{pin}'")
  cursor.execute(delete_account)
  connection.commit()

 elif Main == '5':
  #modify account
  #done
  update = input("what would you like to update?\n 1.name\n 2.id\n")
  
  if update == '1':
   name = input("what is the new name?\n")
   update_name = (f"UPDATE bank_account SET name = '{name}' where id = '{pin}' ")
   cursor.execute(update_name)
   connection.commit()
   print("update successful")

  elif update == '2':
   id = input("what is the new id?\n")
   new_id = (f"UPDATE bank_account SET id = '{id}' where id = '{pin}' ")
   cursor.execute(new_id)
   connection.commit()
   print("update successful")

cursor.close()
connection.close()
