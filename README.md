Aaron Masek
Cloud Resume Challenge Blog

	The cloud resume challenge was an enduring process that spanned many different aws functionalities to produce a resume that is coded in html and fully on the cloud. Coding the resume in html and styling it with css was a unique challenge. I had no prior experience in either coding language so I had to use my knowledge base from python and java to be able to figure out how to properly adapt the resume to html. This was a fun challenge though and one that with more time could have been used to better style the site. But, learning how a website is coded with html and styled with css was a fruitful learning opportunity that broadens my understanding of how the internet and more specifically websites work. 
	The website domain was created on namecheap and registered under my name. This was my first time ever interacting with creating my own website from scratch and was interesting to see the entire cycle from registration to deployment. The domain was then statically hosted on aws via S3 which stores the domain and other variations in buckets. The other variations are www.aaronmasek.com and resume.aaronmasek.com which each had their own S3 buckets that were created to redirect traffic to the main aaronmasek.com site. The bucket for aaronmasek.com contains the index.html and index.css files which house the coding and styling for the resume. The website also had to be secured with https. This was done with Amazon cloudfront that sends the website to edge locations around the globe. This provides the user that searches for the website a very low latency time so that it can be delivered to their client quickly. And to certify that the site is secure, Amazon certificate manager was used to double check that the connections to the site from these edge locations are protected. 
	Amazon Route 53 was used for its DNS capabilities connecting the aaronmasek.com site to the ip address associated. Route 53 is particularly useful because it uses the structure of aws. For the cloud resume challenge, Route 53 connects the domain name to the S3 bucket that stores the website data.
	There was more coding involved than just the html and css. Javascript was used to create a visitor counter that shows how many people have accessed the site. The visitor counter was stored in a dynamoDB table which is a NoSQL aws service. The counter was able to be updated because of a lambda function that was created using python. This function created a dynamoDB resource and client to connect to the visitor count table stored in dynamoDB. It would then increment the counter for every time the index.html page was visited through the aaronmasek.com site. It would do this through Amazon API Gateway which is the Amazon service that would use the lambda function to handle security and manage the APIs needed in order for the visitor count to increment.
	My largest troubleshooting project within the cloud resume challenge came with this lambda function. I was getting an “internal service error” after saving and deploying the function while believing that I accurately completed the steps. I ended up having to go into the Cloudwatch logs, an aspect of AWS that creates logs from Amazon services that can be viewed and searched within for any error codes that were happening when I tried to access my website. While looking at the stream log, I was able to identify that the error was coming from a lowercase t within a table function on the python code for lambda. Simply switching to a capital T resolved the error and allowed my project to be on its way. However, good lessons were learned such as how to use Cloudwatch logs to identify and troubleshoot any stream issues within AWS. As well as knowing to double and even triple checking code to make sure the syntax is accurate and doing what I want. While it is hard to always ensure that syntax is correct, I now know how crucial and nitpicky coding software is when it comes to human error. More troubleshooting experience came with working with the Cloudfront distributions for each site and the invalidations associated. In order for me to see the updates to the html file that I would make, I would have to create a new invalidation on the distribution for aaronmasek.com to clear the cache and see the changes. And finally, to wrap up the project Github repositories were created to store the html, css, java and python code so that versions can be created and stored for future usage. 

