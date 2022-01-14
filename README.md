# Spark-AWS-Intregation
This repository gives a clear understanding of spark and AWS integration.

# Requirements to intregate between spark and aws

 1. Excess key and secret key of AWS
 2. Spark need AWS jars (AWS Spark Jars)
 3. Pass the excess key and secret key to the SparkSession
 
 # Read data from S3
 
 ![image](https://user-images.githubusercontent.com/70854976/149558749-6f2abade-10bf-46f8-808a-8070eccb9ecf.png)
 
 # Write data
 
 ![image](https://user-images.githubusercontent.com/70854976/149557352-5f1ea03d-f210-441c-8374-b7c23910e3c2.png)
 
 # Code
 
 ![image](https://user-images.githubusercontent.com/70854976/149558384-fccbdee3-2f91-45d6-af09-aeaf9ed6e4ef.png)

# Practice-1

     Step1 ---- Download the AWS jars
     Step2 ---- Add those jars to Build path
     Step3 ----Configure spark session with Access key and secret key
     
          val spark = SparkSession.builder()
          .config("fs.s3a.access.key","")
          .config("fs.s3a.secret.key","")
          .getOrCreate()
      
      import spark.implicits._
      
      Step4 ---- Read data from the S3 Bucket
      
           val df = spark.read.format("csv").option("header","true")
           .load("s3a://Superstore1/Sudip_data.csv")
           
      Step 5 ---- Write the data to folder Sudip_Output
      
           df.write.format("com.databricks.spark.avro").mode("overwrite")
           .save("s3a://Superstore2/output/Sudip_Output")
           
           
 
 
 
 


 
