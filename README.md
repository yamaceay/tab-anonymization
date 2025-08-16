# Text Anonymization Benchmark (TAB)

## Overview

In an era where privacy protection is paramount, the ability to effectively anonymize sensitive text while preserving its utility remains a critical challenge. The **Text Anonymization Benchmark (TAB)** addresses this need by providing researchers and practitioners with a comprehensive, standardized dataset for developing and evaluating text anonymization systems.

TAB is a meticulously curated, open-source corpus comprising **1,268 English-language court cases** from the [European Court of Human Rights (ECHR)](https://www.echr.coe.int/Pages/home.aspx?p=home). Each document has been expertly annotated by human experts to identify:

* **Semantic categories** for personal identifiers (names, locations, organizations, etc.)
* **Masking decisions** based on re-identification risk assessment
* **Confidential attributes** that could lead to discrimination
* **Co-reference relations** linking related entity mentions

This rich annotation framework enables comprehensive evaluation of anonymization techniques across multiple dimensions of privacy protection and data utility.

## Research Foundation

The development and validation of this benchmark is detailed in our research paper: 


> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ildikó Pilán, Pierre Lison, Lilja Øvrelid, Anthi Papadopoulou, David Sánchez, Montserrat Batet. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[The Text Anonymization Benchmark (TAB): A Dedicated Corpus and Evaluation Framework for Text Anonymization](https://arxiv.org/abs/2202.00443),<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_arXiv:2202.00443_.

## Dataset Characteristics

This repository contains **version 1.0** of the Text Anonymization Benchmark. The corpus draws from real-world legal documents, providing authentic linguistic complexity and privacy challenges that researchers encounter in practical anonymization scenarios.

**Key Statistics:**
- **1,268 court cases** from the European Court of Human Rights
- **Manual annotation** by domain experts
- **Quality assurance** through multi-annotator review process
- **Comprehensive coverage** of personal identifiers and privacy-sensitive information

The legal domain was chosen for its rich content of personal information and established privacy requirements, making it an ideal testbed for anonymization techniques. The ECHR cases provide diverse linguistic patterns, entity types, and contextual complexity that reflect real-world anonymization challenges. 

## Data Format

The dataset is provided in a structured **JSON format** using standoff annotations, ensuring easy integration with existing NLP pipelines and annotation tools. Each document is represented as a JSON object containing both the original text and comprehensive annotation metadata.

### Document Structure

Each document object contains the following top-level information:

| Variable name | Description |
|---------------|-------------|
| annotations | an object with document annotations, each containing an object with entity mention annotations |
| dataset_type | which data split the court case belongs to (train /dev / test) |
| doc_id | the ID of the court case (e.g. “001-61807”) |
| meta | an object with metadata for each case (year, countries and legal articles involved etc.) |
| quality_checked | whether the document was revised by another annotator |
| task | the target of the anonymisation task (i.g. who to anonymise) |
| text | the text of the court case used during the annotation |

### Entity Annotation Structure

Each entity mention object under 'annotations' has the following attributes:

| Variable name | Description |
|---------------|-------------|
| entity_type | the semantic category of the entity (e.g. PERSON) |
| entity_mention_id | ID of the entity mention |
| start_offset | start character offset of the annotated span |
| end_offset | end character offset of the annotated span |
| span_text | the text of the annotated span |
| edit_type | type of annotator action for the mention (check / insert / correct) |
| identifier_type | the need for masking, masked if 'DIRECT' or 'QUASI', 'NO_MASK' otherwise |
| entity_id | ID of the entity the entity mention is related to in meaning |
| confidential_status | category of a potential source of discrimination (e.g. beliefs, sexual orientation etc.) |

## License

TAB is released under an MIT License.

The MIT License is a short and simple permissive license allowing both commercial and non-commercial use of the software. The only requirement is to preserve the copyright and license notices (see file [License](https://github.com/NorskRegnesentral/text-anonymisation-benchmark/blob/master/LICENSE.txt)). Licensed works, modifications, and larger works may be distributed under different terms and without source code.

 
