# Artificial Music Generation

<p>
<img src="https://github.com/adityachandupatla/artificial_music_generation/blob/master/images/jazz_music.png" align="right"/> 
In this project an RNN with <a href="https://en.wikipedia.org/wiki/Long_short-term_memory">LSTM</a> units is used to generate artificial Jazz music. We will train a network to generate novel jazz solos in a style representative of a body of performed work. The dataset is taken from <a href="https://github.com/adityachandupatla/artificial_music_generation/blob/master/data/original_metheny.mid">data/original_metheny.mid</a>. This dataset is not a raw dataset of mp3 files, but it is a pre-processed one. The musical data is rendered in terms of "values". We can informally think of each "value" as a note, which comprises of a pitch and a duration. Basically, we will obtain a dataset of values, and will learn an RNN model to generate sequences of values. Our music generation system will use 78 unique values. This project is implemented as part of the <a href="https://github.com/adityachandupatla/deeplearning_coursera">deeplearning specialization</a> from Coursera.
</p><br/>

<h2>Running the Project</h2>
<ul>
  <li>Make sure you have Python3 installed</li>
  <li>Clone the project to your local machine and open it in one of your favorite IDE's which supports Python code</li>
  <li>Make sure you have the following dependencies installed:
    <ol>
      <li><a href="http://www.numpy.org/">Numpy</a></li>
      <li><a href="http://web.mit.edu/music21/">Music21</a></li>
      <li><a href="https://keras.io/">Keras</a></li>
    </ol>
  </li>
  <li>Run music_generate.py</li>
</ul>
If you find any problem deploying the project in your machine, please do let me know.

<h2>Technical Skills</h2>
This project is developed to showcase my following programming abilities:
<ul>
  <li>Python</li>
  <li>Developing sequence models using <a href="https://en.wikipedia.org/wiki/Recurrent_neural_network">RNN (Recurrent Neural Network)</a></li>
  <li>Use of high level deeplearning programming frameworks such as Keras</li>
</ul>

<h2>Development</h2>
<ul>
  <li>Sublimt Text has been used to program the application. No IDE has been used.</li>
  <li>Command line has been used to interact with the application.</li>
  <li>The project has been tested on Python3 version: 3.6.1.</li>
</ul>

<h2>Working</h2>
<p><b>Dataset characteristics</b>:
  <ul>
    <li>X: This is an (m,  Tx , 78) dimensional array. We have m training examples, each of which is a snippet of  Tx=30  musical values. At each time step, the input is one of 78 different possible values, represented as a one-hot vector.</li>
    <li>Y: This is essentially the same as X, but shifted one step to the left (to the past). The data in Y is reordered to be dimension  (Ty,m,78) , where  Ty=Tx . This format makes it more convenient to feed to the LSTM later.</li>
    <li>n_values: The number of unique values in this dataset. This should be 78.</li>
    <li>indices_values: python dictionary mapping from 0-77 to musical values.</li>
  </ul>
</p>
<p>You can listen to <a href="https://github.com/adityachandupatla/artificial_music_generation/blob/master/data/30s_seq.mp3">this</a> sample audio from the dataset</p><br/>

<p><b>Architecture</b>: We will be training the model on random snippets of 30 values taken from a much longer piece of music on an LSTM with 64 dimensional hidden states. <a href="https://keras.io/optimizers/">Adam optimizer</a> is used with <a href="https://keras.io/losses/">categorical_crossentropy loss function</a>.
<img src="https://github.com/adityachandupatla/artificial_music_generation/blob/master/images/music_generation.png" />
</p><br/>

<p><b>Generating music</b>: At each step of sampling, we will take as input the activation 'a' and cell state 'c' from the previous state of the LSTM, forward propagate by one step, and get a new output activation as well as cell state. The new activation 'a' can then be used to generate the output.</p>
<img src="https://github.com/adityachandupatla/artificial_music_generation/blob/master/images/music_gen.png" /><br/>
The music, with .midi extension, will be generated in the output folder. Convert this .midi file into an mp3 file, from one of the many online converters available. Then, you can listen to the artificially generated jazz music!
<br/>

Use this, report bugs, raise issues and Have fun. Do whatever you want! I would love to hear your feedback :)
~ Happy Coding
