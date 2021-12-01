Assignment
==========

## Motivation:
Software libraries are used by other software systems or applications and therefore improvement in their energy efficiency would benefit a lot in developing green software. In that context, benchmarking library projects in terms of energy efficiency related metrics could be proved as helpful for the software developers and researchers. 

## 1. Library selection
There are numerous python libraries present today that offer powerful functions for data visualization, image processing, audio/video manipulation, machine learning, computer vision, natural language processing, deep learning and so on. The list of python libraries is quite extensive where each of them provides useful functionalities for performing various tasks without writing codes from scratch. But in this study, we opt for python libraries that support tasks related to natural language processing because of the crucial role that NLP plays in current AI applications. Information extraction from free text is essential for developing chatbots, speech recognition, recommendation engines and so on. Thanks to the development of useful NLP libraries, today, many organizations use NLP techniques to optimize customer support by collecting useful information. NLP improvises the efficiency of text analytics and enhances social media monitoring [1]. Some of the most common and practical examples of NLP-related applications are Google translate, Bing translate, spam email filtering, customer services, and voice assistants (e.g. Alexa, Cortana, Siri or Google Assistant) [2].

Many NLP libraries are available for researchers and developers to perform standard NLP tasks such as segmentation, tokenization, lemmatization, POS tagging, and NER without the need to develop from scratch. In this context, Python provides developers with an extensive collection of NLP tools and libraries that enable developers to handle a diverse set of NLP-related tasks. In this assignment, we focus on two Python NLP libraries to identify a statically computable metric so as to objectively compare the energy efficiency of the two libraries.

Table 1: Summary of some popular NLP libraries
| Library | Language | Features | License |
|---------|----------|-----------|-----------|
| NLTK | Python | Tokenization, lemmatization, stemming, parsing, POS tagging | Apache 2.0 License|
| Stanford CoreNLP | Java | Tokenization, lemmatization, stemming, parsing, POS tagging | GPL v3|
| SpaCy | Python and Cython | Tokenization, lemmatization, stemming, parsing, POS tagging | MIT|
| Stanza | Python | Tokenization, lemmatization, stemming, parsing, POS tagging | Apache 2.0 License|

In order to compare the two libraries in terms of energy efficiency, it is important that they support similar functionalities, even if they have different structures. In our study, we considered two libraries as comparable when they are written using the same programming language and support similar features. For example,  NLTK (Natural Language Toolkit) is used for tasks such as tokenization, lemmatization, stemming, parsing, POS tagging, etc. This library has tools for almost all NLP tasks. Spacy is the main competitor of the NLTK. These two libraries can be used for the same tasks. 

## 2. Metric selection
In this study, we aim to select a metric which is statically computale so as to compare the two selected libraries in terms of energy efficiency.  In order to compare the energy efficiency of two libraries, we decide to focus on code metrics, which are related to analysis of the source code itself. In a systematic literature review, Ergasheva et al listed down a set of metrics for measuring software code for energy efficiency. In their SLR, they analyzed existing studies on green metrics, i.e. energy consumption on mobile, embedded and cloud systems. The main focus of their SLR was to identify the metrics related to the software code metrics for energy efficiency assessment excluding direct measurement of hardware parameters [3]. Although they focused specifically on mobile, embedded and cloud based software systems during the SLR, we can get inspiration from their identified software code metrics for energy efficiency assessment, and apply them on library projects since the code metrics are basically related to the analysis of the source code.

In this assignment, we decide to consider the following software package metric as defined by Robert Cecil Martin.

**M1. Efferent Couplings (Ce):** Efferent coupling between packages (denoted by Ce) is a metric that measures  the total number of external classes coupled to classes of a package due to outgoing coupling. Classes in the package that depend on the other packages. It is an indicator of the external dependencies of a class [4].

Besides efferent couplings metric, in this assignment I also like to calculate cyclomatic complexity of the two selected Python libraries. 

**M2. Cyclomatic complexity (CC):** Cyclomatic complexity is a metric that is used to capture the complexity of a program’s conditional logic. A program with no branches is the least complex; a program with a loop is more complex; and a program with two crossed loops is more complex still. Cyclomatic complexity corresponds roughly to an intuitive idea of the number of different paths through the program—the greater the number of different paths through a program, the higher the complexity [Marsic,2012, p. 231]. Developed by Thomas J. McCabe in 1976, it quantitatively measures the number of linearly-independent paths through a program’s source code. 

## 3. Comparison of the libraries with respect to the metric values  
To collect the metric values we have used Scanyp[^1]. Scayp is a python static code analysis and code quality tool. Scanyp is a tool that simplifies managing a complex Python code base. Architects and developers can analyze code structure, specify design rules, do effective code reviews and master evolution by comparing different versions of the code.

[^1]: https://www.scanyp.com/

The software code metrics related to the energy efficiency of the two Python library projects are captured using Scanyp on a windows 10 machine. The values for the measured metrics per library can be found in Table 2 below.

