# Final Project

**1. Research questions**  
As a music lover, I am a fan of Vietnamese music in its so-called “golden age” between 1945 and 1975. During this era, three musicians - Pham Dinh Chuong, Trinh Cong Son, and Lam Phuong - stood out as some of the most influential figures in the Vietnamese music industry thanks to their immensely popular compositions. By obtaining information about the songs written by these musicians, I aim to answer the following Humanities questions: 
  1. What is the most productive period of the musicians' song-writing career in the golden days of Vietnamese music from 1945 to 1975?
  2. Between 1945 and 1975, were there any changes in the topics of the songs written in their most productive period compared to those written in the periods before and after that?
  
Besides the two main questions, I also have a hypothesis that their most productive period commenced around 1956, which is the year when Sai Gon (now Ho Chi Minh City) welcomed an influx of migrants from the North of Vietnam. Among those migrants were elite artists and middle-class people who contributed to the diverse picture of the art and entertainment industry in the South of Vietnam. Hypothetically, I believe that the newcomers from the North created a higher demand for entertainment products in general and music in particular. There is also a chance that the Northern elite artists encouraged the dissemination of the culture of listening to music. If the results of my research indicate that the most productive period of the three musicians correlated with this great migration of Northern Vietnamese people, it will be interesting to do a network analysis to study about the connections between musicians, artists, singers, intellectuals, record companies, music bar owners, and middle and upper-class people in Sai Gon around the year 1956. Doing so would hopefully result in a better understanding of the cultural life in Sai Gon before Vietnam gained its independence from the U.S.A in 1975.

**2. Data colection**
My preliminary search for data resulted in three wiki pages that are useful for this project. The wiki pages contain a list of songs written by the three musicians and the years in which they were written. Originally, my intention was to use OpenRefine to extract the necessary information from the wiki pages to create a useful dataset. However, due to my lack of experience with OpenRefine and the fact that the ways information is displayed on the three wiki pages are so different, I was unsuccessful at carrying out my original plan. I figured that even if it were possible for me to process one wiki page, I would not be able to apply the same operation to any of the other two pages. At this point, it would be a waste of time to continue with OpenRefine. As a result, I decided to manually create a Microsoft Excel file in which there are details about the songs written by the musicians. After that, I converted the Excel file into a CSV file so that I could use Python to analyze the data. 

**3. Data processing**
First of all, I imported the pandas library, which would allow me to open and work with the CSV file I created previously. The codes are as followed:
  ```
  import pandas as pd
  import re
  data = pd.read_csv("song_data.csv", low_memory=False)
  ```
To quickly count the number of songs written by each musician, I used this code:
  ```
  data['writer'].value_counts()
  ```
The results showed that from 1945 to 1975, Trinh Cong Son wrote the most songs (with 74 songs written), followed by Lam Phuong (45 songs), and Pham Dinh Chuong (39 songs). 

After identifying their most productive periods, I will search for the lyrics of the songs written in those periods and in the beginning stage of their career. Then, I will combine the results of my search into two Microsoft Word documents for each musician. One document will be used to store the lyrics of the songs written in the most productive period and the other for the beginning period. Next, I will process the documents with Voyant so that I can see the topics in the songs. Finally, I will make comparisons of the topics based on Voyant's results.
