# Retail_Price_Optimization
Choosing the appropriate price for products is essential in the cutthroat retail industry of today. The goal of this study is to optimize retail prices by predicting consumer satisfaction levels with machine learning techniques. This is an essential step in creating dynamic pricing strategies that boost client happiness and sales.

Problem statement: Our goal is to create a model that uses a variety of parameters to forecast a product's ideal pricing. With the help of this prediction, we may price a product intelligently to maximize sales and satisfy customers.

The dataset offers a comprehensive picture for our price optimization assignment because to its different elements, which include product specifics, order details, review details, pricing, competition, time, and customer details.

Our goal is to forecast the best pricing for retail goods by examining this data. This would support the strategic pricing decisions that would lead to the successful optimization of retail prices.

The sample dataset includes various details about each order, such as:

- Product details: ID, category, weight, dimensions, and more.
- Order details: Approved date, delivery date, estimated delivery date, and more.
- Review details: Score and comments.
- Pricing and competition details: Total price, freight price, unit price, competitor prices, and more.
- Time details: Month, year, weekdays, weekends, holidays.
- Customer details: ZIP code, order item ID.

## 🐍 Python Requirements

Let's jump into the Python packages you need. Within the Python environment of your choice, run:

```python
git clone https://github.com/mrparikhh/Retail_Price_Optimization.git
pip install -r requirements.txt
```

Starting with ZenML 0.20.0, ZenML comes bundled with a React-based dashboard. This dashboard allows you to observe your stacks, stack components and pipeline DAGs in a dashboard interface. To access this, you need to launch the ZenML Server and Dashboard locally, but first you must install the optional dependencies for the ZenML server:

```python
pip install zenml["server"]
zenml up
```

If you are running the `run_cid_pipeline.p`y` script, you will also need to install some integrations using ZenML:

```
zenml integration install mlflow -y
zenml integration install bentoml
```

The project can only be executed with a ZenML stack that has an MLflow experiment tracker and BentoML model deployer as a component. Configuring a new stack with the two components are as follows:

```
zenml experiment-tracker register mlflow_tracker --flavor=mlflow
zenml model-deployer register bentoml_deployer --flavor=bentoml
zenml stack register local_bentoml_stack \
  -a default \
  -o default \
  -d bentoml_deployer \
  -e mlflow_tracker
  --set
```

## 🚀 Training Pipeline

Our standard training pipeline consists of several steps:

- `ingest`: Ingests the data from the databas into the ZenML repository.
- `categorical_encoder`: Encodes the categorical features of the dataset.
- `feature_engineer`: Create new features from the existing features.
- `split`: Splits the dataset into train and eval splits.
- `train`: Trains the model on the training split.
- `evaluate`: Evaluates the model on the eval split.
- `decision`:
- `deploy`: Deploys the model to a BentoML endpoint.
