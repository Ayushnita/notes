Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: aws
Topic: aws sdk s3   


---

# __S3 methods avilable for java__   

__Question__  List all buckets in s3?   

Steps:  

* create a s3 instance.  
* get buckets list by using listBuckets.  
* then you require to iterate over it.  

__Question__ Read a file from s3 bucket?  

All avobe steps then below metion object.  

* you can you create a s3Object using s3.getObject()  method that take two perameter   
	* bucket name   
	* file name  
* convert Object into s3inputstream  
* create a object mapper.  
* readValue using mapper that convert it into a json class.  

__Question__ Cerating a new bucket ?  

* create a s3 object.  
* s3.createBucket(bucketName)   
* Region pick up from config from cli.  

__Question__ Upload data in bucket?  

* create a file.  
* use mapper to writeValue in file --> (writeValue)  
* use s3.putObject(bucket, keyname/fileName, <JAVA FILE>);   

__Question__ how to check bucketExist?  

s3.doesBucketExistV2  

__Question__ Delete item from bucket?

s3.deleteObject(bucket name, key/fileName)  

__Question__ Delete bucket itself?   

s3.deleteBucket(bucketName);   


