# Project 3 Generative Audio

Kasidech Tantipanichaphan, ktantipa@ucsd.edu

(Your teammate's contact info, if appropriate)

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/Cover_Album.png" width="60%">

## Abstract

In the history of music, there were many great composers in the past who were unable to finish their musical pieces. Some of them have suffered from their health or mental condition,  which makes them pass away before they even finish their pieces. In this project, I wanted to help finishing their composition by using an artificial intelligence programme, which in this case is the machine learning components that we've learned in this class. The main goal of this project is to complete a fragment of their piano composition, as well as making a better piece by manipulating the sound, by using Wave2mid, GANSynth, Music Transformer/RNN performance, and Garageband Software tools/method. So that, the fans of those artists have a chance to hear a new piece by these great composers in the past. The inspiration behind this project is that some of the pianists have died before they are able to finish composing their great pieces.  For example, Puccini, one of the great composers that I’ve selected, suffered from cancer in 1924 and he’d never been the same. Subsequently, he’s undertaking the surgery that ultimately causes his death. As a result, his operatic masterpiece called Turandot was left unfinished. 

Some of the music of course has only the melody which is called Monophonic music. Since it’s missing the accompaniment, which is not a perfectly completed piece, I decided to include these songs into the album as well. For example, Butterfield was another great composer which also produced monophonic music.

For the technical implementations, there are multiple methods that I want to use in order to construct perfect pieces for the album: Wave2mid, GANSynth, Music Transformer/RNN performance, and Garageband Software instrument. The way I approach this is that first, I have to assemble the original pieces using the Wave2mid, in the form of magenta. Because some of the music has only the .wav file. For the implementation of the improvisation of the project, I generate the continuation for the musical pieces to make it finish. And for the monophonic music, I generate the accompaniment of those pieces. The model that I chose to use is called the Music Transformer model, which represented using the event vocabulary from Performance RNN according to the creator of this model. For the last two pieces in the album, there are a couple of pieces that I wanted to make as a choral symphony version. In order to make it as the choral symphony version, I turn the piano frequency into a string ensemble/vocal sound by using GANSynth. Finally, I decided to use Garageband to assemble everything together. In order to make better pieces, I modify the the crescendo, ascendo, as well as sustain. 

The result of the experiments are explained in the below sections. Although, this has been an amazing experience for me, however, in the future I would like to add more songs as well as different instruments for the musical pieces. 

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/Tracklists.png" width="60%">

## Model/Data

In this part of the project, I use the Wave2mid method in order to extract the wave to a magenta form, which in this case is the midi. This is because most of the music doesn’t have the .midi file that I needed. Therefore, I decided to use this method. 

As an example, first I just load the .wav files

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/wave.png" width="40%">

Then, below are the extracted results as midi:

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/mid.png" width="70%">

The generated results and plots for this part can be found through this link below, titled ‘Wave2mid_ECE_188_Project_2’.  It extracted the .wav into midi files.

https://colab.research.google.com/drive/1OsN9bfXUESwQC_RtxLgVZKyHaJ3Mdmda 

And the extracted wave can be viewed in the input folder in each of the songs folder in the github. 

## Code
The code files are in this github. 

Names:

Choral_Orchestral_ECE188_project_2.ipynb

Improvisation_ECE188_project_2.ipynb

Wave2mid_ECE_188_Project_2.ipynb

The code should be run on the collab links that I created.

## Results

The songs can be listen through this link below:

https://drive.google.com/drive/folders/1ZPsPLbjvHPpT6jb00W1dNiBY_UX4GUR8?usp=sharing

Basically, almost everything works according to my expectations. Based on the generated samples, I believe that the originality of the key for those music is kept. Some of the tempo is a little bit off, but most of it stays the same. However, I believe that it’s because of the style effect to make the music sound better. Another thing is that I found that if the pieces have more chords, seems to generate better. There is a bit of change in classical music. The generated piece seems to have a bit of a modern classical vibe, when the original piece is the original classical music. All the results of the plots can be viewed in the .ipynb file on github or the collab links that I shared in the github. The tracks also can be listened to on the github.


## Technical Notes


After performing Wave2mid method. Now, it is time to complete the unfinished music, as well as manipulate the sound.
The following ran on google collabs. The links are provided below:

Gansyth Portion: 
https://colab.research.google.com/drive/1mMBZjV1KNRwy3s12Utqt63kCS7NwNLES

Accompaniment and continuation generation portion:
https://colab.research.google.com/drive/1MT0u1SwV3JNd8S-AOCqMiKatYlgZzURI 



*Continuation and Accompaniment* 

In this part, I use the Music Transformer model. According to the creator of this model, it was introduced by Huang et al, which used to trained on over 10,000 hours of piano recordings from Youtube transcribed using Onsets and Frames and represented using the event vocabulary from Performance RNN. 
First, I just run the environmental setup as well as the piano performance language model. Then, I selected a portion of the songs in order to build off and make the improvisation. Usually the max primer seconds is around 7-10 generated the best results for my case. The code can be examined through the github. Basically, the code just takes out all the irrelevant sounds except for the piano magenta.
	Here is one example of the generated result for Turadot:

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/Turandot_1.png" width="45%">

As mentioned in the abstract, there is music that also contains monophonic music. In this part, I basically generate the accompaniment of the piece that has only the melody. As the music of my pick. I chose TAPS (Butterfield’s Lullaby) as the music to generate. This part is generated first, before generating the continuation to build off the accompaniment part.

Let’s quickly examine the original input in the magenta form (by using mm.plot_sequence):

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/Butterfield_1.png" width="50%">

As we can see, this is the whole piece for Butterfield's Lullaby. It seems very simple and has no complexity. Subsequently, play with the parameters and use the Melody-conditioned transformer model to generate the accompaniment. And this is the result after it is generated:

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/Butterfield_2.png" width="50%">

Finally, repeat the process of continuation or the improvisation.

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/Butterfield_4.png" width="50%">

As we can see, the piece looks more completed this time.

*Gansyth*

To get in touch with the GANSynth techniques, I decided to pick Toradot and Dies Irae Requiem to produce the Choral Symphony version. I realized that GANSynth would produce this part of music that I needed.

There are 4 samples/instruments that I choose to generate for the interpolation. The first sounded like vocal, the second one sounded like trumpet, the third one sounded like string, and the last one sounded like a woodwind instrument. This can be found in the sample sound files. After that I have to set a list of instruments to interpolate. As an example, the list of instruments to interpolate is between [1, 2, 1, 2] for the Requiem, and the relative time is [0, 0.3, 0.6, 1.0].  These instruments can be listen through the Github files that I shared.

Below is the CQT Spectrogram result that I got for the Requiem.

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/Spectrogram_Requiem.png" width="80%">

And another is the CQT Spectrogram result for the Tudorat.

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/Spectrogram_Requiem.png" width="80%">

*GarageBand*

The garageband is basically the last step where I gather everything together, and also to produce the music that has more detail such as creating crescendo, ascendo, or sustain.  This includes the original input as well as the Generated output using the Music transformer.  Little of the part that I decided to adjust the tempo in order to make it sound not awkward. But most of the part seems to conform to what is needed.

<img src="https://github.com/ucsd-ml-arts/generative-audio-kasidech-tantipanichaphan/blob/master/Images/Garageband.png" width="50%">

## Reference

Generating Piano Music with Transformer - Ian Simon, Anna Huang, Jesse Engel, Curtis "Fjord" Hawthorne

GANSynth Demo - gansynth_external.ipynb

Onsets and Frames: Dual-Objective Piano Transcription - Curtis Hawthorne, Erich Elsen, Jialin Song, Adam Roberts, Ian Simon, Colin Raffel, Jesse Engel, Sageev Oore, Douglas Eck
 
