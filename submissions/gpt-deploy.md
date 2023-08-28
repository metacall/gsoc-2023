<h1 align="center">GSOC 2023 with Metacall - GPT-Deploy</h1>

## What is metacall?

<p>MetaCall is a polyglot runtime environment that lets developers call functions and methods between different programming languages. For example, we can call a Python function from a Node.js file. It supports languages like NodeJS, C++, C, Ruby, Python, C# & Typescript.<p>

## Metacall GPT-FaaS

<p>The Metacall FaaS, which lets you deploy your functions into the Metacall dashboard, is another tool that Metacall offers.</p>

<p>For those who don't understand what FaaS is, let me explain :- <p>

```
In simple words, as a developer, you don't need to worry about managing servers, devops, or anything else, all you need is your functions (the application's entity), and Metacall FaaS will turn it into an API endpoint so you can use it in any way you like. So you can see how intriguing it is and how much time it will save you. Applications that previously took months to develop may now be created in as little as 4-5 hours because of the reduction in complex/unnecessary work.
```

Visit <a href="https://metacall.io/doc.html#/" >metacall.io</a> for more information on Metacall FaaS.


## Now What is GPT-Deploy

- Although Metacall FaaS is great way to deploy. But in the era of AI, metacall needs to upgrade itself. So I created a intelligent deployer leveraging ChatGpt which on prompting gives us functions. 
- The Function generated can be in any language based on selected options.  It generates function in multiple language and is trained to use previously generated functions . It automatically generates necessary menifest files like metacall.json to entry point.
- Not only it automatically imports function from same language it also does for different language too using metacall api.
- It is not only for automatically generating and co-piloting function generataion but also includes several more features.
- Getting ready made function from AI with gpt-deploy, user can download generated function files as zip or simply can deploy in 1 click on provided UI.
- User can drag and drop files, folder or zip files to either deploy directly to metacall faas or create prompt which can be edited intelligently.
- User can track his deployed files, remove deployments and do many manipulations to the deployments
- UI has been provided to run the function-api that gets created without and POSTMAN client.

## Work done for achieving all the things I mentioned above

<p> All the goals proposed has been completed. I have created more features than I proposed. </p>  

### 3. My Works
- Uptill the end of GSOC'23, I commited more than 150 commits and it includes several commits that were removed due to copying to metacall repo.
- Project Creation
- CI/CD pipeline for auto deployments.
- While doing So, I founded many issues which I reported to respected admins like vicente sir.
- I have done all backend , frontend and most part of UI designing.
- I myself have developed the architecture.
- I have created it flexible and scalable for more language addition.
- For now it only supports Python and Node.js.

### Future Prospect
- Although my work includes all the basic to mid level functionalities but in order to maximize its potential we have to upgrade gpt-deploy.
- New langauge like C#, C/C++, java , rust and many more has to be added. I have created it scalable so it won't be hard though for new comers.
- Several modification in UI could be done for smooth user experience based of clients feedback.
- datatype integration in GUI for meaningful output on api call

### Screenshots

![image](https://github.com/metacall/gsoc-2023/assets/66236446/8f4c9a52-c75b-4cb4-9767-5e33694a0864)
![image](https://github.com/metacall/gsoc-2023/assets/66236446/15a9f0bd-119f-4914-b7ed-d667f2d6f433)
![image](https://github.com/metacall/gsoc-2023/assets/66236446/d6742395-2013-43bb-84b6-a767a6144c9d)
![image](https://github.com/metacall/gsoc-2023/assets/66236446/0d204b01-a789-4c50-8f7e-d8d20c9a7a8c)
![image](https://github.com/metacall/gsoc-2023/assets/66236446/f8c2e982-f862-468e-b6ff-dca000f396bd)
![image](https://github.com/metacall/gsoc-2023/assets/66236446/a26335d1-ee2c-45cb-8fa6-d64687de8a6a)
![image](https://github.com/metacall/gsoc-2023/assets/66236446/aacf9e5f-18c0-4caf-8d6f-dc5c9033f196)

## Conclusion

Easy UI for several features has capability to change clients perspective of using metacall.

There are a lot of learnings that come along with experience and familiarity with the core team and community. Collaboration and team effort are key for the success of any large-scale project.

Community is really important. Never lose sight of the problem we're trying to solve, and constantly pay attention to the needs and worries community.

Following design patterns and modifying pre-existing code help keep the application's consistency. Always create code that is easy to scale, manageable, and loosely connected.

The most significant development in my career has definitely been GSoC and Metacall. I am really grateful to Google and Metacall for providing me with this fantastic platform. This opportunity has unquestionably had a profound effect on me. I've been able to advance from being an open-source contributor to an open-source maintainer because of it.
