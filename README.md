# pembacaan-data-set

format berkas csv 
--

import pandas  as pd 
df = pd.read_csv("data.csv", delimiter=",")

pd.read_csv = digunakan untuk membaca file csv , data.csv = data yang di baca , delimiter  format pembagian setiap kolum  

format berkas XLSX atau XLS 
--

import pandas  as pd 
df = pd.read_excel("data.xlsx", delimiter=",")

pd.read_excel = digunakan untuk membaca file excel , data.csv = data yang di baca , delimiter  format pembagian setiap kolum  

format berkas JSON
--

import pandas  as pd 
df = pd.read_json("data.json")

pd.read_json = digunakan untuk membaca file json , data.csv = data yang di baca 

format berkas HTML
--

import pandas  as pd 

url = "https://www.fdic.gov/resources/resolutions/bank-failures/failed-bank-list"
df = pd.read_html(url)[0]

pd.read_html= digunakan untuk membaca file dalam url html 

format berkas XML(extensible markup language)
--

import pandas as pd
 
df = pd.read_xml("https://www.w3schools.com/xml/books.xml")

pd.read_xml= digunakan untuk membaca file dalam url xml

Akses data dari SQL database
--
read_sql_table()untuk membaca SQL database table dan mempresentasikannya ke dalam bentuk pandas DataFrame.
import pandas as pd
import sqlalchemy as sqla
 
db = sqla.create_engine("sqlite:///mydata.sqlite")
 
pd.read_sql_table("table_name", db)

read_sql_query()untuk membaca SQL query dan mempresentasikannya ke dalam bentuk pandas DataFrame.
import pandas as pd
import sqlalchemy as sqla
 
db = sqla.create_engine("sqlite:///mydata.sqlite")
 
pd.read_sql_query("SELECT * FROM table_name", db)

read_sql()untuk membaca SQL query atau table dan mempresentasikannya ke dalam bentuk pandas DataFrame.
import pandas as pd
import sqlalchemy as sqla
 
db = sqla.create_engine("sqlite:///mydata.sqlite")
 
pd.read_sql("SELECT * FROM table_name", db)

pengabungan data  atau marge 
==
import pandas as pd
 
product_df = pd.read_csv("product.csv")    data 1 ( primary key )
orders_df = pd.read_csv("orders.csv")      data 2 ( foreign key )
 
new_order_df = pd.merge(
    left=product_df,     kiri  
    right=orders_df,     kanan 
    how="inner",         proses merge 
    left_on="product_id",
    right_on="product_id"
)
pd.merge= ini untuk menggabungkana data 
inner join  mengambil nilai yang bersesuaia antar kedua data 
left join + mengambil semua  nilaidari tabel kiri beserta nilai  yang bersesuaina  dari tabel kanan 
right join = mengambil semua nilai dari tabel kanan besrta nilai yang bersesuain dari tabel kiri 
outer join  mengambil sesuai dengan tabel  semua dta nya 
