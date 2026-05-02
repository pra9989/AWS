import ollama
client = ollama.client()
model = "llama2"
prompt = "what is python?"
response = client.generate(model=model, prompet=prompt)
print("Response from ollama")
print(response.response)
<img width="1337" height="825" alt="image" src="https://github.com/user-attachments/assets/2b3bc29b-d093-4ee1-a5f1-6a02dc7f98a0" />
