<div align="center">
  <h1>korcen</h1>
</div>

![131_20220604170616](https://user-images.githubusercontent.com/85154556/171998341-9a7439c8-122f-4a9f-beb6-0e0b3aad05ed.png)

<div align="center">
  <h2>
    <a href="https://github.com/KR-korcen/korcen-ml/blob/main/README/KR.md">한국어</a>
  </h2>
</div>


Korcen, which showed the best performance among keyword-based censorship, has come to stronger censorship through deep learning.

We learned using `2 million sentences collected by ourselves` and `after classifying datasets through deep learning`.

The open source is **demo version**, so please contact us to use the latest model and data file

Keyword-based existing libraries : [py version](https://github.com/KR-korcen/korcen),[ts version](https://github.com/KR-korcen/korcen.ts)

[Support Discord Server](https://discord.gg/wyTU3ZQBPE)


## Example Code
>Python 3.10
```py
import tensorflow as tf
import numpy as np
import pickle
from tensorflow.keras.preprocessing.sequence import pad_sequences

maxlen = 200

model_path = 'vdcnn_model.h5'

tokenizer_path = "tokenizer.pickle"

model = tf.keras.models.load_model(model_path)
with open(tokenizer_path, "rb") as f:
    tokenizer = pickle.load(f)

def preprocess_text(text):
    text = text.lower()
    
    return text

def predict_text(text):
    sentence = preprocess_text(text)
    sentence_seq = pad_sequences(tokenizer.texts_to_sequences([sentence]), maxlen=maxlen)
    prediction = model.predict(sentence_seq)[0][0]
    print(prediction)
    return prediction
    
while True:
    text = input("Enter the sentence you want to test: ")
    result = predict_text(text)
    if result >= 0.5:
        print("This sentence contains abusive language.")
    else:
        print("It's a normal sentence.")
```


## Maker


>Tanat
```
github:   Tanat05
discord:  Tanat05
email:    tanat@tanat.kr
```

## Reference

### Github
- [KcBERT](https://github.com/Beomi/KcBERT/)
- [Toxic_comment_data](https://github.com/songys/Toxic_comment_data)

### Youtube
- [[NDC] 딥러닝으로 욕설 탐지하기](https://youtu.be/K4nU7yXy7R8)


# License
All `korcen` are released under the `Apache-2.0` license. When using the model and code, please comply with the license. 

- License notice and copyright notice required (displayed in areas accessible to the public)

Copyright© All rights reserved.
