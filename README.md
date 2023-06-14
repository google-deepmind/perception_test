# Perception Test: A Diagnostic Benchmark for Multimodal Video Models

## News
Join the first Perception Test challenge organised as an ICCV2023 workshop, website here [ptchallenge-workshop.github.io](https://ptchallenge-workshop.github.io/).

| ----------------          | ------------------ |
| Download data            | [Download section](https://github.com/deepmind/perception_test#download-the-data-and-annotations) below      |
| Evaluation scripts (including data loader, dummy baseline, evaluation metrics)               | [Object tracking](https://github.com/deepmind/perception_test/blob/main/baselines/single_object_tracking.ipynb), [multiple-choice video QA](https://github.com/deepmind/perception_test/blob/main/baselines/mc_vqa.ipynb), point tracking (coming soon), action/sound localisation (coming soon), grounded video QA (coming soon)   |
|   Evaluation server     | Coming soon
| Leaderboard            | Coming soon        |


## Overview
[Perception Test: A Diagnostic Benchmark for Multimodal Video Models](https://arxiv.org/abs/2305.13786) is a multimodal benchmark designed to comprehensively evaluate the perception and reasoning skills of multimodal video models. The Perception Test dataset introduces real-world videos designed to show perceptually interesting situations and defines multiple tasks (object and point tracking, action and sound localisation, multiple-choice and grounded video question-answering) that require understanding of memory, abstract patterns, physics, and semantics, across visual, audio, and text modalities.

In this repository, you will find:
* A summary of the Perception Test and the associated challenge
* A detailed description of the data and annotations in the Perception Test (**interactive demo notebook [here](https://github.com/deepmind/perception_test/blob/main/data_visualisation.ipynb)**)
* Details about how to download the data and annotations in the Perception Test (**download section [here](https://github.com/deepmind/perception_test#download-the-data-and-annotations)**)
* Metrics for evaluating the performance on the different tasks (**metrics section [here](https://github.com/deepmind/perception_test#metrics)**)
* Dummy baselines showcasing how to evaluate models on each of the tasks (**baselines section [here](https://github.com/deepmind/perception_test#baselines)**)


## 5-minutes summary of the Perception Test
[![Perception Test Overview Presentation](https://img.youtube.com/vi/8BiajMOBWdk/maxresdefault.jpg)](https://youtu.be/8BiajMOBWdk)

*Try the Perception Test for yourself by accessing this [quiz](https://docs.google.com/forms/d/e/1FAIpQLScp49reYMAByszH6vo_y6umlkBPwsua2-kMpGjff3IV0YzYkw/viewform?usp=sf_link).*

For more example videos in the Perception Test, check out this [playlist](https://youtube.com/playlist?list=PLbMStx8-UPhbaKViNMF8ZcQpyzVhwJC3R).

## Download the data and annotations
The Perception Test dataset can be downloaded as zip files containing:
* annotations in JSON format
* videos (including audio) as MP4 files
* audio-only files in WAV format
* pre-computed features for the action localisation and sound localisation tasks.

**Links**

| Task                      | Split  | Videos | Audio  | Labels |
|---------------------------|--------|--------|--------|-------|
| Sample                    | All    |  [sample_videos.zip (214.9MB)](https://storage.googleapis.com/dm-perception-test/zip_data/sample_videos.zip)     |  [sample_audios.zip (83.9MB)](https://storage.googleapis.com/dm-perception-test/zip_data/sample_audios.zip)     |  [sample_annotations.zip (3MB)](https://storage.googleapis.com/dm-perception-test/zip_data/sample_annotations.zip)    |
| All Tasks                 | Train  |  [train_videos.zip (26.5GB)](https://storage.googleapis.com/dm-perception-test/zip_data/train_videos.zip)      |  [train_audios.zip (12.3GB)](https://storage.googleapis.com/dm-perception-test/zip_data/train_audios.zip)      |  [train_annotations.zip (30.6MB)](https://storage.googleapis.com/dm-perception-test/zip_data/train_annotations.zip)   |
| All Tasks                 | Valid  |  [valid_videos.zip (70.2GB)](https://storage.googleapis.com/dm-perception-test/zip_data/valid_videos.zip)      |  [valid_audios.zip (33.1GB)](https://storage.googleapis.com/dm-perception-test/zip_data/valid_audios.zip)      |  [valid_annotations.zip (81.5MB)](https://storage.googleapis.com/dm-perception-test/zip_data/valid_annotations.zip)    |

## Baselines
In this repo we provide dummy baselines to demonstrate how to load the data, evaluate and recreate some baseline results from the paper. For the other results in the baselines section in the paper, we will be adding another external repo.

| Computational task       |Baseline |
|--------------------------|------------------|
| Object tracking            | [Static baseline](https://github.com/deepmind/perception_test/blob/main/baselines/single_object_tracking.ipynb)       |         
| Multiple-choice video QA           |   [Frequency dummy baseline](https://github.com/deepmind/perception_test/blob/main/baselines/mc_vqa.ipynb) |
| Point tracking             | Static baseline (available soon) |


## Metrics

<!-- The [metrics file](https://link) contains the metric code to evaluate the performance for the different tasks. -->

| Computational task       |Metric |
|--------------------------|------------------|
| Object tracking            |            mean IoU       |
| Point tracking             |              Jaccard |
| Temporal action localisation          |           mean Average Precision |            
| Temporal sound localisation           |           mean Average Precision |            
| Multiple-choice video QA         |           top-1 accuracy|
| Grounded video QA             |            HOTA   |

Metrics code to evaluate performance for the different tasks coming soon.

## Perception Test annotations

**Explore the annotations**: [data_visualisation.ipynb](https://github.com/deepmind/perception_test/blob/main/data_visualisation.ipynb)

**Summary**

| Annotation type          | Number of videos | Number of annotations |
|--------------------------|------------------|-----------------------|
| Object tracks            |           11,609 |       189,940        |
| Point tracks             |              145 |          8,647 |
| Action segments          |           11,353 |             73,503       |
| Sound segments           |           11,433 |                137,128    |
| Multiple-choice video QA         |           10,361 |             38,060|
| Grounded video QA             |            3,063 |                6,086   |

**Video metadata**


| Field Name          | Description                                               |
|---------------------|-----------------------------------------------------------|
| split               | The data split the video belongs to                        |
| video_id            | The ID of the video                                       |
| frame_rate          | The frame rate of the video in frames per second           |
| num_frames          | The total number of frames in the video                    |
| resolution          | The height and width of the video in pixels                |
| audio_samples       | The total number of audio samples in the video             |
| audio_sample_rate   | The sample rate of the audio in the video in Hz            |
| is_cup_game         | Whether the video shows a cups-game or not                 |
| is_camera_moving    | Whether the camera used to film the video is moving or not |


**Object tracks**

| Field Name             | Description                                                             |
|------------------------|-------------------------------------------------------------------------|
| task_id                | A unique annotation ID for each object track                             |
| label                  | The name of the object, can also contain object attributes               |
| is_occluder            | Whether the object occludes other objects in the video                    |
| bounding_boxes         | The coordinates of the object's bounding boxes (collected at 1fps)                              |
| initial_tracking_box   | One-hot vector indicating which box annotation should be used to start tracking |
| frame_ids              | The IDs of the frames that are annotated                                  |
| timestamps             | The timestamps of the annotated frames in ms                             |
| is_masked              | Whether the object is masked in the annotated frame                       |

**Point tracks**

| Field Name       | Description                                       |
|------------------|---------------------------------------------------|
| task_id          | A unique annotation ID for each point track       |
| label            | The label of the point track                      |
| parent_objects   | The track_id of the object that the point belongs to |
| frame_ids        | The IDs of the frames that are annotated          |
| points           | The coordinates of the points (collected at 30fps)                      |

**Action segments**

| Field Name        | Description                                      |
|-------------------|--------------------------------------------------|
| task_id           | A unique annotation ID for each action segment   |
| label             | The templated class of the action segment        |
| parent_objects    | The task_ids of the objects involved in the action |
| timestamps        | The start and end timestamps of the action segment |
| frame_ids         | The start and end frame IDs of the action segment |
| label_id          | A unique class ID for each label in the dataset  |


**Sound segments**

| Field Name        | Description                                      |
|-------------------|--------------------------------------------------|
| id                | A unique annotation ID for each sound segment    |
| label             | The name or class of the sound segment           |
| parent_objects    | The object task_ids related to this sound segment |
| timestamps        | The start and end timestamps of the sound segment |
| frame_ids         | The start and end frame IDs of the sound segment  |
| is_visible        | Whether the objects causing the sound in this segment are visible or not |
| label_id          | A unique class ID for each label in the dataset  |


**Multiple-choice video question-answers**

| Field Name       | Description                                             |
|------------------|---------------------------------------------------------|
| task_id          | A unique annotation ID for each question                |
| question         | The text of the question                                |
| options          | The 3 possible options for the question, only 1 is correct                   |
| answer_id        | The ID of the correct option for the question           |
| area             | The skill area the question pertains to                 |
| reasoning        | The type of reasoning required to answer the question   |
| tags              | Different skills involved in answering the given question |


**Grounded video question-answers**

| Field Name       | Description                                             |
|------------------|---------------------------------------------------------|
| task_id          | A unique annotation ID for each question                |
| question         | The text of the question                                |
| answers          | The answer for the question given as a list of object track_ids (corresponding to object tracks) |
| area             | The skill area the question pertains to                 |
| reasoning        | The type of reasoning required to answer the question   |

## Feedback and support

If you have any questions, feedback, or require support regarding the Perception Test dataset or challenge, please contact us at **perception-test@google.com**.

## Citing this work

```
@misc{patraucean2023perception,
      title={Perception Test: A Diagnostic Benchmark for Multimodal Video Models}, 
      author={Viorica Pătrăucean and Lucas Smaira and Ankush Gupta and Adrià Recasens Continente and Larisa Markeeva and Dylan Banarse and Skanda Koppula and Joseph Heyward and Mateusz Malinowski and Yi Yang and Carl Doersch and Tatiana Matejovicova and Yury Sulsky and Antoine Miech and Alex Frechette and Hanna Klimczak and Raphael Koster and Junlin Zhang and Stephanie Winkler and Yusuf Aytar and Simon Osindero and Dima Damen and Andrew Zisserman and João Carreira},
      year={2023},
      eprint={2305.13786},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```
## License and disclaimer

Copyright 2022 DeepMind Technologies Limited

All software is licensed under the Apache License, Version 2.0 (Apache 2.0);
you may not use this file except in compliance with the Apache 2.0 license.
You may obtain a copy of the Apache 2.0 license at:
https://www.apache.org/licenses/LICENSE-2.0

All other materials are licensed under the Creative Commons Attribution 4.0
International License (CC-BY). You may obtain a copy of the CC-BY license at:
https://creativecommons.org/licenses/by/4.0/legalcode

Unless required by applicable law or agreed to in writing, all software and
materials distributed here under the Apache 2.0 or CC-BY licenses are
distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
either express or implied. See the licenses for the specific language governing
permissions and limitations under those licenses.

This is not an official Google product.