Table 2: Code metric values for NLTK and Stanza library
<table>
<thead>
  <tr>
    <th rowspan="3">Python library</th>
    <th colspan="5"><br>Metric values</th>
  </tr>
  <tr>
    <th rowspan="2">Project efferent coupling (Ce)</th>
    <th colspan="4"><br>Method complexity (CC)</th>
  </tr>
  <tr>
    <th>Total methods</th>
    <th>Methods with cyclomatic complexity higher than 10</th>
    <th>Max cyclomatic complexity for Methods</th>
    <th>Average cyclomatic complexity for methods</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>NLTK</td>
    <td>232</td>
    <td>6349</td>
    <td>87</td>
    <td>38 </td>
    <td>2.04</td>
  </tr>
  <tr>
    <td>Stanza</td>
    <td>121</td>
    <td>1776</td>
    <td>42</td>
    <td>25</td>
    <td>2.24</td>
  </tr>
</tbody>
</table>

Study shows that, efferent couplings (Ce) metric strongly correlates with software energy consumption of software applications under study [6]. Efferent couplings metric shows a large negative correlation with ρ values of −0.66 in their study. From the metric values we noticed that, NLTK library has higher efferent couplings value at project level compared to Stanza library, which are 232 units and 121 units respectively. Having a lot of dependencies could mean that the particular project is simply doing too much or that we actually have misaligned project boundaries, which could lead to more energy consumption. High efferent coupling indicates that the concerned project is dependent on other types.

Cyclomatic complexity can be calculated using the control flow graphs with respect to functions, modules, methods or classes within a software program. We calculated cyclomatic complexity metric values for methods of the two python libraries. To have good testability and maintainability, McCabe recommends that no program module should exceed a cyclomatic complexity of 10 (Marsic,2012, p. 232). From Table 2, we notice that the NLTK library has a total of 6349 methods among which 87 methods have a cyclomatic complexity higher than 10. And the max and average cyclomatic complexity for these methods are 38 paths and 2.04 paths long respectively. Whereas, for the Stanza library, it has a total of 1776 methods among which 42 methods have a cyclomatic complexity higher than 10. And the max and average cyclomatic complexity for these methods are 25 paths and 2.24 paths long respectively. 

Note that, Scanyp comes with a dashboard to quickly visualize all the metrics. The dashboard is available both in the Visual Studio extension and in the report. The graph in Figure 1 displays the method complexity of the NLTK library which we generated using the Scanyp tool. Similarly, the graph in Figure 2 illustrates the method complexity of the Stanza library.

<p align="left">
  <img src="Graphs/nltk-method complexity.PNG" width="350">
</p>
Figure 1: Method complexity of NLTK library<br />
&nbsp;
&nbsp;
&nbsp;
<p align="left">
  <img src="Graphs/stanza-method complexity.PNG" width="350">
</p>
Figure 2: Method complexity of Stanza library<br />


<br/>Cyclomatic complexity metrics are an important aspect of determining the quality of software code. I find cyclomatic complexity of the methods a useful metric for energy consumption because it measures the number of pathways through a method. This metric is basically used to figure out areas of code that need certain attention for the source code’s readability, maintainability, and portability. It definitely gives an indication of code improvement in terms of avoiding deep nested loops, conditions etc.  Higher number of decision points implies that the program is more complex and the number of execution points are higher, which could potentially contribute to less energy efficient code structure. If a program has a high complexity number, then the probability of error is high with increased time for maintenance and testing. For example, NLTK library’s max method complexity value is 38, so if a method has a cyclomatic complexity of 38, it means that there are 38 independent paths through the method. This implies that at least 38 test cases are needed to test all the different paths through the code. With a higher complexity number, the program will have more control paths in the code which could lead to more unexpected results and errors that need to be taken care of by the developers. 

## References
1. Yogish D., Manjunath T.N., Hegadi R.S. (2019) Review on Natural Language Processing Trends and Techniques Using NLTK. In: Santosh K., Hegadi R. (eds) Recent Trends in Image Processing and Pattern Recognition. RTIP2R 2018. Communications in Computer and Information Science, vol 1037. Springer, Singapore. https://doi.org/10.1007/978-981-13-9187-3_53
2. Weiying K., Pham D.N., Eftekharypour Y., Pheng A.J. (2019) Benchmarking NLP Toolkits for Enterprise Application. In: Nayak A., Sharma A. (eds) PRICAI 2019: Trends in Artificial Intelligence. PRICAI 2019. Lecture Notes in Computer Science, vol 11672. Springer, Cham. https://doi.org/10.1007/978-3-030-29894-4_24
3. Ergasheva, Shokhista & Khomyakov, Ilya & Kruglov, Artem & Succi, Giancarlo. (2020). Metrics of energy consumption in software systems: a systematic literature review. IOP Conference Series: Earth and Environmental Science. 431. 012051. 10.1088/1755-1315/431/1/012051. 
4. Robert Cecil Martin (2002). Agile Software Development: Principles, Patterns and Practices. Pearson Education. ISBN 0-13-597444-5
5. Marsic., I. (2012, September). Software Engineering. Rutgers University.
6. A. A. Bangash, H. Sahar and M. O. Beg, "A Methodology for Relating Software Structure with Energy Consumption," 2017 IEEE 17th International Working Conference on Source Code Analysis and Manipulation (SCAM), 2017, pp. 111-120, doi: 10.1109/SCAM.2017.18.
