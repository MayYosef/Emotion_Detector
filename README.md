# Emotion_Detector
 An application that receives an audio file from the user and classifies it as their emotion
<hr>

<img src="https://github.com/MayYosef/Emotion_Detector/blob/master/images/1.png" width="65%" /><br>

<h4>This project is part of our final project as part of our "Deep Learning" specialization. <br>
In this project we created an app that accessed every user, <br>
The user can insert an audio clip he is recording and the app will tell him <br>
what his emotion is based on the tone of the sentence. <br>
In fact, the model we developed and behind the app knows how to get  <br>
an audio section and categorize what the feeling of the person who said it is in it.<h4>

Emotion is an abstract thing, and we found it appropriate to classify emotion with the tone of a sentence.<br>
In addition, in this way we can classify emotion no matter what language the sentence is told.

The code shown is the code of the final application with the specific model we chose to put behind it [classified only 4 classes]<br>
in the "Architectures" folder you can find all models and experiments.

The models were written in Python,<br>
The app using FLASK technology<br>
(And HTML, CSS, Bootstrap design)
<hr>
<h3>Features:</h3>

 Each audio section has many features that can be extracted.<br>
 These are the features we came to after research,<br>
 Let us have a set of traits that successfully characterize every emotion (to increase success rates): <br>
 1. melspectrogram
 2. Spectral contrast-
 3.	Chroma 
 4.	Mel-Frequency Cepstral Coefficients (MFCC)  -
 5.	Tonnez
 <hr>

<h3>Data-Set:</h3>

  The data-set with which we trained our model,<br>
  Contains sentences and each sentence is attached to a label of what<br>
  the emotion of the person saying the sentence is.
  Possible Labels:
  1. happy
  2. sat
  3. indicates
  4. neutral
  5. fear
  6. disgust

  In our quest to classify audio clips, we realized that one set of data would not represent <br>
  the distribution of emotion through real-world sound well enough, so throughout the process,<br>
  we created one complete set of ours containing 4 different sets of .wav audio files. 

  • Surrey Audio-Visual Expressed Emotion (SAVEE) <br>
  • Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS)<br>
  • Toronto emotional speech set (TESS)<br>
  • Crowd-sourced Emotional Mutimodal Actors Dataset (CREMA-D)<br>

  Total amount of samples in our set (before augmentation): 7,464<br>
  Total amount of samples in our set (after augmentation): 14,928
  <hr>
  
  <h3>The network architectures:</h3>
  
We have done many experiments to understand what is the network architecture that brings us to the highest performance.<br>
All models can be found in the "Architectures" folder,<br>
Each uses different tools.<br>

<h4>1. VGG & transfer learning-</h4>

<h4>2. LSTM (Long Shory-Term Memory)- </h4> 

LSTM (Long Short Term Memory) is a special type of RNN network,<br> 
which addresses issues that need prior memory, which affects the rest of the network.<br>
This network is suitable when you want to classify,<br>
process and make predictions based on data series (data sequences).<br>
That's why we thought this type of network might perform well for audio that is essentially sequencing.

-Before inserting the network:
 First, the Mel-Spectogram feature has been extracted from all audio files,<br>
 in which the frequencies are converted to the Mel-scale scale. 128 values were extracted for each file.

<ins>Accuracy for 4 classes: 69.21%</ins>

<h4>3. feature extraction & MLPClassifier-</h4>

This network is the simplest of all and consists of several parts:
1. Preparing the Data Set - We load the Data Set and arrange it so that we are comfortable working with it in code
2. Feature extraction - with the help of auxiliary function.<br>
 Reading audio clips using the library - soundfile,
And extracting the features from it using the library-librosa.<br>
(librosa -Python library for music and audio analysis, provides the building blocks needed to create music information retrieval systems)<br>
3. Distribution into training set and test set.
4. Training - and classification using MLPClassifier.

<ins>-Accuracy for 4 classes: 74-76%</ins> <br>
<ins>-Accuracy for 6 classes: 60-61%</ins>  

<h4>4.Hierarchical architecture-</h4>

This architecture has come to improve the previous architecture (number 3),<br>
Here we try to improve the places where the model is wrong and confuses two classifications.<br>
This is done by building a hierarchical model.

The idea:<br>
"Unify" the classes that the model is mistaken for in one class and first separate what can be classified with less error.<br>

Different architectures were built for different class sizes. <br>

<b>-For 4 departments:</b> <br>
<ins>Accuracy: 85-90%</ins> <br>

<img src="https://github.com/MayYosef/Emotion_Detector/blob/master/images/hir1.png" width="75%" /><br>


<b>-For 6 departments:</b> <br>
<ins>Accuracy: 63-65%</ins><br>
<img src="https://github.com/MayYosef/Emotion_Detector/blob/master/images/hir2.png" width="75%" /><br>

<hr>
<h3>The App:</h3>

Our app allows the user to upload a .wab file of his or her voice and get feedback on what his or her sentiment is.
When a .wab file reaches the server side, it runs the file with <br>
the classification model we built and returns a classification answer to the client side.

<b>Examples:</b><br>

<img src="https://github.com/MayYosef/Emotion_Detector/blob/master/images/2.png" width="50%" /><br>
<img src="https://github.com/MayYosef/Emotion_Detector/blob/master/images/3.png" width="50%" /><br>


 <hr>
 
 <h2 style="background-color:Tomato;">Built With:</h2>
  
  The Model:
<ul>
  <li>Google Colab notebook (with GPU)</li>
  <li>Pycharm </li>
  <li>Libraries (python) : KERAS, librosa, SoundFile, Numpy,TensorFlow, Pandas, Scikit-learn, Matplotlib  </li>
</ul>  

The App:
<ul>
  <li>FLASK technology</li>
  <li>HTML, CSS, Bootstrap</li>
</ul>  
<hr>

<h2 style="background-color:Tomato;">Authors:</h2>
<ul>
  <li>May Yosef</li>
  <li>Shunit Avni</li>
  <li>Tom Kaneti</li>
</ul>  
