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
    payload = {}
    headers= {}
    response = requests.request("GET", url, headers=headers, data = payload)
    
    my_dict = json.loads(response.text)
    new_dict = tuzeu(my_dict)
    m2.append(new_dict)
    
my_df = pd.DataFrame(m2)
my_df.to_excel('Card_Results_21.xls')

print("fsyo!")



