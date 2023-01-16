# Comment-Toxicity-Model



0.
-Motivations
i was inspired to create this model because of the kaggle competition for toxic comment classification, which had consisted of different types of hate comments classified into labels depending on their level of toxicity, the labels are ‘toxic’, ‘severe_toxic’, ‘obscene’, ‘threat’, ‘insult’ and ‘identity_hate’. since this covers a very big issue which threatens the overall helath of a lot of people all over the world. confronting this issue with adeep learning  aproach could make big impact that would benefit so many planforms and further aid buisiness in supervising their services more manageably. 
    
1.
-Data collection and Data preprocessing
i had collected the data from the kaggle competition '  '  and from then the data will have to go throug pre-processing in order for it to get it ready for modeling, and this involved a few critical steps.

The approach i took was to feed the comments into the LSTM as part of the neural network but of course i had to perform tokenization. Firstly  i had used the text vectorization layer, which comes in handy when doing nlp, because it makes tokenization a lot simpler, the steps are shown below.

inside of my dictionary so of my text vectorization layer i had specified specify how many words i wanted to store inside of that vocab, understandably the more words that you store the larger you're going to have or the bigger your model is effectively going to be because if you've got massive word embeddings, then you're going to need one word embedding for every single word, with that said i've specified it to 200 000 which may sound like a lot, however i didnt want to risk not creating an accurate model.


2. Sequential neural network
what is Sequential neural network?
..... ?


A Sequential model is appropriate for a plain stack of layers where each layer has exactly one input tensor and one output tensor, i used keras to import the seqe api since it would be the fastest asnd easist to create my model and imported a number keras layers:
lstm(with 32 lstm units, with an activation of 'tanh')
dropout 
bidirectional 
dense

the last layer will have an activation of sigmoid to transform any outputs from the last layer into a value between 0 and 1; i'm going to be taking anything that comes out of this dense layer so that the outputs are going to be somewhere between 0 and 1 which is exactly what im expecting for the labels.

sigmoid activation image (google)


3.
- Predictions
my prediction are shown below to represent my labels.
prediction labels image

4. 
 Evaluate Model
These are the metrics caluculated below are calculated, the had only trained for a single epoch but proven by the loss  still continuously decreasing so it could possibly improve by raising the number of epochs and training a little bit longer to improve the results partcularly on my accuracy in this case.

5.Gradio and testing
and you can see it is determining whether or not our model or whether or not that particular statement gets flagged or not and i had tested it would 2 opposing comments to detect its performace towrads them, and it seemed to work nicely, though i do believe the performance of this model could be imporoved on furter if a higher epoch should be imposed. 

'i freaking hate you' image 


'i love you' image
