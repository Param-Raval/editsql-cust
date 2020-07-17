# nlp_query_builder

### Dependency

The model is tested in python 3.6 and pytorch 1.0. We recommend using `conda` and `pip`:

```
conda create -n editsql python=3.6
source activate editsql
pip install -r requirements.txt
```

Download Pretrained BERT model from [here](https://drive.google.com/file/d/1f_LEWVgrtZLRuoiExJa5fNzTS8-WcAX9/view?usp=sharing) as `model/bert/data/annotated_wikisql_and_PyTorch_bert_param/pytorch_model_uncased_L-12_H-768_A-12.bin`.

Download the database sqlite files from [here](https://drive.google.com/file/d/1a828mkHcgyQCBgVla0jGxKJ58aV8RsYK/view?usp=sharing) as `data/database`.


### Run SParC experiment on EditSQL

First, download [SParC](https://yale-lily.github.io/sparc). Then please follow

- for training run: `run_sparc_editsql.sh`. 
- experimental logs are saved at `logs/logs_sparc_editsql`. Delete `args.log` from there before commencing training
- The dev results can be reproduced by `test_sparc_editsql.sh` with the pre-trained model downloaded from [here](https://drive.google.com/file/d/1MRN3_mklw8biUphFxmD7OXJ57yS-FkJP/view?usp=sharing) and put under `logs/logs_sparc_editsql/save_31_sparc_editsql`.
- The predictions are saved at `logs/logs_sparc_editsql` as `dev_use_predicted_queries_predictions.json`

