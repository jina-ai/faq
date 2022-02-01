# Installation


## How do I Install Jina?

Jina can be installed primarily in three ways, 

via PyPI: `pip install -U jina` , via Docker: `docker run jinaai/jina:latest`, via conda: `conda install jina -c conda-forge`. 

For more details about installing Jina, [visit our Docs.](https://docs.jina.ai/get-started/install/)

## Is Jina compatible with Windows?

As of the moment, Jina runs smoothly with Mac and Linux but gives some problems in Windows due to the non-TTY nature of the operating system. 

We recommend installing WSL and then running Jina for the benefit of running a Linux distribution. 

If there is scope for options, please try using a Virtual Machine for Ubuntu on Windows to experience minimum difficulties.

## Jina installation causing a problem on Macbook?

Jina's installation on Macbook can be because of the M1 chip. Jina runs smoothly on Macbooks with Intel chips, but due to recent advancements in processors, the M1 is relatively new and can throw some problems. To fix this, please follow the steps written in this blog [TO BE BACKLINKED]


# Technical Concepts

## What is neural search, and why is it important for me?

Neural search leverages the power of deep neural networks to build search systems. 

Think of any great search engine you have ever used like Google. Even Google uses AI and neural networks to make its search effective. 

We, as developers, sometimes want to create intelligent search systems, so neural search comes into the picture. 

[Read more about neural search.](https://docs.jina.ai/get-started/neural-search)

## What are the pre-requisites of getting started with Jina?

Intermediate Python and a working laptop. While previous knowledge of ML and AI is a plus, it is not a required attribute. We want Jina to be of use to even the newest people in this field, and that's why the implementation is as simple as possible for developers who want to make sound search systems.

## What is the quickest way to experience the power of Jina?

By running Jina's quick demos. These examples are easy to understand and help users to experience the power of Jina. [Try our example](https://docs.jina.ai/get-started/hello-world/). For users who have difficulties running the examples, please feel free to message us on #support in our Slack channel!

## Where can I find pre-built examples made with Jina?

[We're always a link away.](http://examples.jina.ai/)

## What are the basic concepts I need to know to build a simple working application?

You need to know three simple concepts to build a simple working application. They are Document, Executors, and Flow. Document is the most basic data type in Jina. Executors allow you to do tasks on the Document. And Flow is used for tying executors into a pipeline to perform more significant tasks. You can learn all about them and [see examples here.](https://docs.jina.ai/fundamentals/concepts/)

## Is the neural search system built with Jina compatible with the traditional search system?

You can fully integrate a traditional search system with Jina. 
As in the DocQA example, the first step is pulling candidates and finding out all similar passages by vector indexing. The second step is to use a more computationally intensive deep learning model to find the needed answers from the passages.

When doing the recall in the first step, you can use the method based on vector index or TF-IDF or bm25, so it is entirely possible to use the traditional inverted index to recall in Jina.


## If I want to build a neural search system with Jina, how much computational resources are needed?

The resources required to build a neural search system with Jina depend on the business requirements, such as data volume, stability requirements, required response time, etc.

For a single data type, if the data volume is within one million, the CPU can cope with it; if the data volume is relatively large - such as retrieving hundreds of millions of videos and requiring millisecond-level feedback - it is necessary to use GPU.


## Can we use Jina to search specific content in PDF?

Of course, some customers use Jina to build a search system for the company's internal resources searching, including PDF search, through the text directly searching the relevant semantic content, or through the text to match the images in the PDF.


## My indexed data size became too big. How can I reduce the size of indexing data?

You can reduce the size of your indexed data by projecting the embedding to a smaller dimensionality, using pre-trained ResNet results in features represented as 2048d (if you’re using a fully connected layer as an embedding layer). You can further encode it into another dimensionality, such as 512. You can achieve this with Finetuner by adopting a multi-layer perceptron on top of your embedding model. For instance, in this tutorial, we attached a SimpleMLP on top of the embedding model, and the final embedding has been encoded into 1024d, two times smaller than the pre-trained embedding. You can do it in 128/256/512 or any compact representation. This should significantly reduce your embedding size.

# Executors

## How can I fetch pre-built Executors from Jina Hub?

We provide three ways of using pre-build Executors from the Jina Hub. The first way is using the Executor, the second way is used in a Flow via Docker, and the third way is used in a Flow via the source code. To see the code snippets and understand the syntax, please visit https://docs.jina.ai/advanced/hub/use-hub-executor/.


## How to upload my Executor on Jina Hub?

Jina Hub allows users to publish and share their Executors.

## How do I share executor with my colleague sitting in another part of the world?

"Executors can be shared by pushing them onto [Jina Hub.](https://hub.jina.ai/) 

You can choose to share your Executors either publicly or privately.  

By default, Executors are public, but you can make them private by a `secret`.

Only people having the `secret` can access the private Executors. If no 

--public or --private argument is provided, then it is public by default. "


## How can I remove Executor pushed to Jina Hub?

Once published to Jina Hub, Executors cannot be deleted or removed since Jina Hub is a shared space.


## Jina Hub Executors are failing to load. What should I do?

It can be because of a connection issue (VPN), and reloading should fix it. Also,

If using `jinahub://`, make sure install_requirements=True is added to 

.add(uses='jinahub://Executor, install_requirements=True). If using jinahub+docker// make sure sufficient docker resources are allocated. 


## How can I use Jina Hub Executors in Jupyter Notebook?

Running Jina in Jupyter notebook and Python are the same. So, you can use Executors in the notebook the same way you would in your local system.

# Jina vs... 

## ... AWS Kendra

- AWS Kendra is an AWS-service-only, and so it has a solid lock-in to the ""cloud only"" AWS infrastructure. You have a free-tier version of it, but it's limited to 3GB of data, so you can't really ""play with it"" from a docker image and go from there; Kendra has stricter limitations. Enterprise version is limited to 5 indexes and 500.000 documents or 150GB of text (per node?); You can run Jina on AWS on the other side, and it's Open Source.

- Kendra seems to cover only text search (NLP), whereas Jina also covers image or media search (multi-modal).

- Jina is an end-to-end search system. You can use Jina to extract semantic embedding, store them, search them, and return them to a user. Kendra doesn't seem to cover the whole pipeline. For example, I can't see any front end interface like Jina Box;

- Both Kendra and Jina use distributed node architecture. But the Kendra granularity of settings (user access, security management, etc.) coming with the whole AWS architecture is more advanced at this stage than Jina;

- In Jina, you can distribute various aspects of your training pipeline on other machines. This would demand another pipeline of AWS services (Sagemaker, etc.) on the Amazon platform. Note: you could also add a GPU for all your embedding creation on Jina;

- With Jina, you can use Jina Hub. A community collection of pre-build custom apps. You can plug and play with some of the latest AI research here. Kendra has only [third-party connectors](https://aws.amazon.com/kendra/connectors/) but not customizable packages;

- Kendra comes with 14 custom pre-trained models. Jina has its hub community platform and integrates with HuggingFace directly. With just one line of code in your YAML file, you can pull any of their pre-trained models. This is a huge benefit in terms of customizations and possibilities. The latest research from Facebook/Google is added daily to the HuggingFace community system. I don't know how you could do this with Kendra;

- Jina supports user-provided ML models, but it also supports community-integrated models;

- Kendra has a user feedback loop integrated to do incremental learning. I guess it's possible to [add this to Jina with](https://github.com/jina-ai/jina-hub/tree/master/rankers/LightGBMRanker) probably, but it's not integrated at this stage.

(( Edit by Jina Team: this ranker can help incremental learning. But using a traditional machine learning approach. We could leverage Finetuner to perform feedback collection and model improvement.))



## ... Vertex.ai

One significant difference is that Vespa is built based on their vector database while Jina as a framework offers the flexibility to switch between different options.
