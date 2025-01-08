<div align="center">  
  <h1>Book Recommendation System Using Collaborative and Content-Based Filtering</h1>  
</div>

<div align="center">  
  <h2>Project Overview</h2>
</div>

Recommendation systems are a type of information filtering system designed to suggest specific items to users. These systems are applied across various domains such as movies, music, news, books, and products [1]. A book search recommendation system is important for narrowing down large datasets, making the book search process more efficient compared to traditional syntax-based search methods. The goal of developing such a system is to help users easily find relevant references that meet their needs [2]. Recommendation systems typically use two main techniques for filtering information: Content-based filtering and Collaborative filtering. Content-based filtering recommends items to users that are similar in content to those they have already interacted with [3]. Collaborative filtering, on the other hand, predicts a user's interests based on data from multiple users, leveraging their preferences or tastes (collaboration) [4]. This project aims to develop a book recommendation system using both content-based and collaborative filtering techniques. The goal is to enhance the user experience by providing personalized book suggestions based on their preferences and interactions with books, making the search and discovery process more effective and engaging.

---

**Reference :**

[1] P. Mathew et al., ["Book Recommendation System through content based and collaborative filtering method"](https://ieeexplore.ieee.org/abstract/document/7684166) International Conference on Data Mining and Advanced Computing (SAPIENCE), Ernakulam, India, 2016.

[2] Missi Hikmatyar and Ruuhwan, ["Book Recommendation System Development Using User-Based Collaborative Filtering"](https://iopscience.iop.org/article/10.1088/1742-6596/1477/3/032024/meta) IOP Publishing, Vol. 1477, 2020.

[3] Avi Rana and K. Deeba, ["Online Book Recommendation System using Collaborative Filtering (With Jaccard Similarity)"](https://iopscience.iop.org/article/10.1088/1742-6596/1362/1/012130/meta) Journal of Physics: Conference Series, Vol. 1362, 2019.

[4] Okon Emmanuel et al., ["An Improved Online Book Recommender System using Collaborative Filtering Algorithm"](https://www.researchgate.net/publication/324897120_An_Improved_Online_Book_Recommender_System_using_Collaborative_Filtering_Algorithm) International Journal of Computer Applications, Vol. 179, 2018. 

<div align="center">  
  <h2>Business Understanding</h2>
</div>

### Problem Statements
1. How can book recommendations be provided based on the content preferences of users?
2. How can book recommendations be generated by analyzing ratings from other users with similar interests?

---

### Goals
1. Develop a system that provides book recommendations based on the similarity of content (such as title, author, publisher, and genre) with books previously interacted with by the user.
2. Create a recommendation system that leverages ratings and preferences of similar users to predict and suggest books that a user may like, even without direct interaction with those books.

---

### Solution Approach
1. Use book attributes (title, author, publisher) to recommend books similar to those the user has interacted with, by measuring content similarity using techniques like TF-IDF and cosine similarity.
2. Recommend books based on user ratings by analyzing patterns in user preferences, employing methods like user-based or item-based collaborative filtering.

<div align="center">  
  <h2>Data Understanding</h2>
</div>

### Dataset Description
The dataset available in Kaggle: [Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset). This dataset consists of 3 main files: Users, Books, and Ratings. The dataset provides valuable information for building recommendation systems for books. The Users dataset contains anonymized user IDs, along with demographic information such as location and age (if available). The Books dataset includes information about books, such as their ISBN (which uniquely identifies each book), book title, author, year of publication, publisher, and URLs for different image sizes of book covers. This dataset can be used for both content-based and collaborative filtering techniques in a recommendation system.

---

### Content
The dataset comprises 3 files.

- **Users :**
Contains the users. Note that user IDs (User-ID) have been anonymized and map to integers. Demographic data is provided (Location, Age) if available. Otherwise, these fields contain NULL-values.
- **Books :**
Books are identified by their respective ISBN. Invalid ISBNs have already been removed from the dataset. Moreover, some content-based information is given (Book-Title, Book-Author, Year-Of-Publication, Publisher), obtained from Amazon Web Services. Note that in case of several authors, only the first is provided. URLs linking to cover images are also given, appearing in three different flavours (Image-URL-S, Image-URL-M, Image-URL-L), i.e., small, medium, large. These URLs point to the Amazon web site.
- **Ratings :**
Contains the book rating information. Ratings (Book-Rating) are either explicit, expressed on a scale from 1-10 (higher values denoting higher appreciation), or implicit, expressed by 0.

In this project, only the Books and Ratings datasets will be utilized.
These two datasets will help in generating personalized book recommendations for users based on either the content attributes of the books (Content-Based Filtering) or the preferences of other users (Collaborative Filtering).

---

### Variable in the Dataset

**Books.csv**
- **ISBN :** A unique identifier for each book.
- **Book-Title :** The title of the book.
- **Book-Author :** The name of the book's author.
- **Year-Of-Publication :** The year the book was published.
- **Publisher :** The publisher of the book.
- **Image-URL-S :** The URL link to the small-sized image of the book cover.
- **Image-URL-M :** The URL link to the medium-sized image of the book cover.
- **Image-URL-L :** The URL link to the large-sized image of the book cover.

**Ratings.csv**
- **User-ID :** A unique identifier for each user who rated a book.
- **ISBN :** The unique identifier for the book that was rated.
- **Book-Rating :** The rating given by the user to the book. Ratings are on a scale of 1 to 10, where higher values represent a higher appreciation of the book. Implicit ratings are represented by 0.

---

### Exploratory Data Analysis

**- Information of Books data**
| Column               | Non-Null Count   | Dtype  |
|----------------------|------------------|--------|
| ISBN                 | 271360 non-null  | object |
| Book-Title           | 271360 non-null  | object |
| Book-Author          | 271358 non-null  | object |
| Year-Of-Publication  | 271360 non-null  | object |
| Publisher            | 271358 non-null  | object |
| Image-URL-S          | 271360 non-null  | object |
| Image-URL-M          | 271360 non-null  | object |
| Image-URL-L          | 271357 non-null  | object |

**- Information of Ratings data**
| Column       | Non-Null Count    | Dtype  |
|--------------|-------------------|--------|
| User-ID      | 1149780 non-null  | int64  |
| ISBN         | 1149780 non-null  | object |
| Book-Rating  | 1149780 non-null  | int64  |

**- Shape of Books and Ratings**

  Books :
  - Number of rows : 271360
  - Number of columns : 8

  Ratings :
  - Number of rows : 1149780
  - Number of columns : 3

---
### Visualization

**- Top 10 Books Based on the Most Ratings**

  ![top10books](https://github.com/user-attachments/assets/93197bdf-087f-45cc-b527-5871a394a252)

  The chart highlights "Wild Animus" as the most rated book, significantly surpassing others with nearly 2,500 ratings. Following it are "The Lovely Bones: A Novel" and "The Da Vinci Code," which also received substantial ratings but are notably lower than the top book. Other titles like "Divine Secrets of the Ya-Ya Sisterhood" and "The Red Tent" show moderate ratings, while "A Painted House", "The Secret Life of Bees" and "Snow Falling on Cedars" have fewer ratings. The presence of "nan" indicates missing or undefined book titles in the dataset.

**- Top 10 Authors Based on the Most Ratings**

  ![top10authors](https://github.com/user-attachments/assets/0b80b963-1825-4bb8-a401-62074cdb8edb)

  This visualization shows the top 10 authors based on the number of ratings. Stephen King ranks highest with nearly 10,000 ratings, indicating his immense popularity. At the bottom of the list is Janet Evanovich, with significantly fewer ratings compared to the others.

**- Top 10 Publishers Based on the Highest Number of Books**

  ![top10publisher](https://github.com/user-attachments/assets/6896e7b5-cf55-4e0a-a793-e8e2f6139d92)

  This pie chart shows the top 10 publishers based on the number of books published. Harlequin dominates with 20.1%, followed by Silhouette and Pocket at 11.2% and 10.4%, respectively. Meanwhile other publishers have smaller percentage.

**- Number of Ratings**

  ![numberofrating](https://github.com/user-attachments/assets/2730d1e2-b79c-4b74-a9d7-74834c01b43c)

  This pie chart illustrates the distribution of book ratings, categorizing them into high rating and low rating segments. 21.7% of the books have high ratings (greater than or equal to 5), indicating a significant portion of well-received titles. In contrast, 78.3% of the books fall into the low rating category (less than 5), suggesting that the majority of books are less favored by readers. This visualization highlights the disparity in reader.

<div align="center">  
  <h2>Data Preparation</h2>
</div>

### Content Based Filtering Preparation
**1. Merge datasets based on ISBN**

The ratings and books datasets are merged on the common column ISBN.

**2. Drop unnecessary columns**

The columns Image-URL-S, Image-URL-M, and Image-URL-L are removed as they are not necessary for the analysis.

**3. Fill missing values with "Unknown"**

For columns that may have missing values (like Book-Title, Book-Author, Year-Of-Publication, and Publisher), any missing entries are replaced with the string "Unknown" to avoid issues with incomplete data.

**4. Drop duplicate ISBN but keep the first record**

Any duplicate entries in the dataset based on the ISBN column are removed, keeping only the first occurrence. This ensures that there are no repeated book entries in the dataset.

---

### Collaborative Filtering Preparation
Ratings data is needed to train the model using collaborative filtering method, as it contains information about readers who rate the books they have read. This can serve as a recommendation system from one user to another user.

**1. Remove ratings of 0**

The ratings dataset is filtered to remove entries where the rating is 0, as these ratings indicate no preference from the user. This ensures that only meaningful ratings are used for training the model.

**2. Encode User-ID and ISBN**

User IDs and ISBNs are converted into unique numerical values through encoding. This process allows the collaborative filtering model to work with numeric data rather than string-based IDs.

**3. Shuffle data**

The data is shuffled to randomize the order of the entries, helping prevent any potential bias in the training process.

**4. Split data into training and validation sets**

The dataset is split into training and validation sets in an 80:20 ratio. This ensures that the model has enough data for training while still having a separate set to validate its performance.

<div align="center">  
  <h2>Modeling</h2>
</div>

### Model Development Content Based Filtering
Content-Based Filtering is a recommendation technique that suggests items to users based on the features or attributes of the items they have interacted with in the past. This method focuses on the content or characteristics of the items, such as genre, author, or description, and uses these features to recommend similar items. In the context of books, for instance, it would recommend books with similar titles, authors, or keywords based on the books that a user has rated highly.

Advantages of Content-Based Filtering:
- Since content-based filtering uses the specific preferences of the user, it can provide highly personalized recommendations.
- This method does not rely on the actions or preferences of other users, making it a good choice for new or niche items with limited user interaction.
- It’s easier to explain why a certain recommendation is made, as it’s based on the item’s characteristics (e.g., similar book genres, topics).

Disadvantages of Content-Based Filtering:
- The system can only recommend items that are similar to what the user has already interacted with. This can lead to a lack of diversity in recommendations and a "filter bubble."
- If a user hasn’t rated or interacted with many items, content-based filtering might struggle to make good recommendations.
- The quality of recommendations is highly dependent on the availability and richness of item attributes. Without good metadata (e.g., detailed descriptions, tags), recommendations may be less effective.

---

Before modeling, data sampling is performed due to the large volume of data. A sample of 20,000 records is taken to speed up the modeling process.

After sampling the data, a new column called 'content' is created by combining information from five columns: Book-Title, Book-Author, Publisher, and Year-Of-Publication. This new column provides a combined representation of each book’s metadata, which is useful for generating content-based recommendations.

After creating the 'content' column, TF-IDF (Term Frequency-Inverse Document Frequency) Vectorizer and Cosine Similarity is applied.

#### TF-IDF Vectorizer

TF-IDF (Term Frequency-Inverse Document Frequency) is a statistical measure used to evaluate how important a word is to a document in a collection or corpus. It is commonly used in text mining and information retrieval. The TF-IDF value is higher for words that appear frequently in a specific document but not across many other documents, signaling that the word is significant to that document.

Formula:
1. **Term Frequency (TF)**:

  $`\text{TF}(t) = \frac{\text{Number of times term t appears in a document}}{\text{Total number of terms in the document}}`$

2. **Inverse Document Frequency (IDF)**:\

  $`\text{IDF}(t) = \log \left( \frac{\text{Total number of documents}}{\text{Number of documents containing term t}} \right)`$

3. **TF-IDF Calculation**:

  $`\text{TF-IDF}(t) = \text{TF}(t) \times \text{IDF}(t)`$

How it works:
- High TF-IDF score: Indicates that the term is important to the document and relatively rare across other documents.
- Low TF-IDF score: Indicates that the term is common across many documents, and hence less important for distinguishing one document from others.

---

#### Cosine Similarity
Cosine similarity is a metric used to measure how similar two vectors are, irrespective of their size. It is commonly used in text mining and recommendation systems to measure the similarity between two documents (or two items) based on their vector representations. Cosine similarity ranges from -1 (completely dissimilar) to 1 (completely similar).

Formula:

$`\text{Cosine Similarity}(A, B) = \frac{A \cdot B}{\|A\| \|B\|}`$

Where:
- A . B is the dot product of two vectors A and B.
- ||A|| and ||B|| are the magnitudes (Euclidean norms) of vectors A and B, respectively.

How it works:
- When two items are similar in content (such as two books with similar keywords or topics), their vector representations will have a cosine similarity score closer to 1.
- When the items are dissimilar, the cosine similarity will approach 0 or even negative values in the case of complete dissimilarity.
Cosine similarity is particularly useful in content-based filtering when comparing documents or items (e.g., books) based on their TF-IDF vector representations. It helps determine how closely related two items are based on the terms they share.

---

#### Result
**Recommendation for the book "The White Wolf"**

Suppose a user is interested in the book The White Wolf. The system identifies other books in the dataset that share similar features, such as themes, authors, or publication characteristics. Based on these similarities, the system recommends the following books:

|    | Book-Title                                          | Book-Author         | Publisher              | Year-Of-Publication |
|----|-----------------------------------------------------|---------------------|------------------------|---------------------|
| 1  | King Charlie                                        | Max Brand           | Leisure Books          | 1997                |
| 2  | Mighty Lobo                                        | Max Brand           | Berkley Pub Group      | 1988                |
| 3  | Lawless Land (Silver Star Westerns)                 | Max Brand           | Warner Books           | 1984                |
| 4  | The Storytellers Handbook (Vampire)                 | Tony Harris         | White Wolf Pub         | 1995                |
| 5  | The Weird of the White Wolf                         | Michael Moorcock     | D A W Books, Incorporated | 1977              |
| 6  | Counterparts                                        | Nicholas Royle      | White Wolf Pub         | 1996                |
| 7  | Bloodwar: Masquerade of the Red Death (World of Darkness) | Robert Weinberg   | White Wolf Pub         | 1995                |
| 8  | Vampire: The Masquerade (Vampire)                   | Mark Rein-Hagen     | White Wolf Pub         | 1995                |
| 9  | Manon (Leisure Historical Romance)                  | Melanie Jackson     | Leisure Books          | 2000                |
| 10 | The Infinite (Leisure Horror)                       | Doug Clegg          | Leisure Books          | 2002                |


---

### Model Development Collaborative Filtering
Collaborative Filtering (CF) is a recommendation technique that makes predictions based on past interactions between users and items. It identifies patterns in user preferences and recommends items by finding similar users (user-based) or similar items (item-based). CF can be used without needing content information, relying solely on user-item interactions (such as ratings or clicks).

---

#### RecommenderNet
RecommenderNet is a deep learning-based model used for collaborative filtering. It uses neural networks to predict user-item interactions by learning from both user and item embeddings. RecommenderNet maps users and items into lower-dimensional vector spaces and computes the predicted ratings by learning from user-item interactions. The model improves by updating the embeddings during training.

Advantages of RecommenderNet
- Unlike traditional CF, RecommenderNet can capture complex, non-linear relationships between users and items using deep learning techniques.
- The model can handle large datasets effectively by learning embeddings, reducing the complexity of user-item matrices.
- RecommenderNet typically provides more accurate predictions due to the ability to learn detailed patterns from user-item interactions.

Disadvantages of RecommenderNet
- RecommenderNet needs a substantial amount of data to train effectively. With small datasets, it may not perform well.
- Training deep neural networks can be resource-intensive and requires significant computational power.
- Compared to traditional methods, deep learning models like RecommenderNet may take longer to train, especially with larger datasets.
---

#### Result
Showing recommendations for users 172865:

Top 5 books with the highest ratings from User 172865:

|    | ISBN        | Book-Title                                         | Book-Author        | Year-Of-Publication | Publisher                    |
|----|-------------|----------------------------------------------------|--------------------|---------------------|------------------------------|
| 1  | 0671014773  | Witchlight Night World 9 (Night World , No 9)     | L.J. Smith         | 1998                | Simon Pulse                  |
| 2  | 0671021338  | The Angel Chronicles, Volume 1                     | Nancy Holder       | 1998                | Simon Spotlight Entertainment |
| 3  | 0786817879  | Artemis Fowl (Artemis Fowl, Book 1)                | Eoin Colfer        | 2003                | Miramax Kids                 |
| 4  | 0061067121  | Secret Circle Vol I: The Initiation (Secret Circle)| L. J. Smith        | 1992                | Eos                          |
| 5  | 0440228158  | Ever After : A Cinderella Story (Laurel-Leaf Books)| WENDY LOGGIA        | 1998                | Laurel Leaf                  |

Top 10 book recommendations for User 172865:

|    | ISBN        | Book-Title                                               | Book-Author          | Year-Of-Publication | Publisher                     |
|----|-------------|----------------------------------------------------------|----------------------|---------------------|-------------------------------|
| 1  | 067168390X  | Lonesome Dove                                            | Larry McMurtry       | 1988                | Pocket                        |
| 2  | 0345339738  | The Return of the King (The Lord of the Rings, Vol 3)   | J.R.R. TOLKIEN       | 1986                | Del Rey                       |
| 3  | 0439139597  | Harry Potter and the Goblet of Fire (Book 4)             | J.K. Rowling         | 2000                | Scholastic                    |
| 4  | 0439136369  | Harry Potter and the Prisoner of Azkaban (Book 3)        | J.K. Rowling         | 2001                | Scholastic                    |
| 5  | 0140143505  | 84 Charing Cross Road                                    | Helene Hanff         | 1990                | Penguin Books                 |
| 6  | 043936213X  | Harry Potter and the Sorcerer's Stone (Book 1)           | J.K. Rowling         | 2001                | Scholastic                    |
| 7  | 0618002235  | The Two Towers (The Lord of the Rings, Part 2)           | J.R.R. Tolkien       | 1999                | Houghton Mifflin Company      |
| 8  | 0836220889  | Calvin and Hobbes                                        | Bill Watterson       | 1987                | Andrews McMeel Publishing     |
| 9  | 0743454529  | My Sister's Keeper : A Novel (Picoult, Jodi)             | Jodi Picoult         | 2004                | Atria                         |
| 10 | 0439425220  | Harry Potter and the Chamber of Secrets Postcard Edition | J.K. Rowling         | 2002                | Scholastic                    |

<div align="center">  
  <h2>Evaluation</h2>
</div>

### Content Based Filtering
After the book recommendation function is applied, the results are evaluated using the Precision at K metric.

**Precision at K** is an evaluation metric used to assess the quality of recommendations in a recommendation system. Precision at K measures how many of the recommended items in the top-K recommendations are relevant (correct) according to the user's preferences or needs.

**Formula :**

$`\text{Precision at K} = \frac{\text{Number of relevant recommendations in the top K recommendations}}{K}`$


The result of Precision at 5 is 0.80, it means that 80% of the top 5 recommended books are relevant to the user's interests. In other words, out of the 5 recommended books, 4 are relevant (matching the relevant_books list), and 1 is not relevant.

In general, the higher the Precision at K value, the better the recommendation system is at providing results that match the user's expectations. A result of 0.80 suggests that the recommendation system is performing well, with most of the recommendations being relevant.

---

### Collaborative Filtering
After training the model, the model is evaluated using the RMSE and MAE metrics. The results are as follows: the RMSE is 0.1944, and the MAE is 0.1502.

**1. RMSE (Root Mean Squared Error)**

RMSE is the square root of MSE and measures the prediction error in the same units as the original data. RMSE provides a clearer picture of both large and small model errors.

Formula :

$`RMSE = \sqrt{MSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}`$

Where:  
- $`y_i`$ is the actual value  
- $`\hat{y}_i`$ is the predicted value  
- $`n`$ is the number of data points

In this case, the RMSE = 0.1944, which means the model’s predictions, on average, deviate from the actual ratings by approximately 0.19. This is a good indication that the model’s predictions are relatively close to the true values, but still with some room for improvement.

**2. MAE (Mean Absolute Error)**

MAE measures the average absolute difference between the predicted values and the actual values. The lower the MAE value, the better the model is at making accurate predictions.

Formula :

$`MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|`$  

Where:  
- $`y_i`$ is the actual value  
- $`\hat{y}_i`$ is the predicted value  
- $`n`$ is the number of data points 

In this case, the MAE = 0.1502, which means that, on average, the model's predictions are off by 0.15 ratings. This suggests that while the model is not perfect, it is making fairly accurate predictions overall.