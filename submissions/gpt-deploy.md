<h1 align="center">GSOC 2023 with Metacall - GPT-Deploy</h1>

## What is metacall?

<p>MetaCall is a polyglot runtime environment that lets developers call functions and methods between different programming languages. For example, we can call a Python function from a Node.js file. It supports languages like NodeJS, C++, C, Ruby, Python, C# & Typescript.<p>

## Metacall GPT-FaaS

Metacall aims to provide a multi-language and multi-platform FaaS solution. It allows you to write functions in different programming languages and then deploy and execute those functions in a serverless environment. This can help simplify development and deployment processes, as you can choose the best-suited programming language for specific tasks without being limited to a single language.

Metacall FaaS essentially acts as a bridge between different programming languages, allowing them to communicate and be executed seamlessly in a serverless context. This can be particularly useful in scenarios where different parts of an application are written in different languages or when developers want to leverage the strengths of various languages within the same project.


More about metacall FaaS <a href="https://metacall.io/doc.html#/" >metacall.io</a>


## Now What is GPT-Deploy

- Although Metacall FaaS is great way to deploy. But in the era of AI, metacall needs to upgrade itself. So I created a intelligent deployer leveraging ChatGpt which on prompting gives us functions. 
- The Function generated can be in any language based on selected options.  It generates function in multiple language and is trained to use previously generated functions . It automatically generates necessary menifest files like metacall.json to entry point.
- Not only it automatically imports function from same language it also does for different language too using metacall api.
- It is not only for automatically generating and co-piloting function generataion but also includes several more features.
- Getting ready made function from AI with gpt-deploy, user can download generated function files as zip or simply can deploy in 1 click on provided UI.
- User can drag and drop files, folder or zip files to either deploy directly to metacall faas or create prompt which can be edited intelligently.
- User can track his deployed files, remove deployments and do many manipulations to the deployments
- UI has been provided to run the function-api that gets created without and POSTMAN client.

## Work done for achieving all the things I mentioned on proposal

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

- A user-friendly interface enhances the potential for altering clients' perspectives on Metacall through its various features.
- Profound insights come hand in hand with experience and getting well-acquainted with the core team and the community. Collaborative efforts and teamwork stand as vital components in ensuring the success of any large-scale project.
- The community holds immense significance. It's crucial to always keep the problem we're addressing in focus and consistently address the needs and concerns of the community.
- By adhering to established design patterns and making adjustments to existing code, we can maintain a consistent user experience throughout the application. Strive to create code that is easily scalable, manageable, and loosely interconnected.
- Reflecting on my career journey, participating in GSoC and my involvement with Metacall stand out as the most pivotal developments. I hold deep gratitude towards Google and the Metacall team for offering me such an exceptional platform. This opportunity has undoubtedly had a profound influence on me, propelling my progression from being an open-source contributor to an open-source maintainer.
