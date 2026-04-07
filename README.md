## Project Title - Insurance-Claim-Processing-Using-Pinecone-Vector-Database

## Goal - 
Answering User Queries related to Insurance Claims Document. Analyze workers’ compensation claims data and retrieve cases that match specific injury types based on query prompts. 

## Description - 
Every workplace, from buzzing construction sites to quiet offices, has its share of risks. When accidents happen—whether it’s a slip, a fall, or repetitive strain—workers’ compensation is there to help. This essential system provides support for injured employees while helping businesses manage claims efficiently. The data used in this project is synthetically generated worker compensation insurance policies obtained from kaggle, all of which have had an accident. For each record there is demographic and worker related information, as well as a text description of the accident. This dataset is designed to simulate real-world insurance claims while adhering to data privacy standards. 

## Approach - 
Setting up OpenAI and Pinecone API -> Create a Pinecone index -> Connect to the index -> Create a function to create embeddings -> Inserting embeddings into Pinecone -> Create a function to find similar claims -> Finding the claim description of the claim that is closest to the example query

## Main Functions - 
1) pc.create_index(index_name,dimension=1536,metric='cosine',spec=ServerlessSpec(cloud='aws',region='us-east-1')) - Creating an index with specifications
2) index = pc.Index(index_name) - Connecting to the index (Insert, Update, Query)
3) client.embeddings.create(input=[text], model=model).data[0].embedding - Creating an embedding for the text
4) index.upsert([(str(row['ClaimNumber']),embedding)]) - Inserting embeddings into the Pinecone vector DB
5) index.query(vector=query_embedding, top_k=top_k, include_metadata=True) - Querying the vector DB to find the most similar documents

## Tech Stack -
1) Pinecone
2) Python
3) OpenAI API
