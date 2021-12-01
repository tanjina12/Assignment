Assignment
==========

## Motivation:
Software libraries are used by other software systems or applications and therefore improvement in their energy efficiency would benefit a lot in developing green software. In that context, benchmarking library projects in terms of energy efficiency related metrics could be proved as helpful for the software developers and researchers. 

## 1. Library selection

There are numerous python libraries present today that offer powerful functions for data visualization, image processing, audio/video manipulation, machine learning, computer vision, natural language processing, deep learning and so on. The list of python libraries is quite extensive where each of them provides useful functionalities for performing various tasks without writing codes from scratch. But in this study, we opt for python libraries that support tasks related to natural language processing because of the crucial role that NLP plays in current AI applications. Information extraction from free text is essential for developing chatbots, speech recognition, recommendation engines and so on. Thanks to the development of useful NLP libraries, today, many organizations use NLP techniques to optimize customer support by collecting useful information. NLP improvises the efficiency of text analytics and enhances social media monitoring [Yogish1, 2019]. Some of the most common and practical examples of NLP-related applications are Google translate, Bing translate, spam email filtering, customer services, and voice assistants (e.g. Alexa, Cortana, Siri or Google Assistant) [Weiying(&),2019,].

Many NLP libraries are available for researchers and developers to perform standard NLP tasks such as segmentation, tokenization, lemmatization, POS tagging, and NER without the need to develop from scratch. In this context, Python provides developers with an extensive collection of NLP tools and libraries that enable developers to handle a diverse set of NLP-related tasks. In this assignment, we focus on two Python NLP libraries to identify a statically computable metric so as to objectively compare the energy efficiency of the two libraries.


Table 1: Summary of some popular NLP libraries
| Library | Language | Features | License |
|---------|----------|-----------|-----------|
| NLTK | Python | Tokenization, lemmatization, stemming, parsing, POS tagging | Apache 2.0 License|
| Stanford CoreNLP | Java | Tokenization, lemmatization, stemming, parsing, POS tagging | GPL v3|
| SpaCy | Python and Cython | Tokenization, lemmatization, stemming, parsing, POS tagging | MIT|
| Stanza | Python | Tokenization, lemmatization, stemming, parsing, POS tagging | Apache 2.0 License|

In order to compare the two libraries in terms of energy efficiency, it is important that they support similar functionalities, even if they have different structures. In our study, we considered two libraries as comparable when they are written using the same programming language and support similar features. For example,  NLTK (Natural Language Toolkit) is used for tasks such as tokenization, lemmatization, stemming, parsing, POS tagging, etc. This library has tools for almost all NLP tasks. Spacy is the main competitor of the NLTK. These two libraries can be used for the same tasks. 



## Tools
1. https://www.sonarqube.org/success-download-community-edition/
2. https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/
3. https://www.scanyp.com/download
