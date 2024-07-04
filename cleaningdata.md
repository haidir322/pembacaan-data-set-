cleaning data 
==
 tahapan dalam proses pembersihan data 
 - rancangan tahapan serta metode apa saja yang akan dilakukan   dari masalh yang di temukan   bisa digunkan sebagi dokumens=tasi
 -  mengkonversi ke dalam code dari rancangan tersebut
 -  memriksa kembali data yang dibersihkan   memastikan proses pembersihan

tekninik mengatasi  missing value 
--
- Dropping
===
menghapus seluruh baris  yang terjadi misssing value
dropna()
 mines nya  kita kehilangan informasi
import pandas as pd
 
products_df = pd.read_csv("product.csv")
 
products_df.dropna(axis=0, inplace=True)

- Imputation
==
mengisi  missing value  dengan nilai tertentu
- positifnya  mencegah hilangnya  missing value
- minesnya  memengaruhi variance ? sebaran dari sebuah data  ( kurang cocok sama time serises )
Pada data kontinu, kita bisa menggunakan nilai mean, median, atau mode

Jika bekerja menggunakan data kategoris, kita dapat mengisi missing value dengan kategori yang paling sering muncul.
fillna()

import pandas as pd
 
data=pd.read_csv('employee_data.csv')
 
data.age.fillna(value=data.age.mean(), inplace=True)

- interpolation
==
menghitung titik data baru   berdasarkan  range data yanag  yang sudah ada
menggunkana garis liner ataya  polynominal ( cocok dengn time series )
interpolate()
nentuin dulu  metode interpolasi yang di gunakan
kita juga perlu mendefinisikan parameter limit_direction (forward, backward, dan both) untuk menspesifikkan arah 
konstruktif dari proses interpolasi.

import pandas as pd
 
data=pd.read_csv('bbca_index.csv')
 
data.close_price.interpolate(method='linear', limit_direction='forward', inplace=True)

Teknink mengatasi outlier 
--
- drop

import pandas as pd
 
df = pd.read_csv("data.csv")
 
Q1 = (df['TotalCharges']).quantile(0.25)
Q3 = (df['TotalCharges']).quantile(0.75)
IQR = Q3 - Q1
 
maximum = Q3 + (1.5*IQR)
minimum = Q1 - (1.5*IQR)
 
kondisi_lower_than = df['TotalCharges'] < minimum
kondisi_more_than = df['TotalCharges'] > maximum

 - imputation
mask()
df = pd.read_csv("data.csv")
 
Q1 = (df['TotalCharges']).quantile(0.25)
Q3 = (df['TotalCharges']).quantile(0.75)
IQR = Q3 - Q1
 
maximum = Q3 + (1.5*IQR)
minimum = Q1 - (1.5*IQR)
 
kondisi_lower_than = df['TotalCharges'] < minimum
kondisi_more_than = df['TotalCharges'] > maximum
 
df.mask(cond=kondisi_more_than, maximum, axis=1, inplace=True)
df.mask(cond=kondisi_lower_than, minimum, axis=1, inplace=True)

Teknik mengatasi  duplicate date  
--
- drop
import pandas as pd
 
df = pd.read_csv("data.csv")
df.drop_duplicates(inplace=True)
