# Personal AI Assistant using RAG and ChromaDB

When I was in school, tired of studying endless hours, I would sometimes pick up the hefty book and, in a moment of whimsical fantasy, flip through its pages rapidly. As the pages blurred before my eyes, I imagined a world where all this information could be instantly transferred to my brain. I wouldn’t have to memorize each detail laboriously. Instead, I could effortlessly access any fact or concept, ready to answer any question effortlessly.

What if I told you that a version of this fantasy is becoming a reality?

Enter the world of Retrieval-Augmented Generation, or RAG.

## What is RAG?

Retrieval-augmented generation (RAG) is an innovative approach in the field of artificial intelligence that brings us closer to the idea of instant knowledge access. While it doesn’t download entire textbooks into your brain, it combines two powerful AI techniques to deliver information swiftly and accurately.

## How Does RAG Work?

RAG operates through a seamless integration of two components:

Retrieval: Imagine having an assistant that can instantly scan a vast library of books, articles, and documents. When a question is posed, this assistant retrieves the most relevant information from this extensive corpus.

Generation: Once the relevant information is retrieved, it is then sent to the generative model to formulate a coherent and contextually accurate response. This is like having an expert who not only finds the right page in the textbook but also reads, understands, and explains the content in a way that directly answers your question.

In essence, RAG allows us to do what I had once dreamed of as a student: access vast amounts of information quickly and use it to provide accurate answers on demand.

## Let’s get this working

Recently I have been preparing for Azure AZ-900 certification. I thought of applying this concept to the documentation I prepared for this exam.

I will be using Python to demonstrate this. The below are the 6 steps in which we could achieve this.

```c
// Retrieval
1. Load my Azure Notes which is in Markdown format.
2. Split the data into paragraphs.
3. Save the split chunks in the form of "embeddings" in to Chroma DB

// Generation
1. Ask a question like "what is iaas, paas and saas?"
2. Get the possible responses from chroma db.
3. Feed in these responses to OpenAI to get the best response.
```

```c
"ChromaDB" is like a super-smart library that can remember and quickly
find information. Instead of books, it stores "embeddings," which are like
summaries or important points of data. It helps find similar information
very quickly, which is great for tasks like finding recommendations or
answering questions. It can manage and search through a huge amount of data
efficiently
```

```c
"Embeddings" are just like a map helps you see how close one place is to
another, embeddings help a computer see how similar one word or piece of data
is to another. Basically this helps understand relations with each other.

For example, in an embedding, the words "king" and "queen" would be close
together because they have similar meanings.

Computers can process numbers quickly and easily.
By turning words into numbers, it makes it faster and easier for computers
to work with text.

Simple Example:
Imagine you have three words: "apple," "banana," and "cat."
You want the computer to understand that "apple" and "banana" are more
similar to each other than to "cat."

You could turn them into embeddings like this:

Apple: [1, 0, 0]
Banana: [1, 0.1, 0]
Cat: [0, 0, 1]
In this list of numbers (vector):

The first number could represent "is it a fruit?"
The second number could represent "how sweet is it?"
The third number could represent "is it an animal?"
So, "apple" and "banana" have similar numbers because they are both fruits,
while "cat" is very different because it’s an animal.

How Embeddings are Used?

Search Engines:
To find information similar to what you’re looking for.

Recommendations:
To suggest things like movies or products that are similar to what you like.

Language Translation:
To understand and translate languages by comparing meanings of words.

Finding Similarity Between Words ?

To determine if these words are similar or different, we can calculate the
distance between their vectors. One common method is the "cosine similarity",
which measures the cosine of the angle between two vectors. A cosine similarity closer to 1 indicates that the vectors are similar (close),
while a value closer to 0 indicates that they are different (far apart).

Go to this url to learn about cosine similarity:
https://www.datastax.com/guides/what-is-cosine-similarity
```

[Code in git](https://github.com/jpothanc/my-ai-assistant?source=post_page-----6fd5c259da41--------------------------------)

```c
//load, split save my azure notes.
python retrieve_data.py

//query, get response and optimize it.
python query_data.py
```

```c
Enter your question:what is iaas, paas and saas in detail?

Response: IaaS (Infrastructure as a Service) provides cloud resources such
as servers, storage, and networking as a service, giving consumers high contr
ol over their cloud infrastructure.Consumers are responsible for managing applications, data, runtime,
middleware, and OS in the IaaS model.

PaaS (Platform as a Service) allows consumers to manage applications and data,
with the cloud provider handling the underlying infrastructure. This
model simplifies the development and deployment of applications by providing a platform for developers to build upon.

SaaS (Software as a Service) is a cloud model where most responsibilities are
handled by the cloud provider. Consumers access software applications over
the internet without needing to manage the underlying infrastructure, making it a convenient option for users.
```
