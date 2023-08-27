<p align="center">
  <img width="700" src="https://i.ibb.co/Cm104BN/Screenshot-2023-08-27-201811.png">
</p>

<h1 align="center">GSOC 2023 with Metacall</h1>

## What the heck is metacall?

<p>MetaCall is a polyglot runtime environment that lets developers call functions and methods between different programming languages. For example, we can call a Python function from a Node.js file. It supports languages like NodeJS, C++, C, Ruby, Python, C# & Typescript.<p>

## Metacall FaaS

<p>The Metacall FaaS, which lets you deploy your functions into the Metacall dashboard, is another tool that Metacall offers.</p>

<p>For those who don't understand what FaaS is, Let me explain :- <p>

```
In simple words, As a developer, you don't need to worry about managing servers, devops, or anything else all you need is your functions (the application's entity), and Metacall FaaS will turn it into an API endpoint so you can use it anyway you like. So you can see how intriguing it is and how much time it will save you. Applications that previously took months to develop may now be created in as little as 4-5 hours because to the reduction in complex work.
```

Visit <a href="https://metacall.io/doc.html#/" >metacall.io</a> for more information on Metacal FaaS.

So, Earlier the graphical interface of <a href="dashboard.metacall.io">dashboard.metacall.io</a> can be used to access the Faas service from Metacall in which you have to buy the plans to test the Faas, therefore in as a part of Google Summer of Code 2023, I set out to develop the whole Faas service which mimics the real Faas and developers can now easily test the behaviour of real Faas in their local environments(localhost).


You can find our work on github <a href="https://github.com/metacall/faas">Metacall Faas</a>.

## How it works?

```
MetaCall deployments takes your code package, being inside a repository or zip, loads it into metacall's runtime and runs selected modules, exposing to the local ports that are opened, it also exposes exported functions from modules as serverless functions, and static files.
```

<p>Let me tell you how you can convert your JavaScript functions into an API endpoints although it supports many languages.</p>

<p>Steps to be followed :-</p>

`Step 1` :- Initialize NodeJS using `npm init -y`.

`Step 2` :- Create any .js extension file (ex - `sum.js`) and write functions and export them.

```js
export const sum = (a, b) => a + b;
```

Now that you are almost finished, all that is left to do is generate the `metacall.json` file, which you can do manually or on the fly as if you like. Below is an example of how to manually construct this file.

```json
{
  "language_id": "node",
  "path": ".",
  "scripts": ["sum.js"]
}
```

`Step 3` :- Install metacall-deploy package using `npm install --global @metacall/deploy`

`Step 4` :- Clone metacall-faas package using `git clone https://github.com/metacall/faas.git`

`Step 5` :- 

```sh

# Currently you have to use the cloned version, soon we will ship this project as an npm package

$ cd /faas && npm start

```

`Step 4` :- In your terminal, execute - `metacall-deploy --workdir=PATH-TO-YOUR-APP-DIRECTORY --dev`

<p>And your application will be deployed within no time deployed.</p>

<p> Your application will be launched quickly.</p>

## Here is the quick video explanation for the whole process.

[![Click to Play](https://i.ibb.co/Cm104BN/Screenshot-2023-08-27-201811.png)](https://youtu.be/UUPjUFgWmns)



## Work done for achieving all the things I mentioned above

<p>The major goals of my GSoC with the metacall were completed. These goals were -</p>

### 1. Implementing all the handlers for the flags that can be expected from Metacall Deploy -

Metacall deploy provides 15 CLI flags to consume API endpoints provided in <a href="https://github.com/metacall/protocol/blob/master/src/protocol.ts">Metacall Protocol</a>. A list of all supported options can be <a href="https://github.com/metacall/deploy#supported-arguments-and-commands">found here</a>.

So the handlers for above flags are mentioned below

### 2. Support for all the flags I added

| Flag                   | 
| ---------------------- | 
| `--validate`           |                                 |
| `--workdir`            |
| `--addRepo`            |
| `--delete`            |
| `--inspect`          |
| `--force`            |
| `--logout`           |
| <a href="https://github.com/metacall/faas/commits?author=Creatoon">And a lot More</a>          |     



### 3. Other Works
So till the end of GSOC 2023, I managed to make more than 17 commits and more than 5500 lines of code, Not only I contributed to this project, My work does'nt end here and I will be contributing and maintaining this repository completely till the end, I also contributed to other projects like ```Metacall Deploy``` & ```Metacall Protocol```, I was considered as one of the most autonomous dev of metacall, I always believed only code contributions are not only the way to support open source communities thats why I tried to collaborate with others and arranged meetups and tech talks for metacall.

## Conclusion

The ability to quickly and efficiently deploy your raw functions to the metacall faas via metacall deploy is a game-changer.

There are a lot of learnings that come along with experience and familiarity with the core team and community. Collaboration and team effort are key for the success of any large-scale project.

Community is really important. Never lose sight of the problem we're trying to solve, and constantly pay attention to the needs and worries community.

Following design patterns and modifying pre-existing code help keep the application's consistency. Always create code that is easy to scale, manageable, and loosely connected.

The most significant development in my career has definitely been GSoC and Metacall. I am really grateful to Google and Metacall for providing me with this fantastic platform. This opportunity has unquestionably had a profound effect on me. I've been able to advance from being an open-source contributor to an open-source maintainer because of it.
