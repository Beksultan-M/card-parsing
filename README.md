# card-parsing

# -*- coding: utf-8 -*-
"""
Created on Sat May  2 14:47:19 2020

@author: beksu
"""
import json
import requests
import pandas as pd

def tuzeu(lst):
    kerek = ['number', 'country', 'bank']
    new_dict = {}

    for k in lst.keys():
        if k in kerek:
            for little_k in lst[k].keys():
                new_dict[little_k] = lst[k][little_k]
        else:
            new_dict[k] = lst[k]
    return new_dict



massiv = ["29", "18", "51", "54", "12", "35"]
m3 = ['https://lookup.binlist.net/4402']
m2 = []
mydata = pd.DataFrame()

for line in massiv:
    u = m3[0] + line
    url = u.strip('\n')
    #print(url)
    #m2.append(url)
    payload = {}
    headers= {}
    response = requests.request("GET", url, headers=headers, data = payload)
    
    my_dict = json.loads(response.text)
    new_dict = tuzeu(my_dict)
    m2.append(new_dict)
    #
    #print(my_dict['number']['length'])
    #print(mydata['number'])

#print(m2)
my_df = pd.DataFrame(m2)
#mydata = pd.concat([my_dataframe, mydata])

    
    
    

my_df.to_excel('Card_Results_21.xls')























#mydata = pd.DataFrame(m2)


#print(m2)
#print(type(m2))

#for line in m2:
#    m1.append(str(line, encoding = 'utf-8'))
    
#my_dataframe3 = json.load(m2[0])
#print(m2[0])
#print(df)
#my_dataframe2 = json.loads(m2[0])



#df1 = pd.read_json(m2[0])
#data1 = pd.DataFrame(df1)
#df2 = pd.read_json(m2[1])
#data2 = pd.DataFrame(df2)
#df3 = pd.read_json(m2[2])
#data3 = pd.DataFrame(df3)
#df4 = pd.read_json(m2[3])
#data4 = pd.DataFrame(df4)
#df5 = pd.read_json(m2[4])
#data5 = pd.DataFrame(df5)
#df6 = pd.read_json(m2[5])
#data6 = pd.DataFrame(df6)

#frames = [df1, df2, df3, df4, df5, df6]
#frames = [data1, data2, data3, data4, data5, data6]

#result7 = pd.concat(frames)

#for kerek in m2:
#    df.append(pd.read_json(kerek))
#data10 = pd.DataFrame(df)

#i = 0
#result9 = pd.DataFrame()
#while i < len(m2):
#    df2 = pd.read_json(m2[i])
#    data2 = pd.DataFrame(df2)
#    df.append(df2)
#    frames = [data1, data2]
#    result9 = pd.concat(frames)
#    i = i + 1
    
#data11 = pd.DataFrame(df)    
   # df1.append(df2, ignore_index = True)
  
    
#df = DataFrame(my_dataframe2)
#my_dataframe1 = json.loads(m1)     error

#data = pd.DataFrame(my_dataframe2)
#data = pd.DataFrame(df1)
#data.to_csv('Results3.csv')



#print(m2)
#print(m1)
#print(type(my_dataframe3))
#print(type(my_dataframe2))
#print(type(df))
























print("fsyo!")
#data.to_csv('Results.csv')


















































