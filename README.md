# Wikimedia Page View Analysis with Apache Spark

This project analyzes Wikimedia page view statistics using Apache Spark, implementing tasks in both the map-reduce paradigm and Spark loops for performance comparison.

## Prerequisites

Ensure you have the following:
- Google Colab account
- Apache Spark setup in Google Colab
- Dataset downloaded from [here](https://dumps.wikimedia.org/other/pagecounts-ez/2016/2016-01/pagecounts-20160101-000000.gz)

## Dataset

Download the dataset and upload it to your Google Drive. The dataset should be accessible in your Colab environment.

## Project Structure

```
wikimedia-page-view-analysis/
│
├── data/
│   └── pagecounts-20160101-000000.gz
├── spark_map_reduce.ipynb
├── spark_loops.ipynb
└── README.md

```

## Setup

1. Upload the dataset to your Google Drive.
2. Set up Spark in your Colab environment using the following commands:

    ```python
    !apt-get install openjdk-8-jdk-headless -qq > /dev/null
    !wget -q http://apache.mirrors.tds.net/spark/spark-3.1.1/spark-3.1.1-bin-hadoop2.7.tgz
    !tar xf spark-3.1.1-bin-hadoop2.7.tgz
    !pip install -q findspark
    ```

3. Configure environment variables:

    ```python
    import os
    os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-8-openjdk-amd64"
    os.environ["SPARK_HOME"] = "/content/spark-3.1.1-bin-hadoop2.7"
    ```

4. Initialize Spark:

    ```python
    import findspark
    findspark.init()
    ```

## Execution

### Using Spark Map-Reduce

Open the `spark_map_reduce.ipynb` notebook in the `src/` directory in Colab and run the cells:

1. Compute min, max, and average page size
2. Count page titles starting with "The"
3. Determine unique terms in page titles
4. Extract each title and number of times it was repeated
5. Combine data of pages with the same title

### Using Spark Loops

Open the `spark_loops.ipynb` notebook in the `src/` directory in Colab and run the cells:

1. Compute min, max, and average page size
2. Count page titles starting with "The"
3. Determine unique terms in page titles
4. Extract each title and number of times it was repeated
5. Combine data of pages with the same title

## Analysis

### Task 1: Compute the Min, Max, and Average Page Size

- **Map-Reduce:** The notebook uses Spark's RDD transformations and actions to compute the required statistics.
- **Spark Loops:** The notebook iterates over the RDD using Spark's built-in functions to achieve the same.

### Task 2: Count Titles Starting with "The"

- **Map-Reduce:** The notebook filters and counts titles starting with "The" and distinguishes those not part of the English project.
- **Spark Loops:** The same task is accomplished using loop constructs.

### Task 3: Determine Unique Terms in Page Titles

- **Map-Reduce:** The notebook splits titles into terms, normalizes them, and counts unique terms.
- **Spark Loops:** Terms are processed similarly using loops.

### Task 4: Extract Each Title and Its Repeats

- **Map-Reduce:** The notebook groups titles and counts occurrences.
- **Spark Loops:** The same is done using looping constructs.

### Task 5: Combine Data of Pages with the Same Title

- **Map-Reduce:** The notebook aggregates data for pages with the same title.
- **Spark Loops:** The task is achieved using loop constructs.

## Results

The results of the performance comparison for each task are provided above.

## Conclusion

The project demonstrates the efficiency of both map-reduce and Spark loops paradigms in processing large datasets using Apache Spark. The performance comparison provides insights into the advantages and trade-offs of each approach.

## Contributors

- [Nour](https://github.com/NourAlaassarr)
- [Another Contributor](https://github.com/another-contributor)

---
