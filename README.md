# Comment-Toxicity-Model



0.
-Motivations
i was inspired to create this model because of the kaggle competition for toxic comment classification, which had consisted of different types of hate comments classified into labels depending on their level of toxicity, the labels are ‘toxic’, ‘severe_toxic’, ‘obscene’, ‘threat’, ‘insult’ and ‘identity_hate’. since this covers a very big issue which threatens the overall helath of a lot of people all over the world. confronting this issue with adeep learning  aproach could make big impact that would benefit so many planforms and further aid buisiness in supervising their services more manageably. 


1. brought in text vectorization 
2. created x,y variables 
3. insatntiated text vectorization and trained it
    

-Data collection and Data preprocessing
i had collected the data from the kaggle competition '  '  and from then the data will have to go throug pre-processing in order for it to get it ready for modeling, and this involved a few critical steps.

The approach we are taking is to feed the comments into the LSTM as part of the neural network but we can’t just feed the words as it is, so we performed tokenization and did index representation. As keras made our lives easier, this can be done in below simple steps.



to get this done. and i begun by tokenizing the data, and used  first thing i had done was use the text vectorization layer, which comes in handy when doing nlp because it makes tokenization a lot simpler, before i finished by splitting the data into comments and features.

inside of my dictionary so of my text vectorization layer i had specified specify how many words i wanted to store inside of that vocab, understandably the more words that you store the larger you're going to have or the bigger your model is effectively going to be because if you've got massive word embeddings, then you're going to need one word embedding for every single word, with tha said i've specified it to 200 000 which may sound like a lot, however i didnt want to risk not creating an accurate model.


2.  Sequential Model

21:53


