
# SVM Kernel Approximation

- Python 3.5
- TensorFlow 1.4.1

## Install

[Tensorflow 1.4 Doc](https://github.com/tensorflow/docs/blob/r1.4/site/en/install/install_mac.md#installing-with-anaconda)

```shell
export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/cpu/tensorflow-1.4.1-py3-none-any.whl
pip install --ignore-installed --upgrade $TF_BINARY_URL
```

## Generate test cases

There are some test cases created by running the **./generate.sh** command. These data in test cases are randomly generated by **generate.py** file in order to fit the dataset on compute node.

```shell
./generate.sh
```

## Configurate the data set

Tell the program where the path of the dataset locates. Modify the **config.py** file.

```python
# config.py
train_data_dict = {
        'fcsv_phs': [ './cases/data/3x5.csv', './cases/data/5x10.csv' ],
        'tcsv_phs': [ './cases/target/3x5.csv', './cases/target/5x10.csv' ],
        }
eval_data_dict = {
        'fcsv_phs': [ './cases/data/3x4.csv' ],
        'tcsv_phs': [ './cases/target/3x4.csv' ],
        }

train_dataset_dict = {
        'Short-TrainSet-UdrSamp-3_3_1p0_1p0_0p1': [ './cases/sample/3x5.pkl', './cases/sample/5x10.pkl' ],
        }
valid_dataset_dict = {
        'Short-ValidSet-NoUdrSamp': [ './cases/sample/3x4.pkl' ],
        }

# main.py
X_train_orig = fio.load_file(train_data_dict['fcsv_phs'])
Y_train_orig = fio.load_file(train_data_dict['tcsv_phs'])
X_valid_orig = fio.load_file(eval_data_dict['fcsv_phs'])
Y_valid_orig = fio.load_file(eval_data_dict['tcsv_phs'])
train_sample = fio.load_sample_file(train_dataset_dict['Short-TrainSet-UdrSamp-3_3_1p0_1p0_0p1'])
valid_sample = fio.load_sample_file(valid_dataset_dict['Short-ValidSet-NoUdrSamp'])
```

You can modify the format if you want.

## Run

```shell
python3 main.py
```


