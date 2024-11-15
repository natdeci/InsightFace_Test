## Using InsightFace for Live Face Recognition


Testing Insightface framework, performing live face recognition via local webcam.


Images for known/identifiable faces should be stored in the same directory in this manner:

```bash
database
├── Andika
│   ├── Andika1.jpg
│   ├── Andika2.jpeg
├── Sam
│   ├── Sam1.png
```

The two notebooks are made to differentiate how the code compare faces from the input frame (webcam) to faces from the database. One uses conventional nested-loop and iterate to each embeddings in the dictionary (where we store the embeddings). The other uses FAISS search in hope for a faster searching speed.


the FPS achieved by the one using nested loop is at 5.30 FPS, while the one with faiss is at 4,10 FPS. This is tested while having a total of 28 known face embeddings. Faiss may perform better on a database with much more image embeddings.


The search is based on cosine similarity, hence in the faiss code the input image and the database is normalized first. Using cosine similarity also provides better accuracy for the face recognition rather than euclidean distance who suffers from the curse of dimensionality, considering the embeddings have 512 dimensions.