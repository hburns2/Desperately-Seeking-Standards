# Desperately seeking standards: using text processing to save your eyesight
By [Halle Burns](https://orcid.org/0000-0003-2346-2876) and [Susan B. Wainscott](https://orcid.org/0000-0001-9994-0956)

## Purpose/Hypothesis
We aim to analyze our standards-use and document-delivery-request data on a more regular basis to inform collections management decisions.  However, manually searching for standards titles is time consuming and unlikely to occur on a regular basis. We developed and are assessing an open source text processing tool to flag potential standards mentioned in text and tabular datasets. We believe that this method will be more efficient than manual searching and suitable for regular assessment purposes.

## Design/Method
To determine the appearances of engineering standards and other standards documents in theses and dissertations, the first step was to develop a regular expression, using Python in Jupyter Notebooks. Regular expressions (or regex), used for text processing and querying, identifies patterns within written text. This expression was created to identify any string of words that matched:

1. Starting with two or more capital letters
2. Followed by any character except specific punctuation
3. Followed by one or more numerical characters
4. Followed by zero or one instance of any character except specific punctuation
5. Followed by zero or more numerical characters

This pattern was tested to match a series of standards, within sample text that included known standards such as ANS 10.5-2006. In addition, it was checked against words and phrases it should not match against, including web addresses and mathematical equations. As a proof of concept, the code was evaluated against a collection of sample pdf theses, one of which included standards documents in the text and references list.

Once the pattern was identified, it was then applied (using Python and the pandas package) to compiled spreadsheets to identify standards in tabular collections data. These results are being compared to an earlier manual search performed on the same data.

## Results
As there are many iterations of what a standard can be called, we were unable to restrict the regex matching criteria any further. This means that false-positives appeared, such as the “state name and zip code” combination, report numbers, and chemical formulas. To help identify results from false-positives, we expanded the regular expression to also pull words surrounding the match, giving context to the results. This does not prevent the false-positives but allows us to quickly distinguish a false-positive from an actual match.


## Conclusion
Based on preliminary results, we anticipate that the regex text processing will correctly identify more standards than did the manual search method.  We do expect more false-positives, but the amount of data to manually inspect will substantially decrease from prior tests. This should result in a shorter analysis time overall.  We will also inspect regex’s utility for exploration of standards document use in publications such as theses and dissertations. This method will eventually be used to evaluate our university’s standards collection on an annual basis.
