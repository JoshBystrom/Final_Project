# Final_Project
import sqlite3

connection = sqlite3.connect('city.db')

cursor = connection.cursor()

cursor.execute("create table city (city_id integer, city_name text, cit_population integer)")

city_stats_list = [
    (4614043725, "Lino Lakes", 21608),
    (8746844932, "Duluth", 85916),
    (6356321461, "Mankato", 45958),
    (4362874321, "Saint Cloud", 69032),
    (7432746916, "Eagan", 67534),
    (5432546348, "Winona", 25908),
    (4367214362, "Brainerd", 14404),
    (9438679446, "Minneapolis", 429985),
    (8543245875, "Maple Grove", 70264),
    (1423452533, "Edina", 53487)
]

cursor.executemany("insert into city values (?,?,?)", city_stats_list)

for row in cursor.execute("select * from city"):
    print(row)

connection.close()

