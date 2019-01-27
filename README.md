# Personalize_Chatting_Bot  

The project is compelted in Google AI Winter Camp. There are another [repo](https://github.com/Walleclipse/PersonalityDiscrimination_Chatting) and [repo](https://github.com/xiaotinghe/PCM) from my teamates.

The motivation of our project is that when we communicate with others, our conversations are not only based on the logic and context, but also our personality. People tend to chat with whom has similar characters. So we wonder if we can create a chatting bot with personality that can provide more enjoyable user experiences.

Our project consists of two parts. Firstly, analyze one’s personality basing on current and historic dialog using MBTI personality classification indicators. Secondly, concatenate the personality analysis above with current dialog embedding as chatting generation model’s input. Then seq-2-seq model is used to generate chatting response with personality.

## Method 
The overview of our model is:

In the discrimination model, we use the Kaggle MBTI dataset which includes one’s last 50 posts (on-line behaviors) and personality label from which we extracted 30 posts randomly. We fed biLSTM model (self-attention mechanism based) with Elmo pre-trained model’s embedding.

In the generation model, we concatenate the dialog embedding with personality analysis from the discrimination model as the model’s input, and use seq-to-seq model to generate the response.

<img src="https://github.com/Walleclipse/PersonalityDiscrimination_Chatting/raw/master/demo/chatbot1.png" width="400" >



This work mainly consists of two parts, 1. Personality Discriminator: discriminate the speaker's personality according to some input sentences. 2. Chatting Machine: Ggenerate the corresponding respose according to the input sentence and the speaker's personality. 

<img src="https://github.com/Walleclipse/PersonalityDiscrimination_Chatting/raw/master/demo/model.png" width="800" >

1. Personality Discriminator:

Target of this part is classifying people into 16 distinct personality types across 4 axis, showing their somedialogues or some declaration (or Twitter, Wechat …)  ([kaggle MBTI dataset](https://www.kaggle.com/datasnaek/mbti-type))

We used ELMo pretrained model, Bi-LSTM encoder and self Attention Mechanisms.

2. Chatting Machine:

Given a post X= (x_1,x_2,..,x_n ) and a personality type p of the response
to be generated, the goal is to generate a response Y= (y_1,y_2,..,y_n )
that is coherent with the personality type p.

## Results

The model outputs both personality scores and dialogue response.

<img src="https://github.com/Walleclipse/PersonalityDiscrimination_Chatting/raw/master/demo/chatbot2.jpg" width="300" >

