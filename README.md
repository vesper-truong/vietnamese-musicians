# Final Project

**1. Research questions**  

As a music lover, I am a fan of Vietnamese music in its so-called “golden age” between 1945 and 1975. During this era, three musicians - Trinh Cong Son (1939-2001), Lam Phuong (born 1937), and Pham Dinh Chuong (1929-1991) - stood out as some of the most influential figures in the Vietnamese music industry thanks to their immensely popular compositions. By obtaining information about the songs written by these musicians, I aim to answer the following Humanities questions: 
  1. What is the most productive period of the musicians' song-writing career in the golden days of Vietnamese music from 1945 to 1975?
  2. Between 1945 and 1975, were there any changes in the topics of the songs written in their most productive period compared to those written in the period before that?
  
Besides the two main questions, I also have a hypothesis that their most productive period commenced around 1956, which is the year when Sai Gon (now Ho Chi Minh City) welcomed an influx of migrants from the North of Vietnam. Among those migrants were elite artists and middle-class people who contributed to the diverse picture of the art and entertainment industry in the South of Vietnam. Hypothetically, I believe that the newcomers from the North created a higher demand for entertainment products in general and music in particular. There is also a chance that the Northern elite artists encouraged the dissemination of the culture of listening to music. If the results of my research indicate that the most productive period of the three musicians correlated with this great migration of Northern Vietnamese people, it will be interesting to do a network analysis to study about the connections between musicians, artists, singers, intellectuals, record companies, music bar owners, and middle and upper-class people in Sai Gon around the year 1956. Doing so would hopefully result in a better understanding of the cultural life in Sai Gon before Vietnam defeated the US Army to unite its northen and southern parts in 1975.

**2. Data collection**

My preliminary search for data resulted in three wiki pages that are useful for this project. Each wiki page contains a list of songs written by each musician and the years in which they were written. I acknowledge the fact that using Wikipedia as a datasource is problematic, especially because the information on the wiki pages is incomplete and always subject to changes. It is said on the wiki pages themselves that the song lists are not finished and there are songs with unknown production years. Consequently, this unknown variable will have an influence on my analysis. Therefore, the result of my project should be treated as an attempt to get a better understanding of the Vietnamese music industry in the period from 1945 and 1975. More importantly, the project is expected to result in a pipeline that is applicable to a better dataset to answer (similar) research questions. 

Originally, my intention was to use OpenRefine to extract the necessary information from the wiki pages to create a useful dataset. However, due to my lack of experience with OpenRefine and the fact that the ways information is displayed on the three wiki pages are so different, I was unsuccessful at carrying out my original plan. I figured that even if it were possible for me to process one wiki page, I would not be able to apply the same operation to any of the other two pages. At this point, it would be a waste of time to continue with OpenRefine. As a result, I decided to manually create Microsoft Excel files in which there are details about the songs written by the musicians. After that, I converted the Excel files into CSV files so that I could use Python to analyze the data.  
  

**3. Data processing**

First of all, I imported the pandas library, which would allow me to open and work with the CSV files I created previously. The codes are as followed:
  ```
  import pandas as pd
  data = pd.read_csv("song_data.csv", low_memory=False)
  ```
To quickly count the number of songs written by all the musicians, I used the value_counts() method:
  ```
  data['writer'].value_counts()
  ```
The results showed that from 1945 to 1975, Trinh Cong Son wrote the most songs (with 74 songs written), followed by Lam Phuong (45 songs), and Pham Dinh Chuong (39 songs). In sum, they wrote 158 songs within the span of 20 years. This number does not include the songs with unknown production dates or those that are banned from public release by the Vietnamese government due to political reasons.

Using a similar line of code, I was able to obtain information regarding how many songs were written in a particular year in the studied period of time (1945-1975).
  ```
  data['year'].value_counts()
  ```
After running the code, I learned that most songs were written in the period between 1968 and 1969, with 34 songs in total. This accounts for over 20% of all the songs written by the three musicians. With 19 songs each, 1965 and 1972 were also the two years when the musicians were very productive.

Next, in order to study each musician, I opened the CSV file for Trinh Cong Son, Lam Phuong, and Pham Dinh Chuong consecutively.
  ```
  tcs_data = pd.read_csv("tcs_song_data.csv", low_memory=False)
  lp_data = pd.read_csv("lam_phuong_song_data.csv", low_memory=False)
  pdc_data = pd.read_csv("pdc_song_data.csv", low_memory=False)
  ```
