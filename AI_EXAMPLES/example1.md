import ollama
client = ollama.client() \
model = "llama2" \
prompt = "what is python?" \
response = client.generate(model=model, prompet=prompt) \
print("Response from ollama") \
print(response.response) \
<img width="1337" height="825" alt="image" src="https://github.com/user-attachments/assets/2b3bc29b-d093-4ee1-a5f1-6a02dc7f98a0" />
Create a model file then go to the directory from cmd and create the model \
<img width="1846" height="715" alt="image" src="https://github.com/user-attachments/assets/8b482f6a-ddc7-4246-82e1-f34ce435e7f7" />
ollama run mario \
<img width="1919" height="925" alt="image" src="https://github.com/user-attachments/assets/fdb1ad2b-5517-4855-af19-12a276240285" />
https://github.com/ollama/ollama
