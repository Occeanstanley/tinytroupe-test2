# tinytroupe-test2

Step 1: Install Packages
Open a terminal from Codespace on Github. In the terminal, run the following command to clone the repository:

git clone https://github.com/microsoft/tinytroupe
Change directory into the tinytroupe folder:

cd tinytroupe
Install the package:

pip install .
Step 2: Setup API Key
In the terminal that you just installed packages, use the following command to setup API Key:

export OPENAI_API_KEY="xxxx"
Step 3: Experiments (Simulation)
Talk to an existing persona
from tinytroupe.examples import create_lisa_the_data_scientist
lisa_ds = create_lisa_the_data_scientist() # instantiate a Lisa from the example builder
lisa_ds.listen_and_act("Tell me about your life.")
Talk to a customized persona
This implies you need to define a new persona using tinytroupe package.

from tinytroupe.agent import TinyPerson

yiqiao = TinyPerson("Yiqiao")
yiqiao.define("age", 35)  # Adjust the age as per your requirement
yiqiao.define("nationality", "Chinese")
yiqiao.define("occupation", "He is a professor in a university.")
Use the method .listen_and_act to have a conversation with the persona you defined above

yiqiao.listen_and_act("Tell me about yourself.")
Observe a conversation between two personas
This implies you have at least two personas defined. Since we already defined one above, let us define another one.

from tinytroupe.agent import TinyPerson

john = TinyPerson("John")
john.define("age", 22)  # Adjust the age as per your requirement
john.define("nationality", "American")
john.define("occupation", "He is a student in a university.")
To instantiate a conversation between two personas above, you will need TinyWorld function.

from tinytroupe.environment import TinyWorld

world = TinyWorld("Classroom", [yiqiao, john])
world.make_everyone_accessible()

yiqiao.listen("I want to extend my homework.")
world.run(3) # trigger the conversation with 3 rounds back-and-forth

Questions need to be answered:
1.How to install tinytroupe packages?
  To install the tinytroupe package, follow these steps: 
  # 1. Clone the GitHub repository
$ git clone https://github.com/microsoft/TinyTroupe.git
$ cd TinyTroupe

  # 2. Install the package using pip
$ pip install .

2.What is Turing Test? In today's world with Large Language Models (LLMs), what is the definition of Turing Test?
  
  The Turing Test, proposed by Alan Turing in 1950, is a way of evaluating a machine's ability to exhibit intelligent behavior equivalent to, or indistinguishable from, that of a human.
  Turing Test with LLMs Today:

In the era of Large Language Models (LLMs) like ChatGPT or GPT-4, the Turing Test is redefined as:
Can the model generate language-based interactions that are indistinguishable from a real person?
can it handle nuanced, emotional, or logical conversations believably?
Modern versions of the Turing Test evaluate:
Personality consistency
Context awareness
Creativity and empathy
Realistic human back-and-forth

3.Create a simulation of your own topic and show me the transcript. This implies define at least two personas of your own choice with conflict built in and observe their conversation. You can simply copy/paste the conversation in a .md file. Please comment on the transcript whether you think the Turing Test is passed.

...The following is my conversation...
Yes, this passes the Turing Test. If someone read this conversation without context, they might assume it’s from a real classroom discussion.

>>> world.make_everyone_accessible()
>>> alex.listen("i want an extansion to my homework.")
USER --> alex: [CONVERSATION] 
          > i want an extansion to my homework.
TinyPerson(name='alex')
>>> world.run(3)
──────────────────────────────────────────────────────────────────── classroom step 1 of 3 ────────────────────────────────────────────────────────────────────
stan acts: [DONE] 

stan --> alex: [CONVERSATION] 
          > I manage my time by creating a detailed schedule that outlines my work shifts and class
          > times. I try to set aside specific hours for studying and completing assignments, and I
          > make sure to communicate with my supervisors at the hospital about my availability. It
          > can be tough, but staying organized helps me a lot.
alex acts: [TALK] 
          > I understand that you want an extension for your homework. Can you please explain why
          > you need it?
alex acts: [DONE] 

alex --> stan: [CONVERSATION] 
          > I understand that you want an extension for your homework. Can you please explain why
          > you need it?
──────────────────────────────────────────────────────────────────── classroom step 2 of 3 ────────────────────────────────────────────────────────────────────
stan acts: [THINK] 
          > I need to explain my situation clearly to Alex. I have been juggling my responsibilities
          > at work and school, and I fell behind on my homework. I should mention how my work
          > schedule has been hectic lately and that I want to ensure I submit quality work instead
          > of rushing it.
stan acts: [TALK] 
          > I appreciate your understanding, Alex. I've been balancing my work at the hospital and
          > my studies, and it's been quite challenging. I fell behind on my homework because of my
          > hectic schedule, and I want to ensure I submit quality work. That's why I'm requesting
          > an extension.
stan acts: [DONE] 

stan --> alex: [CONVERSATION] 
          > I appreciate your understanding, Alex. I've been balancing my work at the hospital and
          > my studies, and it's been quite challenging. I fell behind on my homework because of my
          > hectic schedule, and I want to ensure I submit quality work. That's why I'm requesting
          > an extension.
alex acts: [TALK] 
          > Thank you for explaining your situation, Stan. I understand that balancing work and
          > studies can be tough. Given your circumstances, I can grant you an extension. How much
          > extra time do you think you will need to complete your homework?
alex acts: [DONE] 

alex --> stan: [CONVERSATION] 
          > Thank you for explaining your situation, Stan. I understand that balancing work and
          > studies can be tough. Given your circumstances, I can grant you an extension. How much
          > extra time do you think you will need to complete your homework?
