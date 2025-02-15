# Troubleshooting

Let's face it — sometimes things break, and your code and deployment will come back with errors!

But don't worry...

GitHub's version control system, Git, allows you to track changes to your codebase over time. If you or someone else makes a change that introduces a bug or breaks the code, you can quickly revert to a previous, stable state, either through the web interface, the Desktop app, or the command line.

- [Revert a commit in GitHub Desktop](https://docs.github.com/en/desktop/managing-commits/reverting-a-commit-in-github-desktop)
- [Revert to a Vercel deployment](https://vercel.com/docs/deployments/managing-deployments#instant-rollback)

## ChatGPT

When there are things I don't fully understand or when I run into things like deployment errors, I turn to [ChatGPT](https://chatgpt.com/) for help.

For example. I made changes to the tags template, committed the code, but the deployment failed 😭

<img src="https://github.com/astrowp/docs/assets/170225022/0ebe5cc3-b347-44bb-8283-e07c6decfdff" width="750px" />

I then copied the error and pasted it into ChatGPT, asking for an explanation and a fix.

<img src="https://github.com/astrowp/docs/assets/170225022/099a6ebd-7b6f-486b-9959-dec8c79f0c17" width="750px" />

And there was the solution: the tag parameter could not be empty; it must have a value.

I updated the code, and it successfully deployed 😀

I haven't tried it, but there is also this [Astro Helper](https://chatgpt.com/g/g-rhdTzvxST-astro-helper) ChatGPT bot you can use for development and debugging issues.

## CodeGPT

CodeGPT is a VSCode extension that acts as an AI-powered coding assistant.

![296623325-619e296e-fa40-4034-a91c-37c55bddf7d8](https://github.com/astrowp/docs/assets/170225022/d5abbd87-de87-4f46-aa08-691f692e297f)

It integrates various AI models from providers like OpenAI, Microsoft, Google, Mistral, Anthropic, Huggingface, Ollama to offer features such as code auto-completion, error-checking, code explanation, refactoring, documentation generation, bug detection, and unit testing.

For more information, visit the [CodeGPT Visual Studio Marketplace page](https://marketplace.visualstudio.com/items?itemName=DanielSanMedium.dscodegpt).

## Offical Docs

<img src="https://github.com/astrowp/docs/assets/170225022/2006d493-9803-4750-86cd-5b7940c337a3" width="750px" />

[Official Astro Documentation](https://docs.astro.build/en/getting-started/) with guides, resources, and API references to help you build with Astro.

## Tutorials

If you want to learn more about Astro, here are links to tutorials:

<ul>
<li><a rel="nofollow" target="_blank" href="https://www.youtube.com/watch?v=e-hTm5VmofI">Astro Web Framework Crash Course</a> by freeCodeCamp</li>
<li><a rel="nofollow" target="_blank" href="https://www.youtube.com/watch?v=zrPVTf761OI">Astro Crash Course in 20 minutes</a> by Chris Pennington</li>
<li><a rel="nofollow" target="_blank" href="https://www.youtube.com/watch?v=qBOz6TpYAOg">Astro 3.0 Crash Course</a> by James Q Quick</li>
<li><a rel="nofollow" target="_blank" href="https://www.youtube.com/watch?v=NniT0vKyn-E">Astro Crash Course in 60 minutes</a> by @developedbyed</li>
<li><a rel="nofollow" target="_blank" href="https://www.ohansemmanuel.com/books/understanding-astro">Understanding Astro (ebook)</a> by Ohans Emmanuel</li>
<li><a rel="nofollow" target="_blank" href="https://thevalleyofcode.com/astro">The Valley of Code - Astro</a> by Flavio Copes</li>
<li><a rel="nofollow" target="_blank" href="https://www.youtube.com/watch?v=XoIHKO6AkoM">Astro Quick Start Course: Build an SSR Blog</a></li>
<li><a rel="nofollow" target="_blank" href="https://www.youtube.com/watch?v=Gvr4WhgfP0w">How I created a movie application with Astro 3.x</a></li>
<li><a rel="nofollow" target="_blank" href="https://www.youtube.com/watch?v=Fcw4c3wzm7I">You may not ACTUALLY understand Content Collections</a></li>
<li><a rel="nofollow" target="_blank" href="https://www.youtube.com/watch?v=OERqwLy_reA">Build a custom blog platform with Astro and Appwrite</a></li>
<li><a rel="nofollow" target="_blank" href="https://www.youtube.com/watch?v=TwWvNK0yHjI">Astro JS Portfolio Crash Course</a></li>
<li><a rel="nofollow" target="_blank" href="https://egghead.io/courses/build-a-full-stack-blog-with-astro-7ffcf9ec">Build a full stack blog with Astro</a></li>
</ul>
