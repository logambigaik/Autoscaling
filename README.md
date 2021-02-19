# AWS Auto Scaling in EC2:
=========================


  >> Click Autoscaling and select Launch Configuration 

![image](https://user-images.githubusercontent.com/54719289/108523784-53e47580-72f4-11eb-906e-afb2db821f7b.png)

  >> Create new EC2 instance and copy AMI Id:
  
 ![image](https://user-images.githubusercontent.com/54719289/108524550-29df8300-72f5-11eb-8ff6-0a18a6a6698a.png)
 
  >> In Autoscaling, select Launch Configuration
  
      Paste ami id under AMI and select the corresponding one and choose t2.micro as Instance type and remaining part choose defult one except Rules (select Port 22).
      
 ![image](https://user-images.githubusercontent.com/54719289/108524959-9b1f3600-72f5-11eb-995d-7d8b46a2837f.png)
 
 ![image](https://user-images.githubusercontent.com/54719289/108525874-8b542180-72f6-11eb-9217-2a43389b8da4.png)  
  
# Created Launch configuration for Auto scaling:

![image](https://user-images.githubusercontent.com/54719289/108526850-a1161680-72f7-11eb-9997-93ccdcf43e5d.png)


# Create Auto Scaling with exiting Launch configuration

![image](https://user-images.githubusercontent.com/54719289/108526850-a1161680-72f7-11eb-9997-93ccdcf43e5d.png)

![image](https://user-images.githubusercontent.com/54719289/108535121-fa367800-7300-11eb-859f-1c98e1dc2143.png)

  >>  Select all subnet:
 
 ![image](https://user-images.githubusercontent.com/54719289/108535221-189c7380-7301-11eb-88f0-3c3a3ab30fb2.png)

# Select No load balnce since we are going to check the CPU resource:

![image](https://user-images.githubusercontent.com/54719289/108536900-fb68a480-7302-11eb-953a-7e4955cd3c48.png)

# Min 1 Max -4

![image](https://user-images.githubusercontent.com/54719289/108537204-59958780-7303-11eb-9ecf-c89fca197faf.png)

# Click Next /Next/Review and create Autoscaling:

![image](https://user-images.githubusercontent.com/54719289/108537562-c6108680-7303-11eb-8473-f42f079f0a31.png)


# Now ASG is created,

![image](https://user-images.githubusercontent.com/54719289/108537619-d58fcf80-7303-11eb-8d22-dc203e865b75.png)

# Click Launch_conf:

![image](https://user-images.githubusercontent.com/54719289/108538085-6bc3f580-7304-11eb-87b5-7e260d6b09c3.png)


  Under Automatic scaling add condition, either by condition or by scedule.
  
        >> Condition:  cpu > 80 % memory
        >> Schedule ==> cron expression [ * * * * *}
              First  denotes * ==> Minute
              2nd            * ==> Hour
              3rd            * ==> day
              4th            * ==> month
              5th            * ==> week of the day
              
# Click Add Policy
![image](https://user-images.githubusercontent.com/54719289/108544947-2c4dd700-730d-11eb-8f50-c5c4d2e4fe12.png)

  Click cloud watch alarm creation,
  (Cloud watch --- used for monitoring, logging and for setting alarm events)
  
  (Select Ec2 instance and Autoscaling Group in Select Metric , Select AGS1-CPU Utilization)
  
![image](https://user-images.githubusercontent.com/54719289/108545397-bf870c80-730d-11eb-8047-a2e52a361f68.png)
![image](https://user-images.githubusercontent.com/54719289/108545760-36240a00-730e-11eb-888e-b5ab43556078.png)

  # Set the Period interval as 1 minute:
 
 ![image](https://user-images.githubusercontent.com/54719289/108546177-c4988b80-730e-11eb-8845-31741314f469.png)

  Click on Next and create topic
 
   # Create Topic:

  ![image](https://user-images.githubusercontent.com/54719289/108547285-4a690680-7310-11eb-839d-bfb2efc9c65d.png)
  
  # Or Create topic in SNS:

  ![image](https://user-images.githubusercontent.com/54719289/108547554-a2077200-7310-11eb-8de4-54ac318342e9.png)
  
          >> Create Subscription:
   
  ![image](https://user-images.githubusercontent.com/54719289/108547836-01658200-7311-11eb-8758-354408dfcf6f.png)
  
  
          >> Mail Confirmation:
  
  ![image](https://user-images.githubusercontent.com/54719289/108548064-51dcdf80-7311-11eb-81e3-5551ce927daf.png)
  
 # Click on Next in CloudWatch on Create Topic:
 
 ![image](https://user-images.githubusercontent.com/54719289/108548507-ecd5b980-7311-11eb-9057-7faa1db0991d.png)
 
 # Set Name and Description for ALarm and Click Next:
 
 ![image](https://user-images.githubusercontent.com/54719289/108548810-5655c800-7312-11eb-9cae-d492c58474ee.png)

# Set the Notification once CPU reaches 40% utilization:

![image](https://user-images.githubusercontent.com/54719289/108549104-ba788c00-7312-11eb-8e52-8c348197182b.png)


# Alarm is created with insufficient data :

![image](https://user-images.githubusercontent.com/54719289/108549224-dd0aa500-7312-11eb-9fa3-41ac435702cf.png)


# Check EC2 Instance:

![image](https://user-images.githubusercontent.com/54719289/108549648-720d9e00-7313-11eb-9fda-b60fbb0d6179.png)

  >> Open Port 22 under Autoscaling instance
  
 ![image](https://user-images.githubusercontent.com/54719289/108549744-99fd0180-7313-11eb-9686-51c72cf30e0a.png)

# To check CPU utilization , use top command

![image](https://user-images.githubusercontent.com/54719289/108550123-21e30b80-7314-11eb-96e2-f9ac3c7c79ed.png)

# Specify below to increase CPU:

      [root@ip-172-31-45-146 ~]# for i in 1 2 3 4; do while : ; do : ; done & done

![image](https://user-images.githubusercontent.com/54719289/108551237-aaae7700-7315-11eb-88c2-3ba796b87497.png)

# Now CPU Utilization % is:

![image](https://user-images.githubusercontent.com/54719289/108551494-0c6ee100-7316-11eb-875c-e640d9c56929.png)


# CPu Utilization is not yet updated and wait for a minute:

![image](https://user-images.githubusercontent.com/54719289/108552038-c9613d80-7316-11eb-9295-0d88b4258747.png)

>> Check the notifcation in email:

![image](https://user-images.githubusercontent.com/54719289/108552141-e7c73900-7316-11eb-86c0-ebc6d00aa5bd.png)

![image](https://user-images.githubusercontent.com/54719289/108552480-5e643680-7317-11eb-9e01-a5f36cfaeea6.png)

  

  
  
              
        


