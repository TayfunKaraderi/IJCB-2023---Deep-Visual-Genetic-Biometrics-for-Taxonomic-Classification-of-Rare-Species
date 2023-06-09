# WACV-2024---Deep-Visual-Genetic-Biometrics-for-Taxonomic-Classification-of-Rare-Species
Contains source code for https://arxiv.org/abs/2305.06695 - Visual dataset is avaliable at http://endlessforams.org.

# Guide
1. Download forams dataset from http://endlessforams.org, cut text and borders out using processing.py. Then, place those files into datasets folder in train and test folders.
2. To train with full dataset, run command such as:
```
  python train.py --out_path=output/ --folds_file=datasets/splits/all_32_classes.json --img_rows=224 --img_cols=224 --model=TripletResnetSoftmax --learning_rate=0.001 --embedding_size=128 --logs_freq=20 --num_epochs=30 --eval_freq=2 --batch_size=16 --loss_function=OnlineReciprocalSoftmaxLoss
```

3. To train with genetic anchors, use loss_cosine.py (in place of loss.py) and utils_dna.py (in place of utils.py) and train_dna.py(instead of train.py). Model weights for the results table are provided in the output file. 

4. To visualize embeddings with tsne, run command such as:
```
  python visualise_embeddings.py --model_path=output/full_data_rotation_augmented/best_model_state.pkl --dataset=Forams --batch_size=1 --embedding_size=128 --current_fold=0 --folds_file=datasets/splits/all_35_classes.json --save_path=output/fold_0
```
5. To obtain test set performance, run command such as:
```
python test_save.py --model_path=output/augmentations/ALL_AUG_ep10/best_model_state.pkl --dataset=Forams --batch_size=16 --embedding_size=128 --current_fold=0 --folds_file=datasets/splits/all_35_classes.json --save_path=output/full_data_rotation_augmented
```
