# Use an official Python image as the base
FROM python:3.11-bullseye

# Set a working directory in the container
WORKDIR /app

# Copy the requirements file and install dependencies
COPY requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy the Python script into the container
COPY topicmodeling_sentimentanalysis_lda_using_scikit_learn.py /app/topicmodeling_sentimentanalysis_lda_using_scikit_learn.py

# Set the command to run the script
CMD ["python", "topicmodeling_sentimentanalysis_lda_using_scikit_learn.py"]
