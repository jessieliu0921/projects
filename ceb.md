
# Task 1: FILTER CITY NAMES
---
###### AIM: filter out common words in city names; large amount
###### LANGUAGE: pseudo code in python syntax
###### ENV SUGGESTION: Linux(since with a considerable amount of data)
###### MY QUESTION: how many cities are left after filtering is desirable



###### Algorithm in pseudo code:
---




### STEP1: Load library, file of city names as city_names
```
from nltk import stopwords
```

### STEP2: Define common words AND exclude popular city names.

Use the stopwords corpus(words with higher frequency but less value) in nltk library to define common words
At the same time, exclude popular city names.

### STEP3: Cross check with original list and return the list of filtered cities
I personally define important cities as cities with good enough amount #of population.

City and its population data are acquired from UN website，sorted by #population, depending on the desired number of cities left, take the #probably first 5,000 ones.
```

popular_city = UN_city[0,5000]

#Then do the cross check work

def common words(city_names):
    city_names = set(city.lower for city in city_names if city.isalpha())
    common_wd = set(wd.lower() for wd in stopwords.words('english'))

    #leave out the city with common words
    unusual_name = common_wd.difference(popular_city)
    filtered_city = city.names.difference(popular_city)

    #sort the filtered city
    filtered_city = sorted(filtered_city )
return filtered_city
```








---





# Task2: MATCH NAME WITH EMAIL ADDRESS
---
###### AIM: predict names from email addresses
###### LANGUAGE: pseudo code in python syntax
###### ENV SUGGESTION: Linux(since with a considerable amount of data)



###### Algorithm in pseudo code:
---


### STEP1: Extract key info from email addresses

This step mainly deal with format.
```
email_array = cPickle.load(sourcefile)
```
Get rid of the string after @ and numbers in the email addresses.
```
def extract_name(self, email_add):
    extr_string = email_add.split('@')[0]
    extr_string = re.sub('[0-9]{1,}', ' ', extr_string)

```

When special symbols are encountered, split into words and return a list of predicted names.

```
    if ('.' in extr_string):
        pred_names = extr_string.split('.')
    elif ('_' in base_string):
        pred_names = extr_string.split('_')
    elif ('-' in base_string):
        pred_names = extr_string.split('-')
    else:
        pred_names = extr_string

    if len(names) <= 0:
        pred_names = [extr_string]

    pred_names = pred_names[0][0].capitalize()
    pred_names = pred_names[1][0].capitalize()

    log = {}
    log[' '.join.pred_names] = email_add

    
    return pred_names
```
### STEP2: Use the predicted names to match the original name list

Iterate letter by letter to find match in the given name list.
If first name matches, then proceed to match last name.
If birthday info is also available, try to get them and do more matches.

```
name_email_dic = {}
for real_name in name_list:
  if pred_names[0] in real_name:
      if pred_names[1] in real_name:
      name_email_dic[real_name] = log[pred_names] 

```
### STEP3: For the rest of those who doesn't have a match step 2(hopefully not too much), try match their email using web crawl.
