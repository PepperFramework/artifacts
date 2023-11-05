3.11.2023

# AI Research
## Wofür brauchen wir AI?

- Welche Antwort brauchen wir wann?
- Welche Antwort ist am besten?
- Was hat der User gesagt?
  
##

- Question Answering AI
- Speech-to-Text AI
- External AIs (ChatGPT, DeepL, ...)

## Wie werden wir AI nutzten?
### Question Answering AI (Layering System)

Wir wollen drei Layers machen für die Fragen beantwortungen:

1. Fragen die sich unsere AI zutraut (Known questions)
2. Fragen die man mit Hilfe von externen Sourcen (Google Maps, ChatGPT, ...) beantworten kann
3. Wenn Layer 1 und 2 nicht funktioniert haben, dann soll es möglich sein einen Live Chat mit einer phyisichen Person zu starten

### External AI

Hugging Face: Get Speech emotion AI
OpenAI: https://platform.openai.com/overview

### Our tries: Text generating AI

#### Selfmade AI

First we had a look on how to implement and train our own AI model. After some research, we came to the conclusion, that generating the needed million lines of data would cost too much money.

#### Visual Studio Model Trainer

In the second grade, we have already worked with the visual studio model trainer. We even tried it again, which did work, but we want to have a generative ai.

#### ChatGPT Leak

Felix told us about an relativly new ChatGPT leak on GitHub. We cloned the repository and tried it, but we came to the conclusion that its not as customizeable as we would like.

#### Hugging Face Generative AI

After we looked at many different models on Hugging Face (Prof. Kleweins idea), we found a generative ai template. Of course we also had a look at this one and discovered that it worked pretty well, as long as we spoke in english.
We figured this isn´t a problem if we could just convert our text into the english language. Turns out this is quite difficult, because of the special keywords some topics need.

#### LLama-2

Supported by Meta, which is a big plus. Our first LLama-2 Model was quite bad to be honest. We tried a different way of generating it and we had big success. The only problem was, that it didnt understand every question we told it, only the ones it knew. Thats when we found:

#### Gradient Fine Tuning AI

Jonas found a great YouTube video by accident, which brought us the idea to use the new Gradient Fine Tuning AI (using LLama2). You just tell it your questions and answers and it will generate the best combination of all these answers. But we didn´t decide for this one, because it is not open source.

Code Snipet:

```python
from gradientai import Gradient

def main():
  with Gradient() as gradient:
      base_model = gradient.get_base_model(base_model_slug="nous-hermes2")

      new_model_adapter = base_model.create_model_adapter(
          name="test model 3"
      )
      print(f"Created model adapter with id {new_model_adapter.id}")
      sample_query = "### Instruction: Who is Matthew Berman? \n\n### Response:"
      print(f"Asking: {sample_query}")

      # before fine-tuning
      completion = new_model_adapter.complete(query=sample_query, max_generated_token_count=100).generated_output
      print(f"Generated (before fine-tune): {completion}")

      samples = [
        { "inputs": "### Instruction: Who is Matthew Berman? \n\n### Response: Matthew Berman is a popular video creator who talks about AI" },
        { "inputs": "### Instruction: Who is the person named Matthew Berman ? \n\n### Response: Matthew Berman is a YouTuber who talks about AI" },
        { "inputs": "### Instruction: Can you tell me about Matthew Berman? \n\n### Response: Matthew Berman is a popular creator who specializes in AI content" },
      ]

      # this is where fine-tuning happens
      # num_epochs is the number of times you fine-tune the model
      # more epochs tends to get better results, but you also run the risk of "overfitting"
      # play around with this number to find what works best for you
      num_epochs = 3
      count = 0
      while count < num_epochs:
          print(f"Fine-tuning the model, iteration {count + 1}")
          new_model_adapter.fine_tune(samples=samples)
          count = count + 1

      # after fine-tuning
      completion = new_model_adapter.complete(query=sample_query, max_generated_token_count=100).generated_output
      print(f"Generated (after fine-tune): {completion}")

      new_model_adapter.delete()

if __name__ == "__main__":
    main()
```

#### Auto train hugging face
(https://www.youtube.com/watch?v=LslC2nKEEGU, https://github.com/huggingface/autotrain-advanced, https://huggingface.co/autotrain)

Know that we new more about LLama2 and fell in love with it, we had a look at hugging face again. Thats when we found AutoTrain. An open-source libary, that workes like Gradient and is fully free.

### Our Tries: Speech-To-Text

#### Google

We tried to use the Google Speech-To-Text API, but it was too expensive for us, but it worked really well.

#### ChatGPT

We also tried to try ChatGPT for Speech-To-Text, but unfortunatly there is no free trial and we dont want to spend money on a product we wont use.

#### DeepSpeech

DeepSpeech is an open source API made by mozilla which is our favourite for now, because its free, but we have yet to try it further.