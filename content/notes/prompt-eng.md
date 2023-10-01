### Knobs

- Temperature: higher value -> more deterministic output. lower value -> more creative output (_higher chances of hallucination?_). **essentially increasing the weights of other possible tokens!** as temperature decreases. so obv _**for fact based questions -> lower temp, for creative tasks -> higher temp**_
- Top_p: controls how deterministic the model is at generating responses! treat almost the same way as temperature.

**The general recommendation is to alter one, not both.**


moving ahead with stating the obvious. 🙃

parts of a prompt
- Instruction - a specific task or instruction you want the model to perform
- Context - external information or additional context that can steer the model to better responses
- Input Data - the input or question that we are interested to find a response for
- Output Indicator - the type or format of the output.

imma not write obv things now. waste of time.

seperating the prompt into instruction and input helps.
be precise. concise. dont be clever.

```
Explain the concept prompt engineering. Keep the explanation short, only a few sentences, and don't be too descriptive.
```
 vs
<strong>
```
Use 2-3 sentences to explain the concept of prompt engineering to a high school student.
```
</strong>

dont tell what not to do. tell what to do instead. (basically avoid using directly negative speech??)

```
The following is an agent that recommends movies to a customer. DO NOT ASK FOR INTERESTS. DO NOT ASK FOR PERSONAL INFORMATION.
Customer: Please recommend a movie based on my interests.
Agent: 
```
 vs
<strong>
```
The following is an agent that recommends movies to a customer. The agent is responsible to recommend a movie from the top global trending movies. It should refrain from asking users for their preferences and avoid asking for personal information. If the agent doesn't have a movie to recommend, it should respond "Sorry, couldn't find a movie to recommend today.".
Customer: Please recommend a movie based on my interests.
Agent:
```
</strong>

mfing llms can do all nlp tasks. gibe prompt and boom. prompt with examples perform better in most cases.

gibe examples in da prompt if need answer in a specific format.

```
Classify the text into neutral, negative or positive. 
Text: I think the vacation is okay.
Sentiment: neutral 
Text: I think the food was okay. 
Sentiment:
```


### zero-shot prompting

no context straight question. bigger llms are generally better at this. basically ask questions like you're googling

instruction tuning improves this in llms. improving this will lead to general acceptance of llms (personal opinion).

```
Classify the text into neutral, negative or positive. 

Text: I think the vacation is okay.
Sentiment:
```

### few-shot prompting
basically give a few examples to the llm on how to solve the problem.

enables in context learning. - ability of llms to learn new tasks given a few demonstrations.

try to steer the model to give answers you want (or get better performance), give context before asking question.

not great for reasoning problems, but pretty good for use in labelling data.

```
Q: <Question>?
A: <Answer>
Q: <Question>?
A: <Answer>
Q: <Question>?
A: <Answer>
Q: <Question>?
A:
```

```
This is awesome! // Positive
This is bad! // Negative
Wow that movie was rad! // Positive
What a horrible show! //
```

glean the structure not the specific formats.

cool thing is in modern llms something like this works too.

```
Positive This is awesome! 
This is bad! Negative
Wow that movie was rad!
Positive
What a horrible show! --
```
                 
### chain of thought prompting

![Chain of Thought Prompting](/media/cot.webp "chain of thought prompting")

Bascially improve the reasoning capablities lacking in few shot prompting.

extend the few shot examples with intermediary steps of reasoning.
It boots llms capabilities at reasoning tasks.
the authors claim that this is an emergent ability that arises with sufficiently large language models.
[paper](https://arxiv.org/abs/2201.11903)

### Zero shot COT prompting
![Zero shot COT prompting](/media/zero-cot.webp "zero-shot cot prompting")

basically zero shot but when reasoning fails, add "Lets think about this step by step" and it bolsters the models ability on reasoning tasks.
[paper](https://arxiv.org/pdf/2205.11916.pdf)

### Auto COT prompting
![Auto COT prompting](/media/auto-cot.webp "auto cot prompting")

says that zero-shot cot ain't that good. so what we do is we use zero-shot cot to generate few-shot examples and use cot to get the answer for the intended reasoning question.

the main point is diversity of questions used in few shot examples is very important to mitigate faulty reasoning.
[paper](https://arxiv.org/pdf/2210.03493.pdf)

### Self-Consistency



