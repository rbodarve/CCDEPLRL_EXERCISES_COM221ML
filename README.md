# CCDEPLRL

## Review notes (2026-10-18)

1. Environment: `requirements.txt` has 84 conda `file://` pins and is not installable with pip. Suggested plain pins (from env `ml`): `tensorflow==2.19.0`, `numpy==2.1.3`, `pandas==2.3.3`, `matplotlib==3.10.8`. Ex4 cell 4 unzips `fruits.zip`, which is not in the repo; the `fruits/` folder is already there, and the notebook kernel "CCDEPLRL_EXERCISES" is not defined.
2. Ex6 split: the train/test split is the first/last 80/20 % in file order, with no shuffle. Train is 69.5 % positive, test is 32.3 % positive, and the test set is also the validation data. Val accuracy stays at 0.3234 in the first epochs ("predict all positive"); a shuffled, stratified split and a separate validation set would fix this.
3. Ex5 overfitting: train accuracy is 1.000, and test accuracy is 0.54 (saved) and 0.605 (re-run). No random seed is set. Augmentation or dropout and a fixed seed would help.
4. Ex6 code: cell 17 loops over all of `word_index`, but `weights` has 5000 rows. It is safe now (vocabulary 3130 words) and fails above 5000 words. `Embedding(input_length=)` is deprecated, and `Tokenizer` is a legacy Keras API.
5. Data: `class_names` is hardcoded in Ex4 and Ex5 (correct for the current folders). The lemon split is 212/189/91 (train/validation/test). md5 found no duplicate images across splits.
6. Run check: all 3 notebooks run top to bottom on CPU (TF 2.19.0) with the Ex4 unzip cell skipped. Ex4 test accuracy is 0.968 (saved 0.964). Not tested: GPU, the Colab-only cell, `pip install -r`. Ex6 cell 21 sample reviews contain insults and political labels; neutral examples are better because the repo is public.
