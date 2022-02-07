# Jina FAQ

## Understanding neural search and Jina

### What is neural search, and why is it important for me?

[Neural search](https://docs.jina.ai/get-started/neural-search) leverages the power of deep neural networks to build search systems. Think of any great search engine you have ever used like Google. Even Google uses AI and neural networks to make its search effective. We, as developers, sometimes want to create intelligent search systems, so neural search comes into the picture. [Jina's neural search framework](https://get.jina.ai) helps you build exactly these kinds of search systems.

### What's the quickest way to play with Jina and neural search?

By playing around with [Jina's examples](https://examples.jina.ai) and getting hands-on. All code is available in open-source repos for you to fork and tweak as needed

### What are the prerequisites of getting started with Jina?/ 
### Can I use Jina if I only know Javascript/language X? / 
### Can a non-tech background fresher without any coding experience learn Jina?

To use Jina you'll need only intermediate-level Python and a working PC or Mac. Previous knowledge of ML and AI is a plus, but it's not a requirement. We want Jina to be of use to even the newest people in this field, and that's why the implementation is as simple as possible for developers who want to make neural search systems.

### Where can I learn about Jina as a beginner?

- Try our [bootcamp](https://learn.jina.ai/).
- Go through our [detailed docs](https://docs.jina.ai).
- Read posts on our [blog](https://jina.ai/blog).
- Keep an eye out for our workshops and events, which we announce on our [Slack community](https://slack.jina.ai) and [Meetup group](https://www.meetup.com/jina-community-meetup/).

## Installing Jina

Jina can be installed in three ways:

- via PyPI: `pip install -U jina` 
- via Docker: `docker run jinaai/jina:latest`
- via conda: `conda install jina -c conda-forge` 

For more details about installing Jina, [visit our Docs.](https://docs.jina.ai/get-started/install/)

### ...on Windows

We recommend installing [WSL2](https://docs.microsoft.com/en-us/windows/wsl/install) and running Jina from there. Alternatively, you could try a VM like [Virtualbox](https://www.virtualbox.org/) running a recent Linux distribution.

### ...on Mac

You may have trouble installing or using Jina on your Mac if you have a newer model with an M1 chip. Please follow the steps written [in this blog.](https://docs.jina.ai/get-started/install/troubleshooting/#on-mac-m1)


## Building your search engine

### What are the basic concepts I need to know to build a simple working application?

You need to know [three simple concepts](https://docs.jina.ai/fundamentals/concepts/) to build a simple working application: 

- Document: Jina's primitive data type
- Executor: Perform simple tasks on Documents, like splitting into chunks, encoding into vectors, storing in an index, etc
- Flow: Ties Executors together and lets you scale and serve your neural search application

### Is a neural search system built with Jina compatible with the traditional search system?

You can fully integrate a traditional search system with Jina. 
As in the DocQA example, the first step is pulling candidates and finding out similar passages by vector indexing. The second step is to use a more computationally intensive deep learning model to find the needed answers from the passages.

When doing the recall in the first step, you can use the method based on vector index or TF-IDF or bm25, so it is entirely possible to use the traditional inverted index to recall Jina.

### How much computational resources are needed?

The resources required to build a neural search system with Jina depend on the business requirements, such as data volume, stability requirements, required response time, etc.

The CPU can cope with lesser data volume( up to one million) for a single data type. It is necessary to use GPU for applications with larger data volume - such as retrieving hundreds of millions of videos and requiring millisecond-level feedback.

### Can we use Jina to search specific content in PDFs?

Of course, some customers use Jina to build a search system for the company's internal resources searching, including PDF search, through the text directly searching the relevant semantic content, or through the text to match the images in the PDF.

### My indexed data is taking up too much storage. How can I reduce the size?

You can reduce the size of your indexed data by projecting the embedding to a smaller dimensionality, using pre-trained ResNet results in features represented as 2048d (if you're using a fully connected layer as an embedding layer). You can further encode it into another dimensionality, such as 512. You can achieve this with Finetuner by adopting a multi-layer perceptron on top of your embedding model. For instance, in this tutorial, we attached a SimpleMLP on top of the embedding model, and the final embedding has been encoded into 1024d, two times smaller than the pre-trained embedding. You can do it in 128/256/512 or any compact representation. This should significantly reduce your embedding size.

## Using Executors

### How can I use pre-built Executors?

We provide three ways of using pre-built Executors from [Jina Hub](https://hub.jina.ai). The first way is using the Executor, the second way is used in a Flow via Docker, and the third way is used in a Flow via the source code. [Visit here to see the code snippets and understand the syntax](https://docs.jina.ai/advanced/hub/use-hub-executor/).

###  How can I share my Executors with others?

Executors can be shared by pushing them onto [Jina Hub.](https://hub.jina.ai/). You can choose to share your Executors either publicly or privately. 
By default, Executors are public, but you can make them private by a `secret`. Only people who have the `secret` can access private Executors. If no `--public` or `--private` argument is provided, the Executor is public by default.

### How can I remove my Executor from Jina Hub?
Once published to Jina Hub, Executors cannot be deleted or removed since Jina Hub is a shared space. We suggest re-pushing your Executor with the `--private` argument to remove it from public view.

### Jina Hub Executors are failing to load. What should I do?
It can be because of a connection issue (VPN), and reloading should fix it. 
- If you use `jinahub://`, make sure `install_requirements=True` is added to ````.add(uses='jinahub://Executor, install_requirements=True)````. 
- If you use `jinahub+docker//`, make sure sufficient Docker resources are allocated. 

###  How can I use Jina Hub Executors in a Jupyter Notebook or Google Colab?
Running Jina in Jupyter notebook and Python are the same. So, you can use Executors in the notebook the same way you would in your local system.

## Workshops and swag

### How do I get swag?

[Check out this blog](https://jina.ai/blog/swag/). After you have performed the necessary steps, we will reach out for delivery addresses. Remember to make your certificates public (via social media) and tag us!

### How long will my swag take?/ Why hasn't my swag arrived yet?

We're working extremely hard to get swag packages delivered to your address in the middle of a pandemic. There may be some delays due to COVID restrictions, and we thank you in advance for your patience as we navigate challenges that come our way due to constantly changing regulations. 

### How do I organize a workshop with Jina AI?

Please send an email to devrel@jina.ai or reach out on [Twitter](https://twitter.com/jinaai_).

### How do I write a blog post for Jina AI?

Thanks for showing interest in writing a blog for Jina AI. Nothing excites us more than community contributions. Send a message in Slack with your blog idea and where do you think you might publish it. Our team will reach out to you and reply to the thread. Also, if you are writing a blog, please follow our [writing style guide](https://docs.google.com/document/d/1FA7EHVPvfiIYJreffpaOQZf_FQnP3jFsy8cT73VsYPU/edit) to make sure there are no errors/violations.

## Working for Jina AI

### How can I get a job/internship at Jina AI?

Check out our [careers](https://jobs.jina.ai) page!

## Miscellaneous

### Is it Jina? Jina AI? jina.ai?

- [**Jina AI**](https://jina.ai/) is the organization
- [**Jina**](https://get.jina.ai) is Jina AI's open source neural search framework. 
- [**jina.ai**](https://jina.ai) is Jina AI's company website

Also, we're not JinaAI, Gina, Jina-AI or any other variation

### How do I pronounce Jina?

- **Correct**: Roughly, like *jee-na* with the emphasis on the *jee*. Or exactly the way the name "Gina" is pronounced in English.
- **Incorrect**: *jy-na*, *jee-NA*

## :thinking: Unanswered Questions 

We invite you to answer some unanswered questions on our [FAQ sheet:](https://docs.google.com/spreadsheets/d/1H6-Ysv293azuWM8DlYTXTkNakG_VWHAqbcTCjM2bM1k/edit#gid=0)

- What's the difference between shards and replicas? When should I use each?
- What database backends does Jina support?
- How to run the local server in Colab？
- How to return some data for a flow, and the data is Irrelevant with any input docs?
- If I cascade several Executors in a flow, then which endpoint will use in these Executors for a request posting to a specific gateway?
- I noticed Executors only receive docs of type DocumentArray as the first parameter. Will subclasses be supported in the future?
- What are some alternatives to embed_feature_hashing that we could use [in this example?](https://docarray.jina.ai/datatypes/text/#simple-text-matching-via-feature-hashing)
- Is Jina going to participate in GSoC? 

## :confused: What if My Question Isn't Listed Here?

We see you've chosen to take [the road less travelled](https://www.poetryfoundation.org/poems/44272/the-road-not-taken). We're here to help you on your way!
- First, check out our [docs](https://docs.jina.ai) to see if your query is answered by ~~the wisdom of the Prophecy~~ our documentation.
- If you still don't find what you're looking for, please list your question on our [FAQ Sheet](https://docs.google.com/spreadsheets/d/1H6-Ysv293azuWM8DlYTXTkNakG_VWHAqbcTCjM2bM1k/edit#gid=0)

## :sparkling_heart: Thank You 

This FAQ Document has been made possible due to the efforts of our community members: 
- Sam Joy 
- Chris Evers 
- Bandersnatchx64 
- @sephib 
- Chuangfeng Wang 
- Wenxiang Yang 
- Sungsoo Park 
- @DmitryKey 
- Arpita Jena
- Manya Tuli
- Swapna Devi
- Deep Shikha  
- @JoanFM 
- @bwanglzu 
- @ShubhamSaboo 
- @alexcg 
- @alt-shreya
- @joeyouss

## There's an Issue with This Document

Missing link? Notice a typo? Create an issue! [Check out our contributing guidelines to know how](https://github.com/jina-ai/jina/blob/master/CONTRIBUTING.md#-bugs-and-issues)
