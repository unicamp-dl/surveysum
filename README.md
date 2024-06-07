# SurveySum: A Dataset for Summarizing Multiple Scientific Articles into a Survey Section

## Description of the dataset

The dataset contains the text of 79 sections of a survey and the full text of the scientific articles that should be used as input to attempt to generate the text of a survey.

Each entry in the dataset is a JSON that contains, among others, the following properties:

| Property | Description |
|:----------|:-----------:|
| survey_title | Title of the survey |
| section_title | Title of the section |
| section_text_in_survey | The text of the section in the survey |
| citations | JSON with the text of all citations used in the section |

The task is to use the title of the section and the survey, along with all the cited papers, to generate text for the section that can be compared to the actual text of the section.

Each entry in the dataset also contains a JSON (generated_section_text) that includes examples of text generated using 9 distinct pipelines. The pipelines are described in the paper "SurveySum: A Dataset for Summarizing Multiple Scientific Articles into a Survey Section". The relationship between the pipeline from the paper and the properties of generated_section_text are:

| Pipeline | Property |
|:----------|:-----------:|
| 1.1 |autosurvey_t5_3b_5_chunks  |
| 1.2 | autosurvey_t5_3b_10_chunks |
| 1.3 | autosurvey_t5_3b_10_chunks_web |
| 2.1 | specter_gpt-3.5-turbo-0125_1_chunks |
| 2.2 | specter_gpt-3.5-turbo-0125_5_chunks |
| 2.3 | specter_gpt-3.5-turbo-0125_10_chunks |
| 2.4 | specter_gpt-4-0125-preview_1_chunks |
| 2.5 | specter_gpt-4-0125-preview_5_chunks |
| 2.6 | specter_gpt-4-0125-preview_10_chunks |

## Read the dataset

```{python}
import json

sections = []
with open('surveysum.jsonl', encoding='utf-8') as fin:
    for line in fin:
        sections.append(json.loads(line))
```