Again, with the value_counts() method, it was possible to see how many songs were written by each musician in a particular year.
  ```
  tcs_data['year'].value_counts()
  lp_data['year'].value_counts()
  pdc_data['year'].value_counts()
  ```
After this step, it was finally possible to see which were the years in which Trinh Cong Son, Lam Phuong, and Pham Dinh Chuong were most productive in their song-writing profession. With the CSV files I created, I was also able to use RAW to visualize the data so that I could understand it better. The results of the RAW visualization process can be found in the ***visualization_RAW*** folder in this repository.

Having identified their most productive periods, I then searched for the lyrics of the songs written in those periods and in the earlier stage of their career. The lyrics were obtained from [(lyrics.vn)]. Next, I compiled the results of my search into plain text documents for each musician. After that, I processed the documents using Voyant Tools (available at https://voyant-tools.org) so that I could see the topics in the songs. Finally, I made comparisons of the topics based on Voyant's results.

**4. Analysis**

**4.1 The most productive periods**

After processing the data, it would be possible to answer the first research question: what is the most productive period of the musicians' song-writing career in the golden days of Vietnamese music from 1945 to 1975?. Apparently, Trinh Cong Son was most productive in the five-year period between 1968 and 1972, during which he wrote 45 songs. Almost one-fifth of his songs were composed in 1972. Statistically, his peak in song-writing productivity began at the age of 29. As for Lam Phuong, his most productive period was between 1956 and 1960, during which 19 songs were written. 1957 marked the most productive year for Lam Phuong with 7 songs produced. Compared to Trinh Cong Son, Lam Phuong reached the high of his productivity at a much younger age - at only 19 years old. Regarding Pham Dinh Chuong, no period was especially remarkable in terms of song-writing. Nevertheless, it can be seen that there is a period of regular song production from 1952 to 1957, during which he wrote two to three songs each year (with the exception of 1955). Pham Dinh Chuong was only a 23-year-old man in 1952.   

**4.2 Comparison of song topics**

In this project, I used Voyant Tools to answer the second research question: Between 1945 and 1975, were there any changes in the topics of the songs written in their most productive period compared to those written in the period before that?

With the help of Voyant Tools, I could use the visualization tools and corpus tools to get an understanding of the topics of the songs. 

It is possible to explore the Voyant results at: https://vesper-truong.github.io/vietnamese-musicians/

**4.2.1 Trinh Cong Son**

Below are the results of the topics in the songs in Trinh Cong Son's most productive period from 1968 to 1972. The 45 songs written in this period account for over 60% of all the songs Trinh Cong Son wrote in the whole twenty-year period of Vietnamese music industry's golden age (from 1945 to 1975):

<iframe style='width: 100%; height: 800px;' src='//voyant-tools.org/?panels=cirrus%2Creader%2Ctrends%2Csummary%2Ccontexts&corpus=3b97135efa669b687e9c13171ff3e4e5'></iframe>


The corpus has 45 documents, each of which contains the lyrics of a song written in the period between 1968 and 1972. As it was not possible to identify the main topic in Trinh Cong Son's songs just by looking at the most frequently used words in the corpus, I decided to study the distinctive words in the documents (compared to the rest of the corpus). Because in Vietnamese, a meaningful word can be made up of two separate words (e.g. tuổi trẻ (youth) is made up of two separate words 'tuổi' and 'trẻ'), there is a need to use the *Contexts tool* on Voyant Tools to see the words in their contexts. By doing so, it would be possible to see the correct distinctive words. The top distinctive words are: chết (dead/death), sống (live), đường (way), đồng bào (compatriot), tuổi trẻ (youth), Việt Nam, tình (love), máu (blood), hoà bình (peace), dân (people), quê hương (hometown), xác (corpse), cờ (flag), ngày mai (tomorrow). The top distinctive words are: chết (dead/death), sống (live), đường (way), đồng bào (compatriot), tuổi trẻ (youth), Việt Nam, tình (love), máu (blood), hoà bình (peace), dân (people), quê hương (hometown), xác (corpse), cờ (flag), ngày mai (tomorrow). These words indicate that the main topics in Trinh Cong Son's songs written in the period between 1968 and 1972 were patriotism, fighting for peace, life and death.

I decided to compared Trinh Cong Son’s songs in his prime time with those written in the five-year period from 1958 to 1962 as there is no information about any song written before 1958. Another reason is that I wanted to match the length of the most productive period with that of the earlier stage of his career for better comparison. Below are the results of the topics in Trinh Cong Son's songs in the period from 1958 to 1962:

<iframe style='width: 100%; height: 800px;' src='//voyant-tools.org/?panels=cirrus%2Creader%2Ctrends%2Csummary%2Ccontexts&corpus=c5dcff834ae319a7580a94dc3089c0f1'></iframe>


Compared to the songs written in the musician's most productive period, those written in the five-year period from 1958 to 1962 seem to revolve around the topic of love and missing. This is deduced from the most frequent words in the corpus. From 1958 to 1962, Trinh Cong Son tended to use words such as mưa (rain), nhớ (miss), đêm (night), buồn (sad), thương (love), and especially the pronoun *em* which is often used to dearly address a younger person in Vietnamese.

Clearly, there was a distinct shift in topics in Trinh Cong Son's songs in the period from 1958 to 1962 compared to his most productive period.

**4.2.2 Lam Phuong**

Below are the results of the topics in the songs in Lam Phuong's most productive period from 1956 to 1960. During this period, the musician wrote 19 songs, which constitute approximately two-fifths of all the songs written by Lam Phuong (in the context of this study). Four songs were not included in the corpus as it was impossible to find their lyrics. Despite this loss, the results are expected to be affected at a very slight degree:

<iframe style='width: 100%; height: 800px;' src='//voyant-tools.org/?panels=cirrus%2Creader%2Ctrends%2Csummary%2Ccontexts&corpus=6543956fe6d9adf7de31ebaccc4e5f3c'></iframe>


Once again, I used a combination of tools offered by Voyant Tools such as *Summary* and *Contexts* to grasp a picture of the topics in Lam Phuong songs written in his most productive period. The top five frequent words (excluding pronouns) are: ơi (an exclamatory word in Vietnamese), đêm (night), về (go back), tình (love), lòng (equivalent to *heart*). Some of the top distinctive words are: đông (winter), nhớ (miss), mưa (rain), quê (hometown). Although the context of the words are not clear, it can be inferred that the topics in Lam Phuong's songs in this period were about sad longing feelings.

Below are the results of the topics in Lam Phuong's songs in the period from 1952 to 1954 - the beginning of his song-writing career. Unfortunately, it was also impossible to find the lyrics to one song in this period, but this would probably have very little effect on the results:

<iframe style='width: 100%; height: 800px;' src='//voyant-tools.org/?panels=cirrus%2Creader%2Ctrends%2Csummary%2Ccontexts&corpus=83a4abf5e5a622b801be7173db3c7403'></iframe>


A look at the most frequent and distinctive words lead me to notice that there are several nouns such as trăng (moon), lúa (rice plants), tình (love), tiếng (sounds), sông (river), rừng (forest), lửa (fire), thu (autumn). Based on these words, it is possible to suspect that the topics in Lam Phuong's songs in this period circle around the nature and the Vietnamese countryside.

In comparison, without the presence of negativity-inducing words (e.g. rain, winter), it appears that the topics in Lam Phuong's beginning stage of his career were more optimistic.

**4.2.3 Pham Dinh Chuong**

Regarding Pham Dinh Chuong, I examined the songs written in his supposedly most productive period from 1952 to 1957, which was also the period when he regularly produced songs as stated above. Then, I compared the topics of the songs in this period with those of the songs written between 1946 and 1951. One major problem with this musician is that there was no lyric found for 8 out of 22 songs studied. This accounts for almost one-third of the songs, which means the results are heavily affected. Nevertheless, it is still possible to load the corpus via Voyant Tools. Below are the results for the 1952-1957 period:

<iframe style='width: 100%; height: 800px;' src='//voyant-tools.org/?panels=cirrus%2Creader%2Ctrends%2Csummary%2Ccontexts&corpus=26c5842992482ecb938a0bba239728fd'></iframe>


It can be seen that two exclamatory words *hò* and *dô* were frequently used in the songs in this period. These two words are often used to give people motivation among Vietnamese laborers. Lúa (rice plants), sông (river), and xuân (spring) are also among the top ten most frequent words (excluding pronouns). It can be inferred that the common topics in this period are about the joy of labor and celebrating spring time. Nevertheless, this should not be regarded as a definite conclusion as there is a lack of data as explained above.

Among the three musicians, Pham Dinh Chuong appeared to have started his song-writing career at the earliest time. Pham Dinh Chuong was among the first pioneers of Vietnamese music in its golden age from 1945 to 1975. His first documented song was composed in 1946. This is probably due to the fact that he was born in 1929, which created a huge age gap between him and the other two musicians. Below are the results of the topics in Pham Dinh Chuong's songs in the period from 1946 to 1951:

<iframe style='width: 100%; height: 800px;' src='//voyant-tools.org/?panels=cirrus%2Creader%2Ctrends%2Csummary%2Ccontexts&corpus=186b7d8ff3e7ed294f0d869a30578e47'></iframe>


With only 4 songs in the corpus, it is difficult to deduce the topics of Pham Dinh Chuong's songs in this period. The most noticeable and meaningful word in the most frequent word list is tình (love), which surprisingly is not a frequently used word in the songs written between 1952 and 1957.

**5. Discussion**

First of all, the results of the analysis indicate that my hypothesis may not be correct as their most productive periods did not happen around the year 1956. Rather, the results suggest that I should hypothesize that the musicians' most productive periods began after the year 1956 when there were remarkable changes in the population of well-cultured people in the South of Viet Nam. Second, among the three musicians, Trinh Cong Son reached his most productive period at the latest age, at 29 compared to 19 (Lam Phuong) and 23 (Pham Dinh Chuong); however, the total number of songs he wrote in his prime time equals over half of the songs written by both Lam Phuong and Pham Dinh Chuong combined. Third, the most significant and noticeable change in topics was also evident in Trinh Cong Son's songs. In the beginning of his career, Trinh Cong Son had a tendency to write songs about romantic love and missing, but he switched to writing songs about patriotism, fighting for peace, life and death. This change may be attributed to the historical situations of the South of Viet Nam during that time. For example, 1968 was the year when the General Offensive and Uprising of Tet Mau Than broke out in Sai Gon (now Ho Chi Minh City - the center of the South of Viet Nam). From 1968, the Viet Nam war escalated until Viet Nam earned its victory over the U.S.A in 1975, uniting the North and the South of the country. This may also be an explanation to why Lam Phuong's songs seemed to become less optimistic as he progressed in his career. Finally, it was difficult to identify any remarkable shift in Pham Dinh Chuong's song topics, which implies that there is a dire need for more information and a better datasource. 

**6. Limitations**

Compared to the first draft of this project, I have made some significant changes both actively and compulsorily. Due to my inexperience with OpenRefine, I had to manually collect the necessary data from the wiki pages. Fortunately, doing so enabled me to adopt a different approach with which I am more familiar - Python. Thanks to Python, I was able to promptly analyze the data and extract the information I need from  my manually created CSV files. I also decided against using TimeGraphics (available at https://time.graphics/) for visualizations. Instead, I chose RAW, which is a tool presented in one of the in-class meetings. Limited though my experience with RAW is, I was still able to make use of the tool according to my need. I applied RAW to the CSV file of each musician consecutively, not to the complete *song_data.csv* because it appears to me that including too many variables will just make the visualization messy and that will prevent researchers to make sense of the graph. Voyant Tools was, to some extent, useful for getting a good understanding of the corpora. However, it seems to only offer a surface-level view, which makes it difficult for me to deduce the topics of the songs. Consequently, I had to refer to various tools offered by Voyant Tools before I could make a decision on the possible topics. Nevertheless, I cannot claim that I am completely certain about my conclusions. It would be beneficial if there were a tool to evaluate the probability. I wonder about the possibility of using a scale of certainty similar to the one developed in the Cinema Parisien 3D project (Noordegraaf, Opgenhaffen, and Bakker 2016, p. 53). The biggest issue in this project, however, is the datasource itself. Due to my lack of access to a better, more reliable datasource, I had to resort to using Wikipedia. Although wiki pages are conveniently accessible, their contents are not yet complete and they are always subject to changes. After my preliminary search, I found three wiki pages from which I could obtain a dataset. Acknowledging the fact that my dataset is quite small in size, I made efforts to add more variables to it. Nonetheless, there is still a dire need for a better, more detailed dataset.

**7. Conclusion**

In this project, I 

**References**

Noordegraaf, J., Opgenhaffen, L. & Bakker, N. 2016. Cinema Parisien 3D: 3D visualisation as a tool for the history of cinemagoing. *Alphaville, 11*, pp. 45-61.

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
