# Discribe the dataset
This is a ECG dataset gain from 3 hospital
The data contain with the raw data of electrocardiogram and the label like sex, age, the illness that patient have.
Because of privacy and security issues, we can not put the data to public.
# Why it is important?
Cardiovascular disease is the leading cause of death around the world. High-quality ECG data promotes the ability of computerized interpretation of electrocardiogram. We build this dataset for the use of China ECG AI Contest (CEAC) 2019, more information can see from their website http://mdi.ids.tsinghua.edu.cn/#/
# slides
https://github.com/luochuankai-JHU/Decision-Analytics-Fundamentals/blob/master/Chuankai_Luo.pdf
please see the link above
# brief introduce about ECG data?
this is the shape of one heart beat in ECG report
![image](https://github.com/luochuankai-JHU/Decision-Analytics-Fundamentals/blob/master/image/heart%20beat.png)
and when we go to hospital, we can get a report like this from docter
![image](https://github.com/luochuankai-JHU/Decision-Analytics-Fundamentals/blob/master/image/report.jpg)
from the shape of your heart beat shown in ECG report, we can diagnose what disease you have.
# How many samples are in this dataset?
		15,357
		
# label distribution in this dataset (illness and age)?


		#-*- coding: UTF-8 -*-

		import numpy as np
		import pandas as pd 
		import seaborn as sns
		import matplotlib.pyplot as plt


		cgdata=pd.read_excel(r'F:\graduate\multilabel\ECG_z_cg\label_num_onehot.xlsx',sheet_name='Sheet2')
		plt.hist(cgdata['age'],bins=83,normed=1, facecolor= 'lightsteelblue',)
		plt.xlabel("age")
		plt.ylabel("frequency")
		plt.title("Age distribution map")
		plt.show()
we can use histogram to discribe it	
![image](https://github.com/luochuankai-JHU/Decision-Analytics-Fundamentals/blob/master/image/agedistribution.jpg)
		
# Correlation between various diseases and gender and age?	

		sns.violinplot(x="I-AVB", y="age", hue="sex", data=alln, split=True,
							inner="quart", palette={"MALE": "b", "FEMALE": "y"}) 
		sns.despine(left=True)
		plt.show()
we can use violine plot to discribe it
![image](https://github.com/luochuankai-JHU/Decision-Analytics-Fundamentals/blob/master/image/disease1.jpg)
![image](https://github.com/luochuankai-JHU/Decision-Analytics-Fundamentals/blob/master/image/disease2.jpg)
![image](https://github.com/luochuankai-JHU/Decision-Analytics-Fundamentals/blob/master/image/disease3.jpg)
# Correlation between various diseases and diseases?

		corr = cgdata.corr(method='spearman')  
		cgdata1 = cgdata.drop(columns=['age'])
		cov = cgdata1.cov() 
we can draw a form
or statistics simultaneously appear![image](https://github.com/luochuankai-JHU/Decision-Analytics-Fundamentals/blob/master/image/corr.png)
# algorithm that suit for this dataset to make classification
Multi-Feature Multi-Label algorithm
（MFML）
which have a F1 score as 0.86
![image](https://github.com/luochuankai-JHU/Decision-Analytics-Fundamentals/blob/master/image/algr.png)
