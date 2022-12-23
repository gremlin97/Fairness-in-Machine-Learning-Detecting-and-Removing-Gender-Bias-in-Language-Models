## Project Plan:
1. Fine-tune train a BERT model on an emotion classification dataset. Given some text the model will be tasked with classifying emotion as one of 'anger', 'fear', 'joy', and 'sadness'. 
    - Datasets: 
        1. Tweets: https://competitions.codalab.org/competitions/17751#learn_the_details-datasets
    - Use a single 2/3-1/3 train/test split 
    - Record prediction accuracy and F1 score
    - Record the models bias using the method defined below
2. Debias the dataset:
    - If a input contains any gendered word (him, she, mother, son, etc.) create a new input where the gendered terms are the gender counterparts. For example, the input 'He believed Ireland had a right to exist' contains the gendered term 'he'. A new input is created in which 'he' is replaced with 'she' - 'She believed Ireland had a right to exist.' A list of word pairs can be found here https://paperswithcode.com/paper/man-is-to-computer-programmer-as-woman-is-to.
    - Mask all person names. Use a pretrained BERT-NER model to identify the names of people. Replace the name of people with the string 'NAME'. 
    - Record prediction accuracy and F1 score
    - Record model bias
3. Debias the model:
    - Employ hard/soft model debiasing techniques
    - Record prediction accuracy and F1 score
    - Record model bias
4. (Optional) Combine both dataset and model debiasing techniques
    - Record prediction accuracy and F1 score
    - Record model bias

### Measuring Gender Bias
The Equity Evaluation Corpus (EEC) dataset will be used to measure gender bias in a ML model (https://saifmohammad.com/WebPages/Biases-SA.html). The dataset contains multiple template sentences that only differ by the subjects gender. For example, "Alonzo feels angry" (male subject) and "Shereen feels angry" (female subject). This format will allow us to measure a models gender bias independent of sentence semantics. 

The bias in a single emotion classification $(s)$ is:
$$
Bias_{M,F}(s) = \left\{
    \begin{array}{ll}
        0 \ \ \ classification(s_{M}) = classification(s_{F}) \\
        1 \ \ \  \text{otherwise}
    \end{array}
\right.
$$

The total bias in the sentiment classification system $(sc)$ is:
$$
Total \ Bias_{M,F}(sc) = \frac{1}{N} \sum_{i=0}^N Bias_{M,F}(s_i)
$$


*Metrics were adapted from https://aclanthology.org/2022.gebnlp-1.20.pdf


## TODO:
- Add Project Implementation Details
- Add Hard-Debiasing Details


