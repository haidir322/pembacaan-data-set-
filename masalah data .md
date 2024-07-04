missing value 
==
maslah ini muncul karna  adanya nilai yang hilang  dari data  diigambbarkan dengan NAN


import pandas as pd
product_df = pd.read_csv("product.csv")
 
product_df.isnull().sum()
isnull() atau isna() =  ini digunakan untuk mengidentifikasi misssing value  dalama sebuah dataframe 
di kombinasikana sum()  untuk mennghitung   totla misssing  value 

invalid value 
==
ditemui ketika terdapat nilaia yang tidak masuk akal   tidak sesuai dengan ketentuan 
Sebagai contoh, data customer id haruslah bersifat unik dan memenuhi ketentuan tertentu seperti jumlah karakter serta komposisinya 
 tekinik yang digunakan  = filtering dan  regex

 dupllicate  data 
 == 
 meempunyai nilaia yang sama persis setiap kolom 
 import pandas as pd
 
url = "https://www.fdic.gov/resources/resolutions/bank-failures/failed-bank-list"
df = pd.read_html(url)[0]
df.duplicated().sum()     sama sepetti tadi menggunakan sum untuk mengtahui ada taua tidak nilai  duplicate nya dengan sum 

inacurate value 
==
 nilaia dalam sebuah data tidak sesuai dengan  hasil observeasi  

 incosisten value 
 ==
 muncul ketika  sebuah dta  tidak memilki nilaia yang konsisten baik segi satuan atau [un  ketentuan nilai muncul krana adanay perbedaan standar  

 outlier 
 ==
 titikd ata yang berada pada data yang berada sangata jauh  dari titiki data yanag laian  
 metode yang dii gunakan  IQR method 
 adanya ambang batas minimum dan ambang batas max jika lebih  ? kurang dari ambang batas tersebut di sebut outlier 

 import numpy as np
 
q25, q75 = np.percentile(data, 25), np.percentile(data, 75)
iqr = q75 - q25
cut_off = iqr * 1.5
minimum, maximum = q25 - cut_off, q75 + cut_off
 
outliers = [x for x in data if x < minimum or x > maximum]
