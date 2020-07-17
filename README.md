# nlp_query_builder

### Dependency

The model is tested in python 3.6 and pytorch 1.0. :

```
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

Edit `data/sparc/tables.json` to add a new table, edit `data/sparc/dev.json` and `data/sparc/dev_no_value.json` to add new questions:
  - Use https://github.com/taoyds/spider#tables and https://github.com/taoyds/spider#question-sql-and-parsed-sql as reference to understand the structure of the files.
  - parsed_sql_examples.sql(https://github.com/taoyds/spider/blob/master/preprocess/parsed_sql_examples.sql) gives examples to help understand the input structure.
  - In `dev.json` and `dev_no_value.json` there is no need to edit anything except the `utterance` and `utterance_toks` as per the new question that you want to ask.
  
Add the new database schema file (.sqlite file) at `data/sparc/databases/new_schema_name/new_schema.sqlite` and add the database name to the list of database names in `data/sparc/dev_db_ids.txt`

After adding new questions, delete the following folders if they exist:
  - processed_data_sparc_removefrom
  - processed_data_sparc_removefrom_test
  - data/sparc_data_removefrom
These folders contain vocabulary files which need to be recreated if you have edited the dev files or added a new schema

Run `output.py` to get a text file named `output.txt` with formatted results.
