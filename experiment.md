# Experiment Steps
## Part 1: Split Data
We need to split the training dataset in the very beginning for three chosen classes e.g. `1`, `4`, `7` and save remaining training dataset as `train_rem.pkl`. Save separated training sets as `train_1.pkl`, `train_4.pkl` and `train_7.pkl`. Each separated training set including the remaining should be saved in following format in their pickle files.
```
data: {
    images: [...],
    labels: [...]
}
```

## Part 2: Train Model as Pretrained and Computation of its Functional Metrics
Using the `train_rem.pkl` data, we need to train the model and when it's done, save it as `mnist_pt.pth`. Evaluate the model and compute functional metrics for classes `1`, `4` and `7`.

## Part 3: Compute Task Vectors and Functional Metrics for Selected Classes
For each selected class i.e. `1`, `4` and `7`, load the pretrained model `mnist_pt.pth` and train it using the datasets `train_1.pkl`, `train_4.pkl` and `train_7.pkl` separately. After training each model, compute individual task vector. Store the computed task vectors in the list `task_vectors` or on the disk as `tv_1.pkl`, `tv_4.pkl` and `tv_7.pkl`. Evaluate each fine-tuned model and compute functional metrics for classes `1`, `4` and `7`.

## Part 4: Apply Task Vectors to Pretrained Model and Compute Functional Metrics