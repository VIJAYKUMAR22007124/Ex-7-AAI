<H3>B VIJAY KUMAR</H3>
<H3>212222230173</H3>
<H3>EX. NO.7</H3>
<H3>DATE: 27-04-2024</H3>
<H1 ALIGN =CENTER>Implementation of Text  Summarization</H1>
<H3>Aim: 
 To perform automatic text summarization using Natural Language Processing (NLP) techniques. </H3> 
 <BR>
<h3>Algorithm:</h3>
Step 1 Import necessary libraries for natural language processing tasks.<BR>
Step 2: Download NLTK resources, including the punkt tokenizer and stopwords.<BR>
Step 3: Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.<BR>
Step 4: Define the Text Summarization Function using a simple frequency-based approach.<br>
    - Calculate the frequency of each word in the preprocessed text.<br>
    - Calculate a score for each sentence based on the sum of word frequencies.<br>
    - Select the top N sentences with the highest scores to form the summary.<br>
Step 5: Construct the main program to read the paragraph  and perform text summarization<br>
      - Generate and print the original text.<br>
      - Generate and print the text summary using the  Text Summarization function<br>
<H3>Program:</H3>

#### Importing Libraries and Downloads

```
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize, sent_tokenize
from nltk.stem import PorterStemmer

nltk.download('punkt')
nltk.download('stopwords')

```

#### Preprocessing Functions

```

def pp_text(text):
    words = word_tokenize(text)
    stop_words = set(stopwords.words('english'))
    filtered_words = [word for word in words if word.lower() not in stop_words and word.isalnum()]
    stemmer = PorterStemmer()
    stemmed_words = [stemmer.stem(word) for word in filtered_words]
    return stemmed_words

```

#### Summary Generation Function

```
def generate_summary(text, num_sentences=3):
    sentences = sent_tokenize(text)
    preprocessed_text = pp_text(text)
    word_frequencies = nltk.FreqDist(preprocessed_text)
    sentence_scores = {}
    for sentence in sentences:
        for word, freq in word_frequencies.items():
            if word in sentence.lower():
                if sentence not in sentence_scores:
                    sentence_scores[sentence] = freq
                else:
                    sentence_scores[sentence] += freq
    summary_sentences = sorted(sentence_scores, key=sentence_scores.get, reverse=True)[:num_sentences]
    return ' '.join(summary_sentences)

```

#### Main Function

```
if __name__ == "__main__":
    input_text = """
    Natural language processing (NLP) is the ability of 
    a computer program to understand human language as it's 
    spoken and written -- referred to as natural language. 
    It's a component of artificial intelligence (AI).

    NLP has existed for more than 50 years and has roots in 
    the field of linguistics. It has a variety of real-world 
    applications in numerous fields, including medical research, 
    search engines and business intelligence.
    """
    summary = generate_summary(input_text)
    print("Original Text:")
    print(input_text)
    print("Summary:")
    print(summary)

```

<H3>Output</H3>

![image](https://github.com/VIJAYKUMAR22007124/Ex-7-AAI/assets/119657657/fb82fd8c-356e-41b2-9d1a-a8b028d24100)


<H3>Result:</H3>
Thus ,the program to perform the Text summarization is executed sucessfully.


