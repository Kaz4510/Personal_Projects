# Building NLP Applications with Hugging Face

Welcome! In this project, I will be learning how to perform common Natural Language Processing (NLP) tasks using Hugging Face. Some of these tasks include:
- **sentiment analysis** (i.e. categorizing text as negative or positive);
- **text embedding** (i.e. transforming a piece of text into a numerical, n-dimensional vector, representation);
- **semantic search** (i.e. matching a query with the most appropriate result based on embeddings);
- and more!

The dataset comes from "Rent the Runway" [link](https://cseweb.ucsd.edu//~jmcauley/datasets.html#clothing_fit) and is comprised of user reviews on clothing items, their ratings on fit, and other metadata about the user (i.e. gender, height, size, age, reason for renting) and the item (i.e. category). It is a nice mixture of data types, but most importantly, lots of text! 

In order to be successful, you should have:

**Intermediate knowledge of Python**
- list comprehension
- for loops and while loops
- installing packages
- creating and using functions
- using NumPy and Pandas

**Basic understanding of NLP**
- What it is
- Data preparation steps and why they're important
- Familiarity, though not necessarily expert proficiency, in some NLP tasks

## Task 0: Setup
For this project, we will need several Python packages:
- `pandas`
- `numpy`
- `datetime`
- `re`
- `string`
- `matplotlib.pyplot`
- `seaborn`
- `transformers`
- `sentence_transformers`

These packages will help us with the data preprocessing steps, visualization, and, of course, NLP tasks using Hugging Face (i.e. `transformers` and `sentence_transformers`).


## Task 1: Import the Runway Data
The runway data is contained in a CSV file named `runway.csv`.

The dataset contains the following columns.

- `user_id`: the unique identifier for the user.
- `item_id`: the unique identifier for the item/product rented.
- `rating`: the rating by the user.
- `rented_for`: the reason the item was rented.
- `review_text`: the actual text for the submitted user review.
- `category`: the category of the item rented.
- `height`: the height of the user in the format {feet}'{inches}".
- `size`: the size of the item rented by the user.
- `age`: the age of the user.
- `review_date`: the date the review was made by the user.

## Task 2: Preprocessing the `review_text`
Most unstructured text, such as reviews for products, are messy. They contain special characters which may not be necessary, extra spaces, irrelevant digits, and more. Therefore, it is common practice to process, or clean, the text before performing NLP tasks on it.

You will create several processing steps for the `review_text` strings.

Note: there may be some instances where special characters, digits, and the like are important to the meaning, or context, of the sentence. It's best to think through the implications of such preprocessing steps before blindly doing so.

Also note: some Pythonistas will say preprocessing text before using transformers, such as those from Hugging Face, is unnecessary. We will explore this in the following tasks. 

## Task 3: Sentiment Analysis on `review_text_cleaned`
Great! The review text is now clean from extraneous characters. You are ready to start performing some NLP tasks!

You will start with sentiment analysis, or the categorizing of text into two buckets - negative or positive. Some models on Hugging Face have the ability to categorize text as neutral as well. 

Sentiment analysis is a common, and useful, NLP task performed in a typical business settings. It can help decision makers determine trends in product or service perception, customer experience, reviews, and more. It can also act as a starting point for deeper analysis.

In this task, you will use the `pipeline()` function with the ["distilbert-base-uncased-finetuned-sst-2-english"](https://huggingface.co/distilbert-base-uncased-finetuned-sst-2-english) model. This is a smaller general-purpose language representation model that is great at text classification (i.e. sentiment analysis).

## Task 4: Histogram of Sentiment Score
Well, that was straightfoward, yeah?

As I'm sure you're aware by now, Hugging Face hosts a lot of models which can be employed for a variety of NLP tasks. The sentiment analysis pipeline above used the default model, but you can use any available model to suit your data (as long as they are in the [model hub](https://huggingface.co/models)). For example, [FashionClip](https://huggingface.co/patrickjohncyh/fashion-clip) is a model trained specifically for fashion-related datasets - such as this one - and tasks.

On a related note, the [`pipeline()` module](https://huggingface.co/docs/transformers/main_classes/pipelines#pipelines) is quite versatile as well! It encapsulates multiple transformer pipelines including NLP, computer vision, audio, and multi-modal. Within NLP alone, it covers 12 different tasks such as sentiment analysis (listed as "Text Classification"), Named Entity Recognition, Summarization, Conversations, and Q & A.

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/1117f846-1aaa-431c-8fea-8ad0633c1a47" />

## Task 5: Sentiment Over the Years
The distribution is informative from a global perspective - i.e., the reviews skew positive ("great customer experience"). However, it doesn't tell a complete story.

Now that you have sentiment, you can explore the trends of sentiment across different facets of the data (i.e. over time, between products, etc.). Dissecting the data in this way, based on the business questions of interest, will explain more about what is going well and what needs improvement.

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/9a6bb1a8-5adb-48be-8bdb-cc6caaa6b2a8" />

## Task 6: Does Cleaning Text Matter?
Wow - that's quite a set of positive reviews! It seems like the amount of positive reviews increased dramatically in 2021. Potentially a revamp of the customer experience, product quality, more customers, or something else we don't have data for. 

From a business context, digging into the common words/n-grams of the positive reviews can be revealing as to what customers love about the products. Doing the same for the negative reviews can be just as informative for what they don't love (i.e. sizing issues, rental service, etc.). 

We will look into that soon. But first, let's test the previous comment on preprocessing text. Does it matter for sentiment analysis?

In this task, you will build another sentiment analysis pipeline but, in this case, for the non-cleaned `review_text`. Then, you will compare the output from the two pipelines to understand if the cleaning made a difference in categorizing sentiment.

<img width="1781" height="240" alt="image" src="https://github.com/user-attachments/assets/71793b6e-6cb3-43bb-bcf1-d6a625880718" />


Based on the previous results, the sentiment of the review was pretty much the same with cleaned text. Good for us! We can use the original text to perform further analysis. Again, this is situation dependent, so be sure to think through the benefits of cleaning vs. leaving the text as is.

## Task 7: Embeddings
In the next task, we will switch gears to exploring another common use case for Hugging Face and transformers - text embeddings. 

Embeddings, in a very simplistic definition, are a vector (numerical) representation of something within n-dimensions. In this case, they are text embeddings. (Note: each transformer model will have a different number of dimensions for its results). Embeddings are useful because they represent human language to computers which enables a more sophisticated execution of similarity, text generation, semantic search, and the like. This can be extremely valuable for business tasks such as recommendations and searching within websites or products.

You will now try this out on the `rented for` column using the `sentence_transformer` [package](https://huggingface.co/sentence-transformers). The model you'll use is the BERT-based ["all-MiniLM-L6-v2" model](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) which transformer that maps sentences and paragraphs to an n-dimensional vector.

here we have (1506, 384).

## Task 8: Clustering
The all-MiniLM-L6-v2 model outputs embeddings of 384 dimensions. A higher-dimensional embedding can capture more of the relationship between words which is fantastic!

However, for some tasks, such as clustering, it can be a challenge. Clustering tends to perform poorly with higher dimensions of data (i.e. the Curse of Dimensionality), which poses a common challenge in text mining and NLP. Therefore, dimensionality reduction is often employed in order to calculate distance (e.g. Euclidean) between embeddings, then calculate clusters.

Since the transformer is constructed in such a way to be better at learning context, text - words, sentences, documents - that are similar should have similar vectors and therefore be closer together (i.e. in the same cluster).

Understanding which embeddings are closer together can then be used to determine which products, users, reviews, etc. are similar to each other. This is an important step in common method for building recommendations.

TSNE Transformation results in (1506, 2)

## Task 9: Visualizing the Clusters
Now each embedding is 2-dimensional. You don't need to be so drastic in dimensionality reduction for clustering, i.e. use explained variance ratio to determine the right number of components, but is important for visualizing the clusters.

With these smaller vectors, let's move on to generating basic clusters (the average of each category) and building a visualization for them!

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/87ed4352-d6fa-466d-903e-2d08d0459ae4" />

## Task 10: Semantic Search
The plot is showing us all of the review embeddings - based on the "rented_for" column - in a two-dimensional space (since our eyes can't handle 384 dimensions)! The color is indicating the type of item rented, i.e. "dress", "gown", "sheath".

There are clearly two main clusters in this dataset for "rented for" - the mainly blue cluster and the mainly orange one. The blue cluster consists primarily of gowns while the other is mainly dresses.

This is a simple example yet still very informative about how customers rent items for which types of occasions.

Embeddings are not only cool to visualize, as mentioned above, they also facilitate "semantic search". Semantic search denotes "searching with meaning" and with context when available. The goal is to infer what the user's intent is then find the most relevant results. This is different from "lexical search" where a search engine looks for literal matches of a query (or defined variants). Both have their strengths and weaknesses, which we encourage you to research further.

Semantic search can be incredibly powerful in a customer experience setting. Specifically, they can help with recommendations (i.e. which product is similar based on reviews, descriptions, etc.) and - obviously - search (i.e. find me products with these phrases or words in their reviews). 

output for the prompt:'a gorgeous and flattering dress'
"Item ID:  1498329 ; Rented For:  wedding ; Review:  the dress was gorgeous but unfortunately i was unable to wear it due to some quality issues which the renttherunway team was excellent at handlingi would recommend going upsizes from your usual dress size if you have a larger bustit also runs on the long side imand even withinch heels it dragged a little too much for my preferencethe colours are rich and true to the picture the fabric is forgiving when it comes to wrinkles so its a dress that travels very well
Item ID:  1879504 ; Rented For:  wedding ; Review:  this dress was greatit fit really well and was very comfortablethe only negative is that the length is a little odd so it made walking up stairs and getting into the car a little difficultimlbs and the medium fit perfectly
Item ID:  652189 ; Rented For:  wedding ; Review:  even though it was lined with satin this was a light beachy dress that was still formal enough for this casual beach weddingitsbackless though so you cant wear a bra and because the neck is such a scoopneck it makes the neckline a little strange if you have a chest and dont wear onei ended up getting one of those stick on bras and the dress looked much betterits much pinker than the model picture which was a pleasant surprisepretty dress comfortable just a little awkward fitting in the chest area if you have anything larger than an abuy the stick on bra"

## Task 11: Generate New Marketing Material
The semantic search returned three different items that appear to be similar to what we were searching for, i.e. "the dress was gorgeous" and "this dress was a great fit". With some fine-tuning, you can achieve even greater performance. We can also notice some constructive feedback on other parts of the dress. Further investigation here would reveal important insights for the business team.

Let's again switch gears for this final task. Let's generate some new text based on a prompt. Specifically, you want to create some brainstorming material for a new marketing campaign. This type of process can save a lot of time in the creation process - helping you start at "I have a good idea" vs. "I need an idea". 

using prompt = "New for this winter season, a lovely dress that", we get
"New Marketing Campaign:  New for this winter season, a lovely dress that  is going a little off the beaten path. We thought our best bet for keeping her warm was a nice red dress but we are so happy with this dress since the summer season has become so very dry"
