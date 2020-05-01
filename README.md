This is the base template for the content creation for AltCampus online platform.

### Terms -
Here's the hierarchy in the content platform, in order -

- Track (E.g. Full Stack Web Development)
- Module (E.g. HTML-CSS)
- Topic (E.g. Box Model)
- Exercise (E.g. assignment/content/feedback etc.)
- Block (E.g. text, video, quiz, etc.)

Blocks are the fundamental unit of the content platform.

A track is made up of many modules.
A module is made up of many topics.
A topic is made up of many exercises.
An Exercise is made up of many blocks.

### This folder - Explained
This folder is for a topic. Say - Box Model. For each new topic, please use this template(see the option on right hand side of this repo, near clone the repo) this base template and start putting the content in.

- Ex1-explanation.md - file stands for Exercise 1 that has explanation. It will contain the relevant text para, video link, resource link etc.

- Ex2-assignment-level-1.md - Assignment Level 1, could compromise of writing, fixing issues and sending PR on a repo, quiz, writing code in the platform, etc. It's granular, covering the nuances of the concept.

- Ex3-group-discussion - Check the understanding of the students. Mentor has to give feedback on this. This has to be left blank for now. 

- Ex-4-assignment-level-2 - Post group discussion, do the second level assignment on the topic. The complexity increases. Mentor has to review this.

- Ex-5-feedback (Feedback) - Mentor has to provide feedback on the activities done so far the same day. This file has to be left blank.

The second day of the topic -

- Ex-6-assignment-level-3 - Putting everything together, an assignment that tests all the concepts and a bit more hard. Mentor has to review this.

- Ex-7-writeup - Write an article on your understanding of the concept. Mentor has to review this. This has to be left blank for now. 

So right now, you only need to fill the content in following files - 
1. Ex1-explanation.md
2. Ex2-assignment-level-1.md
3. Ex-4-assignment-level-2
4. Ex-6-assignment-level-3

### Things to keep in mind.

- Please make sure naming is consistent. The repo name has to start with 'AC'. Then module name, followed by topic name.

Module names - 
- For Unix & Git - GIT
- For HTML & CSS - STYLE
- For Core JavaScript - JS
- For React & Redux - FRONTEND
- For Node & Mongo - BACKEND

So if we are doing Box model then the name should be - 'AC-STYLE-box-model', if we are spliting a topic into two topics then it should be - 'AC-STYLE-box-model-1' and 'AC-STYLE-box-model-2'.

Another example - if we are doing 'Mongodb Indexes and Aggregation pipeline' topic then the name should be - 'AC-BACKEND-mongodb-indexes-and-aggregation-pipeline'

- You shouldn't change the filenames inside the repo.

- Each exercise is made up of multiple blocks. So please mention the kind of block that you are referring to the heading in H2 tag (in markdown ## means H2). Each heading in the para should be in H3 tag (in markdown ###). Each subheading shoul be in H4 tag(in markdown ####). Rest should be simple paragraphs in markdown.

For example, if I am writing the Ex1-explanation.md of 'AC-GIT-unix-basics' then I will write something like this - 

```

## BLOCK-readText

### What is Unix
Unix is an operating systems. To be functional in Unix, you need to know certain commands.

#### Useful Unix commands
- ls - lists all the files and folders.
- cd - change directory.
..... more content.

```

Here's the list of blocks that we currently support, -

They are basically two types- read or write. 'read' means student has to only read the section and there is no active assignment with it. 'write' means student has to do something.

['readText', 'readVideo', 'writeQuiz', 'writeSubmissionURL', 'writeGithubURL',  'writeTextAnswer', 'writeCode']

```
'readText'- Read the following text (basically a paragraph) 
'readVideo'- Read/watch the following video (basically a video embedded)
'writeQuiz'- Attempt this Quiz.
'writeSubmissionURL'- Submit your submission URL(usually for demos, codesandbox etc).
'writeGithubURL'- - Submit your Github repo/ URL (For Pull requests etc.)
'writeTextAnswer'- Write your answer (Mostly when explanation of concept is needed) 
'writeCode'- Write code. (When student has to write code to solve a problem).
```

Say if I am making a Quiz block then it should look like this. 

```

## BLOCK-writeQuiz

Q. What does the 'mkdir' command do?
- [ ] make a new file
- [x] make a new directory
- [ ] change the directory
- [ ] read a file

```
