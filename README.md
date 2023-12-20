# deploy-kserve-models
  ## Sklearn
    Deploy
     d3x serve create -n sklearn-local --kserve --model_format sklearn -r local --model_path deploy-kserve-models/sklearn/ --protocol_version v2 --min_cpu 1 --min_memory 1
    Prediction
     python kserve_client.py dkubex sklearn-local skl_input.json
  ## Xgboost
    Deploy
      d3x serve create -n xgboost-local --kserve --model_format xgboost -r local --model_path deploy-kserve-models/xgboost/ --protocol_version v2 --min_cpu 1 --min_memory 1
    Prediction
      python kserve_client.py dkubex xgboost-local skl_input.json
  ## Pmml
    Deploy
      d3x serve create -n pmml-local --kserve --model_format pmml -r local --model_path deploy-kserve-models/pmml/ --min_cpu 1 --min_memory 1
    Prediction
      python kserve_client.py dkubex pmml-local pmml_input.json
  ## LightGBM
    Deploy
      d3x serve create -n lgbm-local --kserve --model_format lightgbm -r local --model_path deploy-kserve-models/lightgbm/ --protocol_version v2 --min_cpu 1 --min_memory 1
    Prediction
      python kserve_client.py dkubex lgbm-local skl_input.json
  ## Paddle
    Deploy
      d3x serve create -n paddle-local --kserve --model_format paddle -r local --model_path deploy-kserve-models/paddle/ --min_cpu 1 --min_memory 1
    Prediction
      python kserve_client.py dkubex paddle-local paddle_input.json
  ## Mlflow
    Train
      python mlflow_wine_model_train.py
    Deploy
      d3x serve create -n mlflow-repo --kserve --model_format mlflow -r mlflow --model ElasticnetWineModel --model_version 1 --protocol_version v2 --min_cpu 1 --min_memory 1
    Prediction
      python kserve_client.py dkubex mlflow-repo mlflow_input.json
  ## Custom
    Deploy
      d3x serve create -n custom -r local --kserve --model_format custom --image dkubex123/custom-model:v1 --min_cpu 1 --min_memory 1
    Prediction
      python kserve_client.py dkubex custom custom_input.json
  ## Pytorch
    Deploy
      d3x serve create -n mnist --kserve --model_format pytorch -r local --model_path deploy-kserve-models/pytorch/ --min_cpu 1 --min_memory 1
    Prediction
      python kserve_client.py dkubex mnist pytorch_input.json
  ## Tensorflow-GPU
    Deploy
      d3x serve create -n dogs-vs-cats --kserve --model_format tensorflow -r local --model_path deploy-kserve-models/tensorflow/model/ --min_cpu 1 --min_memory 1 --ngpus 1 --max_memory 10
    Prediction
      pip install pillow h5py tensorflow requests numpy
      python3 tensorflow-train.py -u {url} -i cat.jpg -a {auth token}
