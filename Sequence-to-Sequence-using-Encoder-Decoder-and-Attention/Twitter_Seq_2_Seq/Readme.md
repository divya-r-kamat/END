# Customer Support on Twitter dataset

The Customer Support on Twitter dataset is a large, modern corpus of tweets and replies to aid innovation in natural language understanding and conversational models, and for study of modern customer support practices and impact.

### Context
Natural language remains the densest encoding of human experience we have, and innovation in NLP has accelerated to power understanding of that data, but the datasets driving this innovation don't match the real language in use today. The Customer Support on Twitter dataset offers a large corpus of modern English (mostly) conversations between consumers and customer support agents on Twitter, and has three important advantages over other conversational text datasets:

- Focused - Consumers contact customer support to have a specific problem solved, and the manifold of problems to be discussed is relatively small, especially compared to unconstrained conversational datasets like the reddit Corpus.
- Natural - Consumers in this dataset come from a much broader segment than those in the Ubuntu Dialogue Corpus and have much more natural and recent use of typed text than the Cornell Movie Dialogs Corpus.
- Succinct - Twitter's brevity causes more natural responses from support agents (rather than scripted), and to-the-point descriptions of problems and solutions. Also, its convenient in allowing for a relatively low message limit size for recurrent nets.

### Inspiration
The size and breadth of this dataset inspires many interesting questions:

- Can we predict company responses? Given the bounded set of subjects handled by each company, the answer seems like yes!
- Do requests get stale? How quickly do the best companies respond, compared to the worst?
- Can we learn high quality dense embeddings or representations of similarity for topical clustering?
- How does tone affect the customer support conversation? Does saying sorry help?
- Can we help companies identify new problems, or ones most affecting their customers?

### Content
The dataset is a CSV, where each row is a tweet. The different columns are described below. Every conversation included has at least one request from a consumer and at least one response from a company. Which user IDs are company user IDs can be calculated using the inbound field.

- tweet_id - A unique, anonymized ID for the Tweet. Referenced by response_tweet_id and in_response_to_tweet_id.
- author_id - A unique, anonymized user ID. @s in the dataset have been replaced with their associated anonymized user ID.
- inbound - Whether the tweet is "inbound" to a company doing customer support on Twitter. This feature is useful when re-organizing data for training conversational models.
- created_at - Date and time when the tweet was sent.
- text - Tweet content. Sensitive information like phone numbers and email addresses are replaced with mask values like __email__.
- response_tweet_id - IDs of tweets that are responses to this tweet, comma-separated.
- in_response_to_tweet_id - ID of the tweet this tweet is in response to, if any.
