# Perception Test: A Diagnostic Benchmark for Multimodal Video Models

# News
The Third Perception Test Challenge will be organised as an ICCV2025 workshop! More information coming soon!

<!--Please see the website here for more details and links to eval.ai challenge pages: [ptchallenge-workshop.github.io](https://ptchallenge-workshop.github.io/).-->


# Overview
|  |  |
|-----|----|
|Quickstart visualisation notebook | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://github.com/deepmind/perception_test/blob/main/data_visualisation.ipynb) |
| Dataset Explorer          | [Dataset Explorer](https://ptchallenge-workshop.github.io/explore.html)      |
| Download data            | [Download section here](https://github.com/deepmind/perception_test#download-the-data-and-annotations)      |
| Evaluation scripts (including data loader, dummy baseline, evaluation metrics)               | [multiple-choice video QA](https://github.com/deepmind/perception_test/blob/main/baselines/mc_vqa.ipynb), [object tracking](https://github.com/deepmind/perception_test/blob/main/baselines/single_object_tracking.ipynb), [action localisation](https://github.com/deepmind/perception_test/blob/main/baselines/temporal_action_localisation.ipynb), [point tracking](https://github.com/deepmind/perception_test/blob/main/baselines/single_point_tracking.ipynb), [sound localisation](https://github.com/deepmind/perception_test/blob/main/baselines/temporal_sound_localisation.ipynb), [grounded video QA](https://github.com/deepmind/perception_test/blob/main/baselines/grounded_vqa.ipynb)   |
|   Challenges and evaluation servers     | [multiple-choice video QA](https://eval.ai/web/challenges/challenge-page/2091/overview), [object tracking](https://eval.ai/web/challenges/challenge-page/2094/overview), [action localisation](https://eval.ai/web/challenges/challenge-page/2101/overview), [point tracking](https://eval.ai/web/challenges/challenge-page/2108/overview), [sound localisation](https://eval.ai/web/challenges/challenge-page/2109/overview), [grounded video QA](https://eval.ai/web/challenges/challenge-page/2110/overview)



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

# Download the data and annotations

The Perception Test dataset can be downloaded as zip files containing:
* annotations in JSON format
* videos (including audio) as MP4 files
* audio-only files in WAV format
* pre-computed features for the action localisation and sound localisation tasks.

## Full Dataset Splits

| Task                      | Split  | Videos | Audio  | Labels |
|---------------------------|--------|--------|--------|-------|
| Sample                    | All    |  [sample_videos.zip (214.9MB)](https://storage.googleapis.com/dm-perception-test/zip_data/sample_videos.zip)     |  [sample_audios.zip (83.9MB)](https://storage.googleapis.com/dm-perception-test/zip_data/sample_audios.zip)     |  [sample_annotations.zip (3MB)](https://storage.googleapis.com/dm-perception-test/zip_data/sample_annotations.zip)    |
| All Tasks                 | Train  |  [train_videos.zip (26.5GB)](https://storage.googleapis.com/dm-perception-test/zip_data/train_videos.zip)      |  [train_audios.zip (12.3GB)](https://storage.googleapis.com/dm-perception-test/zip_data/train_audios.zip)      |  [train_annotations.zip (30.6MB)](https://storage.googleapis.com/dm-perception-test/zip_data/train_annotations.zip)   |
| All Tasks                 | Valid  |  [valid_videos.zip (70.2GB)](https://storage.googleapis.com/dm-perception-test/zip_data/valid_videos.zip)      |  [valid_audios.zip (33.1GB)](https://storage.googleapis.com/dm-perception-test/zip_data/valid_audios.zip)      |  [valid_annotations.zip (81.5MB)](https://storage.googleapis.com/dm-perception-test/zip_data/valid_annotations.zip)    |
| All Tasks                 | Test  |  [test_videos.zip (41.8GB)](https://storage.googleapis.com/dm-perception-test/zip_data/test_videos.zip)      |  [test_audios.zip (19.3GB)](https://storage.googleapis.com/dm-perception-test/zip_data/test_audios.zip)      |  [test_annotations.zip (633.9kB)](https://storage.googleapis.com/dm-perception-test/zip_data/test_annotations.zip)    |

*In test videos where the end of the video gives away the answer to some questions (e.g. in cup-games, where is the hidden object at the end), we cut the end of the video. For the validation and train splits, we provide the frame id where the cut should be made: [cut_frame_mapping_train.json](https://storage.googleapis.com/dm-perception-test/misc/cut_frame_mapping_train.json), [cut_frame_mapping_valid.json](https://storage.googleapis.com/dm-perception-test/misc/cut_frame_mapping_valid.json). 


## Challenge Downloads

**Video IDs**\
Since some of the challenges use subsets of the benchmark, we provide here the lists of video IDs for each challenge. These should be used to filter the videos/audios/annotations from the full splits above. 
For single object tracking, single point tracking, and grounded video QA we provide separate zip files since the subsets are much smaller than the full dataset.

| Computational Task         | Challenge Train Video IDs | Challenge Valid Video IDs                                     | Challenge Test Video IDs                                      |
|---------------------------|---------------------------|--------------------------------------------------------------|---------------------------------------------------------------|
| Single Object Tracking    | [object_tracking_train_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/object_tracking_train_id_list.csv) | [object_tracking_valid_subset_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/object_tracking_valid_subset_id_list.csv) | [object_tracking_test_subset_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/object_tracking_test_subset_id_list.csv) |
| Single Point Tracking     | [point_tracking_train_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/point_tracking_train_id_list.csv) | [point_tracking_valid_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/point_tracking_valid_id_list.csv) | [point_tracking_test_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/point_tracking_test_id_list.csv) |
| Temporal Action Localisation | [action_localisation_train_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/action_localisation_train_id_list.csv) | [localisation_challenge_valid_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/localisation_challenge_valid_id_list.csv) | [localisation_challenge_test_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/localisation_challenge_test_id_list.csv) |
| Temporal Sound Localisation  | [sound_localisation_train_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/sound_localisation_train_id_list.csv) | [localisation_challenge_valid_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/localisation_challenge_valid_id_list.csv) | [localisation_challenge_test_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/localisation_challenge_test_id_list.csv) |
| Multiple-Choice Video QA  | [mc_question_train_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/mc_question_train_id_list.csv) | [mc_question_valid_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/mc_question_valid_id_list.csv) | [mc_question_test_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/mc_question_test_id_list.csv) |
| Grounded Video QA        | [grounded_question_train_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/grounded_question_train_id_list.csv) | [grounded_question_valid_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/grounded_question_valid_id_list.csv) | [grounded_question_test_id_list.csv](https://storage.googleapis.com/dm-perception-test/misc/grounded_question_test_id_list.csv) |





**Single Object Tracking**
<!--Challenge link: [https://eval.ai/web/challenges/challenge-page/2094/overview](https://eval.ai/web/challenges/challenge-page/2094/overview)-->

| Task                      | Split  | Videos | Audio  | Labels |
|---------------------------|--------|--------|--------|-------|
| Single Object Tracking     | Train  | Use full split download above  |  N/A   |  Use full split download above   |
| Single Object Tracking     | Valid  |  [sot_valid_videos_challenge2023.zip (11.6GB)](https://storage.googleapis.com/dm-perception-test/zip_data/sot_valid_videos_challenge2023.zip)      |  N/A    |  [sot_valid_annotations_challenge2023.zip (9MB)](https://storage.googleapis.com/dm-perception-test/zip_data/sot_valid_annotations_challenge2023.zip)    |
| Single Object Tracking     | Test  |  [sot_test_videos_challenge2023.zip (12.1GB)](https://storage.googleapis.com/dm-perception-test/zip_data/sot_test_videos_challenge2023.zip)      |  N/A    |  [sot_test_annotations_challenge2023.zip (613kB)](https://storage.googleapis.com/dm-perception-test/zip_data/sot_test_annotations_challenge2023.zip)    |


**Single Point Tracking**
<!--Challenge link: [https://eval.ai/web/challenges/challenge-page/2108/overview](https://eval.ai/web/challenges/challenge-page/2108/overview)-->

| Task                      | Split  | Videos | Audio  | Labels |
|---------------------------|--------|--------|--------|-------|
| Single Point Tracking     | Train  | [point_tracking_train_videos.zip (398.4MB)](https://storage.googleapis.com/dm-perception-test/zip_data/point_tracking_train_videos.zip)    |  N/A   | [point_tracking_train_annotations.zip (4.7MB)](https://storage.googleapis.com/dm-perception-test/zip_data/point_tracking_train_annotations.zip)    |
| Single Point Tracking     | Valid  |  [point_tracking_valid_videos.zip (1.1GB)](https://storage.googleapis.com/dm-perception-test/zip_data/point_tracking_valid_videos.zip)    |  N/A   | [point_tracking_valid_annotations.zip (11.1MB)](https://storage.googleapis.com/dm-perception-test/zip_data/point_tracking_valid_annotations.zip)    |
| Single Point Tracking     | Test  |  [point_tracking_test_videos.zip (691MB)](https://storage.googleapis.com/dm-perception-test/zip_data/point_tracking_test_videos.zip)    |  N/A   | [point_tracking_test_annotations.zip (42.2kB)](https://storage.googleapis.com/dm-perception-test/zip_data/point_tracking_test_annotations.zip)    |


**Temporal Action Localisation**
<!--Challenge link: [https://eval.ai/web/challenges/challenge-page/2101/overview](https://eval.ai/web/challenges/challenge-page/2101/overview)-->

| Task                      | Split  | Videos | Audio  | Labels | Video Features (TSP) | 
|---------------------------|--------|--------|--------|-------|----------|
| Temporal Action Localisation          | Train  |  Use full split download above   | Use full split download above |  [action_localisation_train_annotations.zip (217kB)](https://storage.googleapis.com/dm-perception-test/zip_data/action_localisation_train_annotations.zip)   | [action_localisation_train_video_features.zip (81.7MB)](https://storage.googleapis.com/dm-perception-test/zip_data/action_localisation_train_video_features.zip)    |
| Temporal Action Localisation          | Valid   |  Use full split download above   | Use full split download above |  [challenge_action_localisation_valid_annotations.zip (558kB)](https://storage.googleapis.com/dm-perception-test/zip_data/challenge_action_localisation_valid_annotations.zip)   | [action_localisation_valid_video_features.zip (219.2MB)](https://storage.googleapis.com/dm-perception-test/zip_data/action_localisation_valid_video_features.zip)     |
| Temporal Action Localisation          | Test   |  Use full split download above   | Use full split download above | N/A | [action_localisation_test_video_features.zip (131.7MB)](https://storage.googleapis.com/dm-perception-test/zip_data/action_localisation_test_video_features.zip)     |



**Temporal Sound Localisation**
<!--Challenge link: [https://eval.ai/web/challenges/challenge-page/2109/overview](https://eval.ai/web/challenges/challenge-page/2109/overview)-->

| Task                      | Split  | Videos | Audio  | Labels | Audio Features (MMV) | 
|---------------------------|--------|--------|--------|-------|----------|
| Temporal Sound Localisation          | Train  |  Use full split download above   | Use full split download above |  [sound_localisation_train_annotations.zip (363kB)](https://storage.googleapis.com/dm-perception-test/zip_data/sound_localisation_train_annotations.zip)   | [sound_localisation_train_audio_features.zip (109.1MB)](https://storage.googleapis.com/dm-perception-test/zip_data/sound_localisation_train_audio_features.zip)    |
| Temporal Sound Localisation          | Valid   |  Use full split download above   | Use full split download above |  [challenge_sound_localisation_valid_annotations.zip (552kB)](https://storage.googleapis.com/dm-perception-test/zip_data/challenge_sound_localisation_valid_annotations.zip)   | [sound_localisation_valid_audio_features.zip (291.4MB)](https://storage.googleapis.com/dm-perception-test/zip_data/sound_localisation_valid_audio_features.zip)     |
| Temporal Sound Localisation          | Test   |  Use full split download above   | Use full split download above | N/A | [sound_localisation_test_video_features.zip (177.2MB)](https://storage.googleapis.com/dm-perception-test/zip_data/sound_localisation_test_audio_features.zip)     |


**Multiple-Choice Video QA**
<!--Challenge link: [https://eval.ai/web/challenges/challenge-page/2091/overview](https://eval.ai/web/challenges/challenge-page/2091/overview)-->

| Task                      | Split  | Videos | Audio  | Labels |
|---------------------------|--------|--------|--------|-------|
| Multiple-Choice Video QA          | Train  |  Use full split download above   | Use full split download above |  [mc_question_train_annotations.zip (85kB)](https://storage.googleapis.com/dm-perception-test/zip_data/mc_question_train_annotations.zip), [cut_frame_mapping_train.json](https://storage.googleapis.com/dm-perception-test/misc/cut_frame_mapping_train.json)  |
| Multiple-Choice Video QA          | Valid   |  Use full split download above   | Use full split download above |  [mc_question_valid_annotations.zip (200kB)](https://storage.googleapis.com/dm-perception-test/zip_data/mc_question_valid_annotations.zip), [cut_frame_mapping_valid.json](https://storage.googleapis.com/dm-perception-test/misc/cut_frame_mapping_valid.json)    |
| Multiple-Choice Video QA          | Test   |  Use full split download above   | Use full split download above |  [mc_question_test_annotations.zip (200kB)](https://storage.googleapis.com/dm-perception-test/zip_data/mc_question_test_annotations.zip)   |

**Grounded Video QA**
<!--Challenge link: [https://eval.ai/web/challenges/challenge-page/2110/overview](https://eval.ai/web/challenges/challenge-page/2110/overview)-->

| Task                      | Split  | Videos | Audio  | Labels |
|---------------------------|--------|--------|--------|-------|
| Grounded Video QA         | Train  | [grounded_question_train_videos.zip (7.3GB)](https://storage.googleapis.com/dm-perception-test/zip_data/grounded_question_train_videos.zip) | [grounded_question_train_audios.zip (3.4GB)](https://storage.googleapis.com/dm-perception-test/zip_data/grounded_question_train_audios.zip) | [grounded_question_train_annotations.zip (6.1MB)](https://storage.googleapis.com/dm-perception-test/zip_data/grounded_question_train_annotations.zip)   |
| Grounded Video QA         | Valid  | [grounded_question_valid_videos.zip (19.3GB)](https://storage.googleapis.com/dm-perception-test/zip_data/grounded_question_valid_videos.zip) | [grounded_question_valid_audios.zip (9.1GB)](https://storage.googleapis.com/dm-perception-test/zip_data/grounded_question_valid_audios.zip) | [grounded_question_valid_annotations.zip (16.8MB)](https://storage.googleapis.com/dm-perception-test/zip_data/grounded_question_valid_annotations.zip)   |
| Grounded Video QA         | Test  | [grounded_question_test_videos.zip (11.3GB)](https://storage.googleapis.com/dm-perception-test/zip_data/grounded_question_test_videos.zip) | | [grounded_question_test_annotations.zip (17.5kB)](https://storage.googleapis.com/dm-perception-test/zip_data/grounded_question_test_annotations.zip)   |



## Baselines
In this repo we provide dummy baselines to demonstrate how to load the data, evaluate and recreate some baseline results from the paper. For the other results in the baselines section in the paper, we will be adding another external repo.

| Computational task         | Baseline                                                           | Description |
|---------------------------|-------------------------------------------------------------------|-------------|
| Single Object Tracking    | [Static](https://github.com/deepmind/perception_test/blob/main/baselines/single_object_tracking.ipynb) | Static object baseline. |
| Single Point Tracking     | [Static](https://github.com/deepmind/perception_test/blob/main/baselines/single_point_tracking.ipynb) | Static point baseline. |
| Temporal Action Localisation | [ActionFormer](https://github.com/deepmind/perception_test/blob/main/baselines/temporal_action_localisation.ipynb) | [ActionFormer model](https://github.com/ptchallenge-workshop/actionformer_release_PT) fine-tuned on Perception Test data. |
| Temporal Sound Localisation  | [ActionFormer](https://github.com/deepmind/perception_test/blob/main/baselines/temporal_sound_localisation.ipynb) | [ActionFormer model](https://github.com/ptchallenge-workshop/actionformer_release_PT) fine-tuned on Perception Test data. |
| Multiple-Choice Video QA   | [Frequency](https://github.com/deepmind/perception_test/blob/main/baselines/mc_vqa.ipynb)           | Frequency baseline using training question/answer pairs. More details are provided in the paper. |
| Grounded Video QA        | [MDETR + static](https://github.com/deepmind/perception_test/blob/main/baselines/grounded_vqa.ipynb)       | [MDETR](https://github.com/facebookresearch/multimodal/tree/main) open-vocabulary object detections kept static throughout the video. |



## Metrics

<!-- The [metrics file](https://link) contains the metric code to evaluate the performance for the different tasks. -->

| Computational task       |Metric |
|--------------------------|------------------|
| Single Object Tracking            |            Average IoU  |
| Single Point Tracking             |              [Average Jaccard](https://arxiv.org/pdf/2211.03726.pdf) |
| Temporal Action Localisation          |           Mean Average Precision |            
| Temporal Sound Localisation           |           Mean Average Precision |            
| Multiple-Choice Video QA         |           Top-1 Accuracy|
| Grounded Video QA             |            [HOTA](https://arxiv.org/pdf/2009.07736.pdf)   |

Metrics code to evaluate performance for the different tasks coming soon.

## Perception Test annotations

**Explore the annotations**: [data_visualisation.ipynb](https://github.com/deepmind/perception_test/blob/main/data_visualisation.ipynb)

**Summary**

| Annotation type          | Number of videos | Number of annotations |
|--------------------------|------------------|-----------------------|
| Object tracks            |           11,609 |      189,940   |
| Point tracks             |              145 |      8,647   |
| Action segments          |           11,353 |      73,503  |
| Sound segments           |           11,433 |      137,128 |
| Multiple-choice Questions|           10,361 |      38,060  |
| Grounded video Questions |            3,063 |      6,086   |

**Video metadata**


| Field Name         | Description                                                      |
|--------------------|------------------------------------------------------------------|
| split              | The data split the video belongs to, one of ['train','valid','test']. |
| video_id           | The ID of the video ['video_xxxx'].                              |
| frame_rate         | The frame rate of the video in frames per second.                |
| num_frames         | The total number of frames in the video.                          |
| resolution         | The height and width of the video in pixels.                      |
| audio_samples      | The total number of audio samples in the video.                   |
| audio_sample_rate  | The sample rate of the audio in the video in Hz.                  |
| is_cup_game        | Whether the video shows a cups-game or not, see paper for details.|
| is_camera_moving   | Whether the camera used to film the video is moving or not.       |



**Object tracks**

| Field Name             | Description                                                                        |
|------------------------|------------------------------------------------------------------------------------|
| id                     | A unique annotation ID for each object track                                         |
| label                  | The name of the object, can also contain object attributes, e.g. red box.           |
| is_occluder            | Whether the object occludes other objects in the video (This is valid only for the cups-games videos). |
| bounding_boxes         | The coordinates of the object's bounding box in the format [x1,y1,x2,y2] shape [n,4] where n is the number of annotated frames. |
| initial_tracking_box   | one-hot vector indicating which box annotation should be used to start the tracking for this object [n]. |
| frame_ids              | The IDs of the frames that are annotated, normally 1 per second, e.g. 0, 30, 60, etc. shape [n]. |
| timestamps             | The timestamps of the annotated frames in &mu;s. Shape [n].                             |
| is_masked              | Whether the object is masked in the annotated frame, corresponds to the bounding boxes [n] ( This is valid only for the cups-games videos). |


**Point tracks**

| Field Name         | Description                                           |
|--------------------|-------------------------------------------------------|
| id                 | A unique annotation ID for each point track.            |
| label              | The label of the point track.                           |
| parent_objects     | The id of the object that the point belongs to.         |
| frame_ids          | The IDs of the frames that are annotated, normally 0, 1, 2 etc. shape [N], where N is the total number of points in the track. |
| points             | The coordinates of the points in [y,x], shape [N, 2]. |

**Action segments**

| Field Name         | Description                                                          |
|--------------------|----------------------------------------------------------------------|
| id                 | A unique annotation ID for each action segment.                       |
| label              | The templated class of the action segment, e.g. Putting something into something. |
| parent_objects     | The ids of the objects involved in the action, can be empty, single, multiple or -1 for an object not annotated. |
| timestamps         | The start and end timestamps of the action segment in &mu;s [start time, end time]. |
| frame_ids          | The start and end frame IDs of the action segment [start frame, end frame]. |
| label_id           | A unique class ID for each label in the dataset.                      |



**Sound segments**

| Field Name         | Description                                                              |
|--------------------|--------------------------------------------------------------------------|
| id                 | A unique annotation ID for each sound segment.                             |
| label              | The name or class of the sound segment.                                    |
| parent_objects     | The object ids related to this sound segment, can be empty, single, multiple or -1 for an object not annotated. |
| timestamps         | The start and end timestamps of the sound segment in &mu;s [start time, end time]. |
| frame_ids          | The start and end frame IDs of the sound segment [start frame, end frame]. |
| is_visible         | Whether the objects causing the sound in this segment are visible or not, e.g. if an object falls off the table and the impact point with the floor is occluded, then is_visible=False. |
| label_id           | A unique class ID for each label in the dataset.                            |



**Multiple-choice video question-answers**

| Field Name         | Description                                                      |
|--------------------|------------------------------------------------------------------|
| id                 | A unique annotation ID for each question.                         |
| question           | The text of the question.                                         |
| options            | The possible options for the question. There are 3 possible options, and only one is correct. |
| answer_id          | The ID of the correct option for the question.                    |
| area               | The skill area the question pertains to. Can be Memory, Abstraction, Physics, Semantics. |
| reasoning          | The type of reasoning required to answer the question. Can be Descriptive, Explanatory, Predictive, or Counterfactual. |
| tag                | Different skills involved in answering the given question. A question can have multiple skill tags. |



**Grounded video question-answers**

| Field Name         | Description                                                      |
|--------------------|------------------------------------------------------------------|
| id                 | A unique annotation ID for each question.                         |
| question           | The text of the question.                                         |
| answers            | The answer for the question given as a list of IDs, these relate to single object tracking annotation IDs, specifically the 'id' field for a given object in the same video.        |
| area               | The skill area the question pertains to. Can be Memory, Abstraction, Physics, Semantics. |
| reasoning          | The type of reasoning required to answer the question. Can be Descriptive, Explanatory, Predictive, or Counterfactual. |


## Feedback and support

If you have any questions, feedback, or require support regarding the Perception Test dataset or challenge, please contact us at **perception-test@google.com**.

## Citing this work

```
@inproceedings{patraucean2023perception,
      title={Perception Test: A Diagnostic Benchmark for Multimodal Video Models}, 
      author={Viorica Pătrăucean and Lucas Smaira and Ankush Gupta and Adrià Recasens Continente and Larisa Markeeva and Dylan Banarse and Skanda Koppula and Joseph Heyward and Mateusz Malinowski and Yi Yang and Carl Doersch and Tatiana Matejovicova and Yury Sulsky and Antoine Miech and Alex Frechette and Hanna Klimczak and Raphael Koster and Junlin Zhang and Stephanie Winkler and Yusuf Aytar and Simon Osindero and Dima Damen and Andrew Zisserman and João Carreira},
      booktitle={Advances in Neural Information Processing Systems},
      year={2023},
      url={https://openreview.net/forum?id=HYEGXFnPoq}
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
