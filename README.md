# ML_stock




**List of Features**

0. Year of transcript release
1. Quarter of transcript release
2. Date of transcript release
3. Earnings Transcript contents


**Independent Variables (inputs of the machine learning model)**

5. EPS surprise value

The "EPS surprise value" indicates how much the EPS number released by a company exceeds or falls short of the predicted value by a financial analyst. This information can be used to determine whether the company has exceeded or missed the forecast.
**Features extracted from Pre-release/Safe Harbour materials**
5. Whole pre-release’s net sentiment index
6. Whole pre-release’s positive sentiment index 
7. Whole pre-release’s negative sentiment index
8. Whole pre-release’s average text complexity index

Numbers 5 to 8 only analyses the contents in pre-releases. The hypothesis is that if there is a huge difference between the pre-release and Q&A section, it may be a signal of deteriorating future business performances, thus potentially affecting the stock price. 

The “net sentiment index” measures the average sentiment of all pre-release sentences. To derive the positive sentiment index, the number of positive-sentiment sentences is divided by the total number of sentences. A similar approach is used for the negative sentiment index but with negative sentences.

“Average text complexity index” refers to the average text complexity for the pre-release materials (i.e. flesch reading ease index). The hypothesis here is that higher text complexity may indicate a lack of clarity, hesitation, or uncertainty in their communication, potentially leading to a negative impact on the stock price due to uncertain future business performance.

9. Specific forward-looking statement’s net sentiment index
10. Specific forward-looking statement’s positive sentiment index
11. Specific forward-looking statement’s negative sentiment index
12. Specific forward-looking statements average text complexity index

13. Non-Specific Forward-looking statement’s net sentiment index
14. Non-Specific Forward-looking statement’s positive sentiment index
15. Non-Specific Forward-looking statement’s negative sentiment index
16. Non-Specific Forward-looking statement’s average text complexity index

17. Not Foward-looking statement’s net sentiment index
18. Not Foward-looking statement’s positive sentiment index
19. Not Foward-looking statement’s negative sentiment index
20. Not Foward looking statement’s average text complexity index

21: Specific forward-looking statement index (calculated as the number of sentences classed as specific forward-looking, over the total number of sentences)
22: Non-Specific forward-looking statement index (calculated as the number of sentences classed as non-specific forward-looking, over the total number of sentences)

Specific forward-looking statements refer to statements that involve a precise estimation of future events (e.g. expected revenue). 

Non-specific forward-looking statements, on the other hand, are more general in nature and do not involve specific figures or estimates. They may include statements regarding future plans or strategies, but without committing to a precise outcome. 

Not forward-looking statements are statements that do not estimate future events or projections, but instead, they describe the current state of affairs or historical data. 

Numbers 9 to 22 essentially tries to find any relationship between sentiment and semantical differences between these three forward-looking classifications and tests whether they have an effect of future stock performances.


**Features extracted from the Questions & Answers:**
“Questions” are those from analysts
“Answers” are replies from the management

23. Whole Q&A’s net sentiment index
24. Whole Q&A’s positive sentiment index
25. Whole Q&A’s negative sentiment index
26. Whole Q&A’s average text complexity index

27. All Question’s net sentiment index
28. All Question’s positive sentiment index
29. All Question’s negative sentiment index
30. All Question’s average text complexity index


**Combining all management replies:**
31. All Reply’s net sentiment index
32. All Reply’s positive sentiment index
33. All Reply’s negative sentiment index
34. All Reply’s average text complexity index

35. Specific forward-looking statement’s net sentiment index
36. Specific forward-looking statement’s positive sentiment index
37. Specific forward-looking statement’s negative sentiment index

38. Non-Specific Forward-looking statement’s net sentiment index
39. Non-Specific Forward-looking statement’s positive sentiment index
40. Non-Specific Forward-looking statement’s negative sentiment index

41. Not Forward-looking statement’s net sentiment index
42. Not Forward-looking statement’s positive sentiment index
43. Not Forward-looking statement’s negative sentiment index

