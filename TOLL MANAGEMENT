import cx_Oracle
#imported library to connect oracle database

connection = cx_Oracle.connect(user="system", password="student", dsn="localhost/XE")
cursor = connection.cursor()
#connection established

# cursor.execute("create table Akshansh_239(Vehicle_Type varchar(6),Plate_number varchar(12),
#  Mode_payment varchar(7),Amount number(10),RFID_No varchar(20))")
print("_"*220)
print('\t\t\t\t\t\t\t\t\t\t * TollTaxManagement Database *')
print("_"*220)
print()
def menu_d():

    print("\n\t\t\t\t Select the task required to be performed \n")
    print("\t\t\t\t\t *1[  Enter   Vehicle   Information ]:- ")
    print("\t\t\t\t\t *2[  Display   Current   Data ]:- ")
    print("\t\t\t\t\t *3[  Update   Data]:- ")
    print("\t\t\t\t\t *4[  Delete   Data]:-")
    print("\t\t\t\t\t *5)[ Analyzing Records for particular Data]")
    print("\t\t\t\t\t *6) [Exit] :-")
    print()
End_table=True
Amount = 0
while End_table:
    menu_d()
    select = int(input("\t\t\t\t\tEnter the Task_Number "))
    if select == 1:
        # acquiring the info of all the users to be
        try:
            Wheel = True
            while Wheel:
                Mode_of_payment = ""
                Vehicle_Type = input("Enter the type of vehicle ")
                if Vehicle_Type == "car" or Vehicle_Type == "Car":
                    Amount = 35
                elif Vehicle_Type == "jeep" or Vehicle_Type == "Jeep":
                    Amount = 50
                elif Vehicle_Type == "lcv" or Vehicle_Type == "LCV":
                    Amount = 100
                elif Vehicle_Type == "hcv" or Vehicle_Type == "HCV":
                    Amount = 150
                elif Vehicle_Type == "govt":
                    Amount = 0
                else:
                    print("Some custom vehicle entered ")
                    Amount = int(input("Enter the amount "))
                Plate_number = input("Enter the plate of vehicle ")
                Mode_of_payment = input("Enter Cash or Card or fastag ")
                if Mode_of_payment == "fastag":
                    RFID_No = int(input("Enter the fastag number"))
                else:
                    RFID_No = 0
                # Making ORACLE Query
                query = "insert into Akshansh_239 values('{}','{}','{}',{},{})".format(Vehicle_Type, Plate_number, Mode_of_payment, Amount, RFID_No)
                cursor.execute(query)
                connection.commit()
                print('Data successfully registered')
                print("-"*220)
                Wheel_P = input("To Insert more records press Enter otherwise press Spacebar and Enter  ")
                if Wheel_P==" ":
                    Wheel=False
        except Exception as e:
             print("something went wrong  ",e)
    elif select == 2:  # Displaying records entered until now
        try:
            query = 'select * from Akshansh_239'  # all the records
            cursor.execute(query)
            retrieve = cursor.fetchall()
            # review data
            print('Showing data registered')
            for i in retrieve:
                print(["Vehicle_Type", i[0], "Plate_number", i[1], "Mode_payment", i[2], "Amount", i[3],
                       'RFID_No',i[4]])  # printing all data entered until now

        except Exception as e:
            print("something went wrong ", e)

    elif select == 3:  # Modification of data in case of  changes and mistake
        try:
            Upd_data = True  # loop start
            while Upd_data:
                To_update = input("Enter the Plate Number of the Vehicle's data you wish to update  ")
                query = f"SELECT * FROM Akshansh_239 where Plate_number='{To_update}'"
                cursor.execute(query)
                retrieve = cursor.fetchall()
                Empty_input = cursor.rowcount  # using rowcount
                print(Empty_input)
                if Empty_input == 0:
                    print("An invalid or unregistered number entered ")
                else:
                    Empty_input = cursor.rowcount  # using rowcount
                    Listx = []
                    Listc = {}  # making a dictionary for the queries and then changing the information
                    for i in retrieve:
                        Listc["Vehicle _Type"] = i[0]
                        Listc["Plate_number"] = i[1]
                        Listc["Mode_payment"] = i[2]
                        Listc["Amount"] = i[3]
                        Listc['RFID_No'] = i[4]
                        Listx += "Vehicle_Type", i[0], "Plate_number", i[1], "Mode_payment", i[2], "Amount", i[
                            3], "RFID_No", i[4]
                    print(Listx)
                    print("                    1 ---> Vehicle_Type\n\
                       2--->Plate_number \n\
                       3 ---> Mode_payment\n\
                       4 ---> Amount\n\
                       5 ---> RFID_No")
                    Mod_R = int(input("Press the number to change value  "))
                    if Mod_R == 1:
                        a = input("Enter the corrected value ")
                        Listx.insert(1, a)
                        Listx.pop(2)

                        print(Listx)
                    elif Mod_R == 2:
                        a = input("Enter the corrected value ")
                        Listx.insert(3, a)
                        Listx.pop(4)

                        print(Listx)
                    elif Mod_R == 3:
                        a = input("Enter the corrected value ")
                        Listx.insert(5, a)
                        Listx.pop(6)

                        print(Listx)
                    elif Mod_R == 4:
                        a = input("Enter the corrected value ")
                        Listx.insert(7, a)
                        Listx.pop(8)

                        print(Listx)
                    elif Mod_R == 5:
                        a = input("Enter the corrected value ")
                        Listx.insert(9, a)
                        Listx.pop(10)
                        print(Listx)
                    else:
                        print("An Invalid value was entered type correctly ")
                        print(Listx)

                try:
                    query = 'select * from Akshansh_239'  # all the records
                    cursor.execute(query)
                    retrieve = cursor.fetchall()  # review data
                    print('Showing data updated')
                    for i in retrieve:
                        print(["Vehicle_Type", i[0], "Plate_number", i[1], "Mode_payment", i[2], "Amount", i[3],
                               'RFID_No', i[4]])  # printing all data entered until now

                    print(Listx)
                except Exception as e:
                    print("something went wrong ", e)

                Upd_dat = input("To update more records press Enter  ")
                if Upd_dat == " ":
                    Upd_data = False  # loop end

        except Exception as e:
            print("Something went wrong ", e)



    elif select == 4:
        try:
            Del_spe = True  # loop start
            while Del_spe:
                To_delete = input("Type the Plate of the vehicle to erase data ")
                query = f"delete FROM Akshansh_239 where Plate_number='{To_delete}'"
                cursor.execute(query)
                connection.commit()
                Empty_input = cursor.rowcount
                if Empty_input > 0:
                    print("Data erased")
                else:
                    print("No Plate of such a person found")
                Del_mor = input("To Delete more records press Enter   ")
                if Del_mor == " ":
                    Del_spe = False  # loop end
        except Exception as e:
            print("something went wrong ", e)

    elif select == 5:  # finding specific records
        try:
            Get_spe = True  # loop start
            while Get_spe:
                To_find = input("Enter  the record's plate number to be found   ")
                query = f"SELECT * from Akshansh_239 where Plate_number='{To_find}'"
                cursor.execute(query)
                retrieve = cursor.fetchall()
                print(retrieve)
                Empty_input = cursor.rowcount  # using rowcount
                if Empty_input == 0:
                    print("An invalid or unregistered number entered  ")
                Get_mor = input("To search for more records press Enter   ")
                if Get_mor == " ":
                    Get_spe = False  # loop end
        except Exception as e:
            print("something went wrong  ", e)

    else:  # closing the database
        print("The database is now being closed ")
        print('-' * 220)
        End_table = False
        break

    ask_user = input("To go to the main screen press Enter or Press 1 to Exit the Database  ")
    print('-' * 220)
    if ask_user == '1':
        End_table = False