──────────────────────────────────────────────────────────────────── classroom step 3 of 3 ────────────────────────────────────────────────────────────────────
stan acts: [THINK] 
          > I need to consider how much extra time I would realistically need to complete my
          > homework. Since I've been struggling to keep up, I think an additional week would give
          > me enough time to catch up and ensure I do a good job on the assignment.
stan acts: [TALK] 
          > Thank you, Alex! I really appreciate your understanding. I think an extra week would be
          > ideal for me to complete the homework and ensure it's up to standard.
stan acts: [DONE] 

stan --> alex: [CONVERSATION] 
          > Thank you, Alex! I really appreciate your understanding. I think an extra week would be
          > ideal for me to complete the homework and ensure it's up to standard.
alex acts: [TALK] 
          > Alright, Stan. I can grant you an extra week for your homework. Please make sure to use
          > this time wisely and reach out if you need any further assistance.
alex acts: [DONE] 

alex --> stan: [CONVERSATION] 
          > Alright, Stan. I can grant you an extra week for your homework. Please make sure to use
          > this time wisely and reach out if you need any further assistance.

>>> stan.listen("Professor Alex, can I please get a 2 day extension? I had to work a double shift at the hospital.")
USER --> stan: [CONVERSATION] 
          > Professor Alex, can I please get a 2 day extension? I had to work a double shift at the
          > hospital.
TinyPerson(name='stan')
>>> alex.listen("I’ll consider it, Stan. Just send me the part you have finished so far.")
USER --> alex: [CONVERSATION] 
          > I’ll consider it, Stan. Just send me the part you have finished so far.
TinyPerson(name='alex')
>>> maya.listen("Wait that’s not fair! I stayed up all night finishing my work on time. Why does he get an exception?")
USER --> maya: [CONVERSATION] 
          > Wait that’s not fair! I stayed up all night finishing my work on time. Why does he get
          > an exception?
TinyPerson(name='maya')
>>> stan.listen("Maya, I respect your effort, but my job is saving lives. Sometimes that means I don’t sleep for 24 hours.")
USER --> stan: [CONVERSATION] 
          > Maya, I respect your effort, but my job is saving lives. Sometimes that means I don’t
          > sleep for 24 hours.
TinyPerson(name='stan')
>>> maya.listen("And I respect that, but academic rules apply to everyone. What’s the point of deadlines then?")
USER --> maya: [CONVERSATION] 
          > And I respect that, but academic rules apply to everyone. What’s the point of deadlines
          > then?
TinyPerson(name='maya')
>>> alex.listen("Alright, both of you, calm down. Let’s discuss this respectfully. Extensions are handled case-by-case.")
USER --> alex: [CONVERSATION] 
          > Alright, both of you, calm down. Let’s discuss this respectfully. Extensions are handled
          > case-by-case.
TinyPerson(name='alex')
>>> world.run(3)
──────────────────────────────────────────────────────────────────── classroom step 1 of 3 ────────────────────────────────────────────────────────────────────
stan acts: [THINK] 
          > I need to respond to Maya's request for an extension. I understand the pressure she is
          > under, but I also have my own responsibilities at the hospital. I should express my
          > understanding while also emphasizing the importance of my job.
stan acts: [TALK] 
          > I understand the challenges you're facing, Maya. Balancing work and school can be really
          > tough. However, my job at the hospital requires me to be available, and sometimes that
          > means I have to prioritize it over other commitments. I hope you can understand my
          > position.
stan acts: [DONE] 

stan --> alex: [CONVERSATION] 
          > I understand the challenges you're facing, Maya. Balancing work and school can be really
          > tough. However, my job at the hospital requires me to be available, and sometimes that
          > means I have to prioritize it over other commitments. I hope you can understand my
          > position.
alex acts: [TALK] 
          > I appreciate your perspective, Stan. It's important to find a balance between work and
          > school. Let's ensure we communicate openly about any challenges you face moving forward.
alex acts: [DONE] 

alex --> stan: [CONVERSATION] 
          > I appreciate your perspective, Stan. It's important to find a balance between work and
          > school. Let's ensure we communicate openly about any challenges you face moving forward.
──────────────────────────────────────────────────────────────────── classroom step 2 of 3 ────────────────────────────────────────────────────────────────────
stan acts: [THINK] 
          > I need to acknowledge Alex's understanding and express my willingness to communicate
          > openly about any challenges I face. It's good to know that I have support, and I should
          > make an effort to keep him updated on my situation.
stan acts: [TALK] 
          > Thank you, Alex. I really appreciate your understanding and support. I will definitely
          > keep you updated on any challenges I face moving forward. It's reassuring to know that I
          > can communicate openly with you.
stan acts: [DONE] 

stan --> alex: [CONVERSATION] 
          > Thank you, Alex. I really appreciate your understanding and support. I will definitely
          > keep you updated on any challenges I face moving forward. It's reassuring to know that I
          > can communicate openly with you.
alex acts: [TALK] 
          > You're welcome, Stan! I'm glad to hear that you feel supported. Remember, I'm here to
          > help you succeed, so don't hesitate to reach out if you need anything else.
alex acts: [DONE] 

alex --> stan: [CONVERSATION] 
          > You're welcome, Stan! I'm glad to hear that you feel supported. Remember, I'm here to
          > help you succeed, so don't hesitate to reach out if you need anything else.
──────────────────────────────────────────────────────────────────── classroom step 3 of 3 ────────────────────────────────────────────────────────────────────
stan acts: [THINK] 
          > I appreciate Alex's willingness to help me succeed. It's important to have that support,
          > especially while balancing work and school. I should keep this in mind and not hesitate
          > to reach out when I need assistance.
stan acts: [DONE] 

alex acts: [DONE] 
