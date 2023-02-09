# Perception Test

**February 9, 2023**: Recordings from the Computer Perception workshop at ECCV 2022 where we introduced the Perception Test benchmark are available on the [workshop page](https://computerperception.github.io/). Slides presenting the Perception Test and the available tasks are available [here](https://github.com/ComputerPerception/computerperception.github.io/blob/main/CoPe%20workshop%20ECCV2022.pdf)

[Perception Test: A Diagnostic Benchmark for
Multimodal Models](https://storage.googleapis.com/dm-perception-test/perception_test_report.pdf) is a multimodal benchmark that aims to comprehensively
evaluate perception and reasoning skills of multimodal models. The Perception Test dataset introduces real-world
videos designed to show perceptually interesting situations and defines multiple tasks that require
understanding of memory, abstract patterns, physics, and semantics – across visual, audio, and text
modalities. 

[![Example of tracked objects](https://img.youtube.com/vi/XJP1QFOsF-4/hqdefault.jpg)](https://youtu.be/XJP1QFOsF-4)

[GoogleForm-quiz to try the Perception Test yourself](https://docs.google.com/forms/d/e/1FAIpQLScp49reYMAByszH6vo_y6umlkBPwsua2-kMpGjff3IV0YzYkw/viewform?usp=sf_link)

[Playlist of more example videos in the Perception Test](https://youtube.com/playlist?list=PLbMStx8-UPhbaKViNMF8ZcQpyzVhwJC3R)

The dataset consists of 11.6k videos (with audio), of 23s average length, and filmed by
around 100 participants worldwide. The videos are annotated with six types of labels: object and point
tracks, temporal action and sound segments, multiple-choice video question-answers and grounded
video question-answers; see above example of annotations for object tracking.

The dataset probes pre-trained models for their *transfer capabilities*, in
either zero-shot or fine-tuning regime.

This repo contains a Colab that demonstrates how to access, parse and visualise the training and test splits of the datasets. The [gsutil](https://cloud.google.com/storage/docs/gsutil) tool can be used to browse and download the datasets (currently requiring Google account authentication). For example, list the directories with ```gsutil ls gs://dm-perception-test/tfrecords/v1``` and download the `base_oss` dataset with ```gsutil cp -r gs://dm-perception-test/tfrecords/v1/base_oss .```. A held-out test split will be available through an evaluation server. 

We hope this will inspire and contribute to progress towards more general perception models. If you have any comments, suggestions, concerns about the dataset, please contact us at perception-test at google dot com

[![Open Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/deepmind/perception_test/blob/main/inspect_data.ipynb)


## Citing this work

```
@techreport{perceptiontestv1,
     title = {{Perception Test: A Diagnostic Benchmark for Multimodal Models}},
     author = {Viorica Pătrăucean and Lucas Smaira and Ankush Gupta and Adrià Recasens Continente and Larisa Markeeva and Dylan Banarse and Mateusz Malinowski and Yi Yang and Carl Doersch and Tatiana Matejovicova and Yury Sulsky and AntoineMiech and Skanda Koppula and Alex Frechette and Hanna Klimczak and Raphael Koster and Junlin Zhang and StephanieWinkler and Yusuf Aytar and Simon Osindero and Dima Damen and Andrew Zisserman and João Carreira},
     year = {2022},
     institution = {DeepMind},
     month = {10},
     Date-Added = {2022-10-12}
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
