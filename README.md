# Comment-Toxicity-Model



0.
-Motivations
i was inspired to create this model because of the kaggle competition for toxic comment classification, which had consisted of different types of hate comments classified into labels depending on their level of toxicity, the labels are ‘toxic’, ‘severe_toxic’, ‘obscene’, ‘threat’, ‘insult’ and ‘identity_hate’. since this covers a very big issue which threatens the overall helath of a lot of people all over the world. confronting this issue with adeep learning  aproach could make big impact that would benefit so many planforms and further aid buisiness in supervising their services more manageably. 


1. brought in text vectorization 
2. created x,y variables 
3. insatntiated text vectorization and trained it
    

-Data collection and Data preprocessing
i had collected the data from the kaggle competition '  '  and from then the data will have to go throug pre-processing in order for it to get it ready for modeling, and this involved a few critical steps.

The approach i itook was to feed the comments into the LSTM as part of the neural network but of course i to perform tokenization, but first what i had done was use the text vectorization layer, which comes in handy when doing nlp because it makes tokenization a lot simpler, the steps are sghown below.


inside of my dictionary so of my text vectorization layer i had specified specify how many words i wanted to store inside of that vocab, understandably the more words that you store the larger you're going to have or the bigger your model is effectively going to be because if you've got massive word embeddings, then you're going to need one word embedding for every single word, with tha said i've specified it to 200 000 which may sound like a lot, however i didnt want to risk not creating an accurate model.


2. Sequential method?

A Sequential model is appropriate for a plain stack of layers where each layer has exactly one input tensor and one output tensor.

Schematically, the following Sequential model:

using the sequential method is the fastest and easiest then 
-we're bringing
in a bunch of layers so from tensorflow.keras.layers import:
lstm
dropout 
bidirectional 
dense
these are going to be the layers that we actually use to build up a deep neural network starting off with our lstm layers so our bi-directional layer is going to be a modifier on top of that and it's going to allow us to pass the featuresor the values from our lstm outputs across the board as we're passing through our sequences and lastly,
dropout is a method of regularization.

first up we're going to instantiate our model so model equals sequential and this is going to instantiate the sequential api we can then add in a number of layers to that particular model to be able to build it up.

-Make Predictions

and that is what we're instantiating there so model.add and then we're passing through our embedding and now
40:22
embedding is going to represent be represented as the number of words plus one i think the plus one is because of
40:28
the unknown word so the unknown words are going to have their own separate embedding i've got to double check why
40:34
we had to add plus one but when i was prototyping it i needed to add an additional one to ensure that the layer
40:39
dimensions matched so the first thing that we're going to be specifying is how many different types of embeddings that
40:44
we're going to need so this is going to correspond to one embedding per word and then our embeddings are going to be 32
40:50
values in length so imagine we're gonna have two hundred thousand and two hundred and one thousand in different
40:56
types of embeddings and they're gonna be 32 values long so that's how big our information or our embedding space is
41:02
going to be so model.ad we're passing through our embedding we're passing through how many words plus one we're going to have it in
41:08
our embedding and then how many features we're going to have in that specific embedding cool then the next thing we're doing is
41:15
we're creating our lstm layer the lstm layer is going to have 32 different lstm
41:20
units and then what we're going to do is specify that they have an activation of 10h the reason that i'm using 10h
41:27
instead of my usual favorite of relu is because the gpu acceleration that is required
41:33
for an lstm layout needs to be 10h so that that's something that's dictated by tensorflow so just keep that in mind so
41:41
we've got this lstm layer here and then we're actually specifying that we want it to be bi-directional so let's take a
41:46
look at that bi-directional so this actually allows you to pass the
41:53
information backwards and forwards across your lstm layers so um we don't have a great explanation here but
41:59
basically it's a bi-directional wrapper for recurrent neural network layers so when we're passing through our different
42:04
words typically you have the sequence outputting information in one direction bi-directional allows you to pass
42:10
information in both direction now now this is particularly useful for sentences because words prior to a
42:17
current word will still have meaning might even modify a meaning so let's say for example i don't hate you well if our
42:25
neural network is looking at it purely from left to right it might see the word hate as the last value and interpret
42:31
that as a negative statement but because don't is the previous modifier that actually has value in terms of modifying
42:38
the output meaning of that particular layer this is why implementing a bidirectional layer particularly when it
42:43
comes to nlp definitely helps you a lot attention or self-attention when it comes to transformers does help with
42:50
that a little bit so it does transform that and make it a little bit easier to work with but just know bi-directional allows you to pass
42:56
information both ways really really useful when you're doing nlp type tasks particularly on sentences so we're going
43:03
to be adding that to our model as well so this is going to implement our bi-directional
43:08
lstm layer and then we've just got a bunch of dense layers so we've got uh what is that so one two three so three
43:15
layers that think of them as your feature extractors so you've got uh one dense slayer with 128 units and an
43:21
activation of relu another dense layer would then activate or 256 units with an activation of relu and then a final
43:28
dense layer with or almost penultimate dense layer with 128 units and an activation of value so
43:35
these think of these feature extractor dense or fully connected layers
43:43
and then we have our final layer so this is our final layer and this final layer maps to the number
43:50
of different outputs that we've got inside of our neural networks remember if we take a look at our y values
43:57
we have one let's take a look at the shape probably easier we have 159 571 samples
44:05
and each one of those represents six different values in that particular vector or array right so if we go and
44:11
grab one by having six final units in our dense
44:17
layer we are going to be able to output the exact same style of output as our labels and this is effectively what you
44:23
need to be able to train our model then we're using a sigmoid activation so let's take a look at that sigmoid
44:31
activation basically it's going to transform any outputs that we get from this particular layer here into a value
44:37
between zero and one so remember our activation acts like a modifier and it allows us to take non-linearities into
44:44
account when building a deep neural network so we're going to be taking anything that comes out of this dense layer here passing it through a sigmoid
44:51
and that basically means that our outputs are going to be somewhere between 0 and 1 which is exactly what we're expecting for our labels so that
44:57
is our neural network now created so we can then go and compile it
45:03
we take a look at a summary we do so let's take a look at our compile first so i've typed in model dot compile and
45:08
i've specified our loss as being binary cross entropy now if you've ever done too much or much deep learning before
45:14
you're probably looking at this and going but nick you've got six values coming out of this shouldn't this be something like categorical cross entropy
45:21
no we're actually running this is almost as though we're running six different binary classifiers at one time because
45:28
any combination of these could be zero or one we don't necessarily have one value coming out of this it's not like a
45:35
categorical classification model we can actually have a or effectively having a multi-output model so we might have a
45:40
one here one here one here one here so on and so forth and by using binary cross entropy that is what we're
45:45
reducing our loss for to be able to effectively classify in that approach



21:53


