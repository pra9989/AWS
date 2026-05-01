  Complete End To End Generative AI Project On AWS Using AWS Bedrock And AWS Lambda
  <img width="1474" height="929" alt="image" src="https://github.com/user-attachments/assets/767bf544-4756-4d2b-a1b0-fd3c77ac9e91" />
Blog Generation
> create API
Amazon Bedrock
 Here we will have all the foundational models will be available. Foundational models in bedrock are
Lama 3
Lama 2
paid from cloudy antropic
> <img width="1427" height="1011" alt="image" src="https://github.com/user-attachments/assets/29db65c5-3856-464f-a594-fe13a8b712b1" />
Foundational models supports caht, text and image.
Foundational models (A121 labs(jurassic-2 series), Titan(by amazon), AI claude(by anthropic), command(by cohere), llama3(by meta), Mistral (by Mstral AI), stable difussion (by stability AI)
> LLama3
> <img width="1449" height="887" alt="image" src="https://github.com/user-attachments/assets/060f3dc2-6fbc-4ccb-8ec2-5152fe73eb41" />
LLama 2chat 13Bv1 (chain of thought)
LLama 2chat 13Bv1 (debug code)
LLama 2chat 13Bv1(Few shot learning )
In python code we have included the
> import json
> import response
> from datetime import datetime
Model access
<img width="1847" height="481" alt="image" src="https://github.com/user-attachments/assets/745659d3-640d-4e98-9327-0f3864077ffa" />
<img width="1425" height="957" alt="image" src="https://github.com/user-attachments/assets/d6d18d8e-bb11-4698-ba7e-f9920e9e5196" />
<img width="1835" height="542" alt="image" src="https://github.com/user-attachments/assets/554c6bb4-35d8-43ff-8fd8-5fbfe678fbc2" />
After clicking on manage model access you need to select which models you need
 <img width="1414" height="1021" alt="image" src="https://github.com/user-attachments/assets/3ea1eb57-2657-4d8a-bfeb-712516eef3da" />
after selecting go on click save changes
<img width="1882" height="809" alt="image" src="https://github.com/user-attachments/assets/6f155f8c-05a1-4148-a73a-2c80bbadb58a" />
The model access will be granted
<img width="1392" height="886" alt="image" src="https://github.com/user-attachments/assets/f33f843d-c224-4a0c-808d-91a942092a08" />
<img width="1696" height="826" alt="image" src="https://github.com/user-attachments/assets/747666c2-446c-4b04-85e6-9f809625b5d6" />
<img width="1630" height="863" alt="image" src="https://github.com/user-attachments/assets/e8d7c440-6619-4544-bc3c-9ee7c96e6657" />
<img width="1703" height="653" alt="image" src="https://github.com/user-attachments/assets/e412adf1-ef21-4055-b76a-30f814fb9e86" />
<img width="1621" height="779" alt="image" src="https://github.com/user-attachments/assets/034a2410-3146-41aa-94ba-9064ce886e61" />

import boto3
import botocore.config
import json

from datetime import datetime

def blog_generate_using_bedrock(blogtopic:str)-> str:
    prompt=f"""<s>[INST]Human: Write a 200 words blog on the topic {blogtopic}
    Assistant:[/INST]
    """

    body={
        "prompt":prompt,
        "max_gen_len":512,
        "temperature":0.5,
        "top_p":0.9
    }

    try:
        bedrock=boto3.client("bedrock-runtime",region_name="us-east-1",
                             config=botocore.config.Config(read_timeout=300,retries={'max_attempts':3}))
        response=bedrock.invoke_model(body=json.dumps(body),modelId="meta.llama2-13b-chat-v1")

        response_content=response.get('body').read()
        response_data=json.loads(response_content)
        print(response_data)
        blog_details=response_data['generation']
        return blog_details
    except Exception as e:
        print(f"Error generating the blog:{e}")
        return ""

def save_blog_details_s3(s3_key,s3_bucket,generate_blog):
    s3=boto3.client('s3')

    try:
        s3.put_object(Bucket = s3_bucket, Key = s3_key, Body =generate_blog )
        print("Code saved to s3")

    except Exception as e:
        print("Error when saving the code to s3")



def lambda_handler(event, context):
    # TODO implement
    event=json.loads(event['body'])
    blogtopic=event['blog_topic']

    generate_blog=blog_generate_using_bedrock(blogtopic=blogtopic)

    if generate_blog:
        current_time=datetime.now().strftime('%H%M%S')
        s3_key=f"blog-output/{current_time}.txt"
        s3_bucket='aws_bedrock_course1'
        save_blog_details_s3(s3_key,s3_bucket,generate_blog)


    else:
        print("No blog was generated")

    return{
        'statusCode':200,
        'body':json.dumps('Blog Generation is completed')
    }

    



