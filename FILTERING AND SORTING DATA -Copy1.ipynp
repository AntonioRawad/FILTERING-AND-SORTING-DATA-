#!/usr/bin/env python
# coding: utf-8

# # Ex1 - Filtering and Sorting Data
# 
# Check out [Chipotle Exercises Video Tutorial](https://youtu.be/ZZPiWZpdekA) to watch a data scientist go through the exercises

# This time we are going to pull data directly from the internet.
# Special thanks to: https://github.com/justmarkham for sharing the dataset and materials.
# 
# ### Step 1. Import the necessary libraries

# In[1]:


import pandas as pd


# ### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/justmarkham/DAT8/master/data/chipotle.tsv). 

# ### Step 3. Assign it to a variable called chipo.

# In[9]:


url = 'https://raw.githubusercontent.com/justmarkham/DAT8/master/data/chipotle.tsv'

chipo = pd.read_csv(url, sep = '\t')


# ### Step 4. How many products cost more than $10.00?

# To clean the item_price column and transform it into a float, we can use the following code:
# 

# In[10]:


prices = [float(value[1:-1]) for value in chipo.item_price]
chipo.item_price = prices


# Next, we can remove duplicates in item_name and quantity using the drop_duplicates method:

# In[11]:


chipo_filtered = chipo.drop_duplicates(['item_name', 'quantity', 'choice_description'])


# we select only the products with quantity equals to 1:

# In[14]:


chipo_one_prod = chipo_filtered[chipo_filtered.quantity == 1]


# To calculate the price per item, we can create a new column price_per_item:

# In[23]:


chipo_one_prod.loc[:, 'price_per_item'] = chipo_one_prod['item_price'] / chipo_one_prod['quantity']



# In[ ]:


Finally, we can count the number of unique item names that have a price per item greater than 10:


# In[22]:


chipo_one_prod[chipo_one_prod['price_per_item'] > 10].item_name.nunique()


# In[ ]:





# ### Step 5. What is the price of each item? 
# ###### print a data frame with only two columns item_name and item_price

# In[24]:


# delete the duplicates in item_name and quantity
# chipo_filtered = chipo.drop_duplicates(['item_name','quantity'])
chipo[(chipo['item_name'] == 'Chicken Bowl') & (chipo['quantity'] == 1)]

# select only the products with quantity equals to 1
# chipo_one_prod = chipo_filtered[chipo_filtered.quantity == 1]

# select only the item_name and item_price columns
# price_per_item = chipo_one_prod[['item_name', 'item_price']]

# sort the values from the most to less expensive
# price_per_item.sort_values(by = "item_price", ascending = False).head(20)


# ### Step 6. Sort by the name of the item

# In[25]:


chipo.item_name.sort_values()

# OR

chipo.sort_values(by = "item_name")


# ### Step 7. What was the quantity of the most expensive item ordered?

# In[26]:


chipo.sort_values(by = "item_price", ascending = False).head(1)


# ### Step 8. How many times was a Veggie Salad Bowl ordered?

# In[27]:


chipo_salad = chipo[chipo.item_name == "Veggie Salad Bowl"]

len(chipo_salad)


# ### Step 9. How many times did someone order more than one Canned Soda?

# In[28]:


chipo_drink_steak_bowl = chipo[(chipo.item_name == "Canned Soda") & (chipo.quantity > 1)]
len(chipo_drink_steak_bowl)

