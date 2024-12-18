# PetroRAG
**Retrieval Augmented Generation (RAG) application in energy**

First of all is RAG-LLM, then I will do some experiments with NLP and Knowledge Graph. Just want to do something fun with GenAI

## RAG with OpenAI 

Here, for example, a user comes to us and has few reports in his database and he wants to quickly perform a query to get information from the reports.

I use 3 reports from the public Volve dataset; discovery report, completion report, and drilling report of well 15/9-F-15 A. 

![image](https://github.com/user-attachments/assets/a00c32fd-7441-4de0-8f32-a2a3bbc3c445)

## RAG with ColPali and Qwen2

While OpenAI is costly, I use an open source ColPali model (by Illuin Technology) and Qwen2 model (by Alibaba Group) to build a multimodal RAG that can understand reports with charts and tables. 

![image](https://github.com/user-attachments/assets/38d685f2-c782-42e2-80cd-4d2d85956dd0)

This is a free of charge alternative than OpenAI. The only limitation of using ColPali-Qwen2 is that **it requires a very powerful GPU** up to Ampere (GPU A100). You may need Colab Pro to run this. 

### Notebooks: 
* [ColPali](https://github.com/yohanesnuwara/PetroRAG/blob/main/notebooks/colpali.ipynb) Using the pretrained ColPali to generate relevant pages from a collection of reports based on user query
* [Generate Norwegian dataset for fine tuning](https://github.com/yohanesnuwara/PetroRAG/blob/main/notebooks/Generate_Finetuning_Dataset_ColPali_Norwegian_QnA.ipynb) Synthetic dataset for fine tuning pushed to HuggingFace space based on a Norwegian handbook of oil and gas

## Open for contribution/collaboration

There are several challenges that I want to address:
* Most legacy reports are scanned so it has the format of picture. How can we effectively apply OCR?
* Reports have charts, tables, or even equations. How can we use multimodal LLM to understand these information?
* Company reports are highly confidential. How can we use open-source alternatives of OpenAI models to store RAG privately? How are cost compared from one model to another?
* How can we use knowledge graph from reports to help us summarize and find connections between reports?
* Embedding vectors are huge and need storage as there are a lot of reports. How can we use different vector databases and scale up with hundreds or thousands of reports?
* How to finetune RAG with a knowledge to improve the answer for example to teach the system with Petroleum Engineering knowledge?
* How to represent multilingual RAG so that it understand reports written in Norwegian for example?
* LLM need a very huge computational power such as the top-notch GPU. Can we use a smaller model - Small Language Model (SLM)?

Open for collaboration, if anyone has ideas on this :)

## References

1. Finetuning ColPali with LoRA - https://github.com/tonywu71/colpali-cookbooks/blob/main/examples/finetune_colpali.ipynb
2. Generate data for finetuning - https://danielvanstrien.xyz/posts/post-with-code/colpali/2024-09-23-generate_colpali_dataset.html
3. Vespa on Docker - https://pyvespa.readthedocs.io/en/latest/getting-started-pyvespa.html#Deploy-the-Vespa-application
4. ColPali on Vespa - https://pyvespa.readthedocs.io/en/latest/examples/visual_pdf_rag_with_vespa_colpali_cloud.html
