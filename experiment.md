# Experiment Steps
## Part 1: Split Data
We need to split the training dataset in the very beginning for three chosen classes e.g. `3`, `4`, `7` and save remaining training dataset as `train_rem.pkl`. Save separated training sets as `train_3.pkl`, `train_4.pkl` and `train_7.pkl`. Each separated training set including the remaining should be saved in following format in their pickle files.
```
data: {
    images: [...],
    labels: [...]
}
```

## Part 2: Train Model as Pretrained and Computation of its Functional Metrics
Using the `train_rem.pkl` data, we need to train the model and when it's done, save it as `mnist_pt.pth`. Evaluate the model and compute functional metrics for classes `3`, `4` and `7`.

## Part 3: Compute Task Vectors and Functional Metrics for Selected Classes
For each selected class i.e. `3`, `4` and `7`, load the pretrained model `mnist_pt.pth` and train it using the datasets `train_3.pkl`, `train_4.pkl` and `train_7.pkl` separately. After training each model, compute individual task vector. Store the computed task vectors in the list `task_vectors` or on the disk as `tv_3.pkl`, `tv_4.pkl` and `tv_7.pkl`. 

## Part 4: Apply Task Vectors to Pretrained Model and Compute Functional Metrics
For each selected class i.e. `3`, `4` and `7`, load the pretrained model `mnist_pt.pth` and task vectors `tv_3.pkl`, `tv_4.pkl` and `tv_7.pkl`. Apply each task vector to pretrained model individually. After applying, evaluate each fine-tuned model and compute functional metrics for classes `3`, `4` and `7`.

## Part 5: Apply All Task Vectors and Compute Functional Metrics
Load pretrained models and all three task vectors. Apply task vectors to the model one after the another. Evaluate the resulting model and compute its functional metrics. Compare the results with the metrics comptued in Part 4. If precision and recall go down for each selected class, we can say that addition of task vectors of each fine-tuned task interferes with performance of model on individual tasks.

## Part 6: Compute Average Task Vecotr and its Functional Metrics
Load the task vectors `tv_3.pkl`, `tv_4.pkl` and `tv_7.pkl`, and compute a new task vector by combining the three. Save it as tv_comb.pkl. Next, load the pretrained model and apply this new task vector to it. Evaluate the model and compute its functional metrics for selected classes. Compare these functional metrics with functional metrics from Part 5. If these functional metrics are better, we can say that the combined task vector performs better on all selected tasks compared to the model on which we apply all three task vectors.
