# Video-Keyword-Extraction

Pipeline of the project is as follows:

!(pipeline)[https://drive.google.com/file/d/1wtitXv2pdxmzLFUrl1hkdGY2LxwCIr8z/view?usp=sharing]

In the first step, audio was extracted from the video file.

In the second step, to improve the quality of speech some audio manipulation were done. First, music sources were separated from the vocal speech using spleeter package. Second, remained stationary noise was reduced using noisereduce package.

In the third step, two pretrained speech recognition models were used. One was wav2vec from Facebook and another was whisper from OpenAI. These two models are based on the transformer architecture. For wav2vec, a pretrained model for Persian was used. In the other hand, whisper was able to handle other languages other than English by itself. As the input, all raw audio, vocal extracted and noise reduced vocal audios were given to these two models. To compare the result, jellyfish package were used to compare the manually transciped text and the output texts. As it was shown in the figure above, the vocal audio and the raw audio got the best results from the wav2vec and whisper models, respectively.

In the next step, the generated texts from the speech-to-text models were given to the spell checker of the Parsivar package to improve some misspelling words. Moreover, for the next step of keyword extractoion, some Persian stop words were gathered. In this way, keyword extraction methods can ignore stop words as important keywords.

In the last step, some methods were used to extract keywords from the generated texts. The simplest method was extracting nouns and adjectives in the sentences using POS tagger of the Parsivar package. The second and third methods were using multi-rake and yake automatic keyword extraction models. The advantages of using these two packages is that they can extract most important keywords of a text regardless of the language. However, we should set proper hyperparameters of these models such as number of n-grams to get desirable keywords. At last, to have a visual representation of extracted keywords, a "word cloud** was generated from all of the extracted keywords.

It is good to mention some methods which were not successfully implemented. Maybe in the future, they can come in handy. First, the famous "spaCy" package can easily extract Named Entity words which can be considred as the subset of the keywords of a text. Unfortunately, there were no Persian packages to use that. Second, the "Perke" package which is a keyphrase extraction package for Persian could not be implemented because of the version of the installed Python. Lastly, the "vosk" which is a light-weight speech recognition package could not be used because of the correctness of the generated text.
