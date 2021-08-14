# AWS-Operationalizing-ML-Project


## Training and deployment

Setting up a Sagemaker instance:
![Alt text](images/1.png)

ml.t2.xlarge is a suitable notebook instance for this project as it has suficient memory form data hangling and is still relatively cheap instance. It has 4 vCPU, 16 GiB and it costs $0.223 per hour. Other avaliable instances can be seen in the following table:
![Alt text](images/2.2.png)

The created notebook instance:
![Alt text](images/2.3.png)

Setting up a S3 Bucket for the project:
![Alt text](images/3.png)

The created AWS S3 Bucket:
![Alt text](images/4.png)

Coping data to the bucket:
![Alt text](images/5.png)

Defininf an EC2 instance for training:
`
estimator = PyTorch(
    entry_point="hpo.py",
    base_job_name='pytorch_dog_hpo',
    role=role,
    framework_version="1.4.0",
    instance_count=1,
    instance_type="ml.m5.2xlarge",
    py_version='py3'
)

tuner = HyperparameterTuner(
    estimator,
    objective_metric_name,
    hyperparameter_ranges,
    metric_definitions,
    max_jobs=2,
    max_parallel_jobs=2,
    objective_type=objective_type
)
`

ml.m5.2xlarge is a suitable training instance for this project as it has suficient memory form deep learning training and is still relatively cheap instance. It has 8 vCPU, 32 GiB and it costs $0.461 per hour. Other avaliable instances can be seen in the following table:
![Alt text](images/7.png)
