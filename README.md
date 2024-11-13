# kapa-ml-takehome

## Background

Customers are very interested in the questions their kapa instance is answering. Reviewing these conversations helps them understand questions like:

- How are users using the product? 
- What are common things users are struggling with?
- What features are missing from the product?
- What is documented well and what is not?

Every kapa deployment comes with an analytics platform where customers can see all their production questions.

Unfortunately, customers struggle to review all their questions because of the sheer volume. Once kapa is deployed it is often answering hundreds of questions per day for a single customer. Hence, we need to give the customers some smart filtering options that help them scope down the questions they are interested in reviewing.

To help the customers filter their questions before reviewing we want to automatically categorize questions. This feature we have recently implemented in our production system and this challenge replicates it.

Here is one real deployment for [Mapbox](https://docs.mapbox.com) on their developer docs and a [brief case study](https://www.kapa.ai/customer-stories/mapbox) explaining how they use it.

![image](https://github.com/user-attachments/assets/20cca6d4-8813-410f-b568-e11d730483b7)

## What are the categories ?

From manually reviewing a large amount of real questions we have created 6 categories which most questions across all kapa deployments fall into.

- `Discovery`: User is exploring how to do something or looking something up.
- `Troubleshooting`: User is asking about an error, often this is a stacktrace.
- `Code`: The user is inputing code and asking kapa to change, debug or explain something.
- `Comparison`: User is asking kapa to contrast two things i.e. Are X and Y the same, what is the difference betwenn X and Y
- `Advice`: The user is asking kapa what to do or what the best practice is.
- `Off-topic`: Anything else, could be something unrelated, gibberish, abuse and so on.

In production we are running an asynchronous workflow that categorizes each new incoming question and saves the labels to a database. In our analytics platform users can then filter their conversations by these labels, i.e. *"Show me only the troubleshooting questions"*.

> **Note:** Look through labelled `data.json` to get a feel for the categories.

## What is the challenge? 

Your task is to create a classifier for labelling questions.

The classifer should take as input a `question` and optionally an `answer` if you find that this helps.

The classifier should output ONE of the six labels described above.

You have access to a labelled dataset of +1000 questions and answers which you can use to create and test your classifier. You can assume that this dataset is representative of the questions in production and that all questions are in English.

> **Note:** This challenge is only about creating a classifier and NOT about writing any code for assigning and storing the labels.

## What do I need to submit?

We are hiring for a research position that involves a lot of open ended experimentation in a not-yet fully established field. Hence, the requirements for this challenge are intentionally vague.

You can solve this problem in any way you like. We just require you to submit 3 things:

1. The `performance results` of the classifier you have created. How you want to test and measure the accuracy of your classifier is up to you.
2. A documentation of your `thought process`. You will probably think about different solutions to this problem, test a few things and make some assumptions. So please just take some notes on this process in any way you like and include it in your submission.
3. The `code you have written` for your classifier.

## How do I submit my solution?

When you are done with your work. Create a private repo, raise a PR in it and invite finn@kapa.ai to it so we can take a look.

If you submit a solution to us you get a USD 300 Amazon gift card as an appreciation of the time you have invested.

## How can I use technologies that cost money?

We don't require you to solve this problem purely with tech you can use for free or run on your laptop. **You can use whatever you want**. Just send finn@kapa.ai and email if you need access to any commercial products and we will cover it (within reason), so you don't have to cover the cost yourself. We can create you accounts, make you an API key, etc.

## What if I have some clarifying questions?

Please email finn@kapa.ai with any questions you have. If something is unclear we do not want that to stop you from completing the challenge.

## How can I get bonus points?

A great solution is theoretically extensible to let users define their own labels. This is not something we have currently implemented ourselves. However, users keep asking us: 

*"Your categories are great but we would like to define our own and have them automatically assigned to our questions"*

When thinking about this these guideing questions might help:
- What input would you require from users to make this work for them?
- Is it possible to give this feature to users as self service without any intervention/configuration/training from the kapa engineering team?
- Is it possible to deliver this feature to customers without creating their own classifier for them?

> **Note:** This is not required to pass this take home but it gets bonus points.
