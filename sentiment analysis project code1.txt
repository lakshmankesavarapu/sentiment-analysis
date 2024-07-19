import pandas as pd
data=pd.read_csv("Reviews.csv")
print(data)
data
data.head()
data.tail()
data.head(10)
data.tail(10)
data.info()
data.isnull().sum()
data.duplicated()
import seaborn as sns
import matplotlib.pyplot as plt
from wordcloud import WordCloud
combined_text=" ".join(data['Review']) #Combine all review text into one string
wordcloud=WordCloud(width=800,height=400,background_color='white').generate(combined_text)
plt.figure(figsize=(10,6))
plt.imshow(wordcloud,interpolation='bilinear')
plt.axis('off')
plt.title('Word Cloud of Reviews')
plt.show()
from collections import Counter
targeted_words=['good','great','amazing','bad','not bad']
all_words=" ".join(data['Review']).lower().split()     #flattened reviews into a single list of words
word_counts=Counter(all_words)
target_word_count={word:word_counts[word] for word in targeted_words}
#plotting
plt.figure(figsize=(8,6))
plt.bar(target_word_count.keys(),target_word_count.values(),color=['blue','green','orange','red','black'])
plt.xlabel('Words')
plt.ylabel('Frequency')
plt.title('Frequency of specific words in reviews')
plt.show()