In the Q&A section, analysts asks questions, and management replies (an answer). Hence, we can compare the difference between the two parties and their general sentiment and semantical state, potentially giving a hint of future business performances.


**Analysing specific words:**
These features only look at sentences that contain the required word.

44: "margin" - average sentiment (i.e. what’s the average sentiment for sentences that mentioned the word “margin”)
45: "margin" - positive sentiment index
46: "margin" - negative sentiment index
47: "cost" - average sentiment
48: "cost" - positive sentiment index
49: "cost" - negative sentiment index
50: "revenue" - average sentiment
51: "revenue" - positive sentiment index
52: "revenue" - negative sentiment index
53: "earnings/EBIDTA" - average sentiment
54: "earnings/EBIDTA" - positive sentiment index
55: "earnings/EBIDTA" - negative sentiment index
56: "growth" - average sentiment
57: "growth" - positive sentiment index
58: "growth" - negative sentiment index
59: "leverage/debt" -  average sentiment
60: "leverage/debt" -  positive sentiment index
61: "leverage/debt" -  negative sentiment index
62: "industry/sector" – average sentiment
63: "industry/sector" – positive sentiment index
64: "industry/sector" – negative sentiment index
65: "operation" - average sentiment
66: "operation" - positive sentiment index
67: "operation" - negative sentiment index
68: "cashflow" - average sentiment
69: "cashflow" - positive sentiment index
70: "cashflow" - negative sentiment index
71: "dividend/share buyback" - average sentiment
72: "dividend/share buyback" - positive sentiment index
73: "dividend/share buyback" - negative sentiment index

For numbers 44 to 73, it finds all sentences where a particular word appears, it then checks the sentiment value for this sentence. For example, if the sentences associated with the word “earnings” is positive, this may imply they are achieving higher earnings in the future, hence potentially bullish for the stock price.


**Finding text similarity between transcripts**
74: Text similarity between the current and the 2nd most recent earnings transcript
75: Text similarity between the current and the 3rd most recent earnings transcript
76: Text similarity between the current and the 4th most recent earnings transcript

77: Text similarity between the current and the 2nd most recent earnings transcript (only looking at the pre-release materials)
78: Text similarity between the current and the 3rd most recent earnings transcript (only looking at the pre-release materials)
79: Text similarity between the current and the 4th most recent earnings transcript (only looking at the pre-release materials)

80: Text similarity between the current and the 2nd most recent earnings transcript (only looking at the management replies)
81: Text similarity between the current and the 3rd most recent earnings transcript (only looking at the management replies)
82: Text similarity between the current and the 4th most recent earnings transcript (only looking at the management replies)

83: Text similarity between the current and the 2nd most recent earnings transcript (only looking at the analyst questions)
84: Text similarity between the current and the 3rd most recent earnings transcript (only looking at the analyst questions)
85: Text similarity between the current and the 4th most recent earnings transcript (only looking at the analyst questions)

The hypothesis here is that text dissimilarity may imply operational changes in the business. For example, if there is a sudden drop in the frequency of the term 'iPad' and a corresponding increase in mentions of 'Macbooks' by Apple during the second quarter of 2022, it is reasonable to infer that they may have reoriented their attention towards Macbooks, which may have an impact on the stock price.


**Dependent Variable (output of the machine learning model):**
The dependent variable is what I want to predict (i.e. stock returns after the earnings call). Day 0 represents the day the earnings call is broadcasted. The reason I have multiple dependent variables is to see which time series is more accurate.

86: Stock price difference between Day 0 and Day 10
87: Stock price difference between Day 0 and Day 30
88: Stock price difference between Day 0 and Day 50
89: Stock price difference between Day 0 and Day 70
90: Stock price difference between Day 0 and Day 90
91: Stock price difference between Day 1 and Day 10
92: Stock price difference between Day 1 and Day 30
93: Stock price difference between Day 1 and Day 50
94: Stock price difference between Day 1 and Day 70
95: Stock price difference between Day 1 and Day 90


**Market Cap:**
I included market cap so I can use it as a filter, for example, create a model that only looks at small-cap stocks, or one that only looks at large-cap etc.

96: Market Cap