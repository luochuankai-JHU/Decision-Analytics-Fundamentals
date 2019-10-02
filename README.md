# Discribe the dataset
This is a ECG dataset gain from 3 hospital


# How many samples are in this dataset?
		data.shape
# label distribution in this dataset (illness and age)?
we can use histogram to discribe it

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
		
		
# Correlation between various diseases and gender and age?	
we can use violine plot to discribe it
		sns.violinplot(x="I-AVB", y="age", hue="sex", data=alln, split=True,
							inner="quart", palette={"MALE": "b", "FEMALE": "y"}) 
		sns.despine(left=True)
		plt.show()

# Correlation between various diseases and diseases?
we can draw a form
		corr = cgdata.corr(method='spearman')  
		cgdata1 = cgdata.drop(columns=['age'])
		cov = cgdata1.cov() 
