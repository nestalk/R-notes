Natural Language Processing
===========================

Analysing text.

When reading in the data don't convert the strings to factors,
add argument `stringsAsFactors=FALSE` to `read.csv`

Bag of Words
------------

Counts the times each word is used in the text. Best to preprocess the text,
check for casing and punctuation, tailor to what you are processing.
Remove stop words, e.g. the, is, at, etc.... be careful for double stop words.

**Stemming** Match words that mean the same thing by removing the end of the word,
pluralised words and alternate spellings. `Porter Stemmer` is a common process.

Convert the text to a dataframe using the `tm` package to create a variable for
each word, then use a regression tree to do predictions. 