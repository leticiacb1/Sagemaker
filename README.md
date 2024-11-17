### AWS Sagemaker

**AWS SageMaker** provides a complete end-to-end workflow for Machine Learning.

> Amazon SageMaker is a fully managed machine learning service. With SageMaker, data scientists and developers can quickly and easily build and train machine learning models, and then directly deploy them into a production-ready hosted environment.

#### Dependencies

```bash
  $ aws configure
```

#### Notebook instances

Notebook instances in AWS SageMaker are used when you need an interactive development environment based on Jupyter Notebooks in the cloud.
Work similarly to a Jupyter Lab or Notebooks, but running on AWS.

##### Create a Notebook instances

1. Create instance

```bash
 $ aws sagemaker create-notebook-instance \
--notebook-instance-name "exp-note-INSPER_USERNAME-01" \
--role-arn "ROLE_ARN" \
--instance-type "ml.t2.medium" \
--volume-size-in-gb 10
```

2. Wait until status change from _Pending_ to _InService_ :

```bash
 $ aws sagemaker describe-notebook-instance --notebook-instance-name "exp-note-YOUR_INSPER_USERNAME-01"
```

When status is  _InService_ look for the **Url** (In **https**) in the output of the command and access in the browser.
Replace the end of the URL `/tree` with `/lab`.


3. Create a notebook in Sagemaker instance with **conda_python3** kernel and run in any cell:

```bash
!wget https://mlops-material.s3.us-east-2.amazonaws.com/sagemaker/01-eda.ipynb
!wget https://mlops-material.s3.us-east-2.amazonaws.com/sagemaker/02-train-model-on-instance.ipynb
!wget https://mlops-material.s3.us-east-2.amazonaws.com/sagemaker/03-train-deploy.ipynb
```

4.  To prevent unnecessary resource expenditure, instances can be stopped and restarted as needed.

Start the instance:
```bash
 $ aws sagemaker start-notebook-instance --notebook-instance-name "exp-note-INSPER_USERNAME-01"
```

Stop the instance:
```bash
 $ aws sagemaker stop-notebook-instance --notebook-instance-name "exp-note-INSPER_USERNAME-01"
```

Delete the instance: 

```bash
 $ aws sagemaker delete-notebook-instance --notebook-instance-name "exp-note-INSPER_USERNAME-01"
```

<br>
@2024, Insper. 9° Semester, Computer Engineering.

Machine Learning Ops & Interviews Discipline