# Klassifikation af AI Modeller

Oversigt fra [huggingfaces klassifikation af modeller](https://huggingface.co/models?sort=trending)

#TODO: Add explanation to most significant models classes (and reorder so to have most important first)

```mermaid
block
  columns 4
  
  block:nlp:2
    columns 2
    nlp_title["Natural Language Processing"]:2

    nlp_tg["Text Generation"]
    nlp_tc["Text Classification"]
    nlp_tokc["Token Classification"]
    nlp_tqa["Table Question Answering"]
    nlp_qa["Question Answering"]
    nlp_zsc["Zero-Shot Classification"]
    nlp_trans["Translation"]
    nlp_sum["Summarization"]
    nlp_fe["Feature Extraction"]
    nlp_fm["Fill-Mask"]
    nlp_ss["Sentence Similarity"]
    nlp_tr["Text Ranking"]
  end
  
  block:mm:2
    columns 2
    mm_title["Multimodel"]:2

    mm_attt["Audio-text-to-text"] 
    mm_ittt["Image-Text-to-Text"]
    mm_itti["Image-Text-to-Image"]
    mm_ittv["Image-Text-to-Video"]
    mm_vqa["Visual Question Answering"]
    mm_dqa["Document Question Answering"]
    mm_vttt["Video-Text-to-Text"]
    mm_vdr["Visual Document Retrieval"]
    mm_ata["Any-to-Any"]
  end

  block:cv:2
    columns 2
    cv_title["Computer Vision"]:2
    
    cv_de["Depth Estimation"]
    cv_ic["Image Classification"]
    cv_od["Object Detection"]
    cv_is["Image Segmentation"]
    cv_tti["Text-to-Image"]
    cv_itt["Image-to-Text"]
    cv_iti["Image-to-Image"]
    cv_itv["Image-to-Video"]
    cv_uig["Unconditional Image Generation"]
    cv_vc["Video Classification"]
    cv_ttv["Text-to-Video"]
    cv_zsic["Zero-Shot Image Classification"]
    cv_mg["Mask Generation"]
    cv_zsod["Zero-Shot Object Detection"]
    cv_tt3d["Text-to-3D"]
    cv_it3d["Image-to-3D"]
    cv_ife["Image Feature Extraction"]
    cv_kd["Keypoint Detection"]
    cv_vtc["Video-to-Video"]
  end
  
  block:a:2
    columns 2
    a_title["Audio"]:2

    a_tts["Text-to-Speech"]
    a_tta["Text-to-Audio"]
    a_asr["Automatic Speech Recognition"]
    a_ata["Audio-to-Audio"]
    a_ac["Audio Classification"]
    a_vad["Voice Activity Detection"]
  end
  
  block:t:2
    columns 2
    t_title["Tabular"]:2

    t_tc["Tabular Classification"]
    t_tr["Tabular Regression"]
    t_tsf["Time Series Forecasting"]
  end

  block:rl:2
    columns 2
    rl_title["Reinforcement Learning"]:2

    rl_rl["Reinforcement Learning"]
    rl_r["Robotics"]
  end

  block:o:2
    columns 2
    o_title["Other"]:2
    
    o_gml["Graph Machine Learning"]
  end
  
  classDef title fill:none, stroke-width:0px
  
  class mm_title title
  class cv_title title
  class nlp_title title
  class a_title title
  class t_title title
  class rl_title title
  class o_title title
```


```mermaid
block
  columns 5
  
  block:nlp:2
    columns 2
    nlp_title["Natural Language Processing"]:2

    nlp_tg["Text Generation"]
    nlp_tc["Text Classification"]
    nlp_tokc["Token Classification"]
    nlp_tqa["Table Question Answering"]
    nlp_qa["Question Answering"]
    nlp_zsc["Zero-Shot Classification"]
    nlp_trans["Translation"]
    nlp_sum["Summarization"]
    nlp_fe["Feature Extraction"]
    nlp_fm["Fill-Mask"]
    nlp_ss["Sentence Similarity"]
    nlp_tr["Text Ranking"]
  end
  
  block:a:1
    columns 1
    a_title["Audio"]

    a_tts["Text-to-Speech"]
    a_tta["Text-to-Audio"]
    a_asr["Automatic Speech Recognition"]
    a_ata["Audio-to-Audio"]
    a_ac["Audio Classification"]
    a_vad["Voice Activity Detection"]
  end
  
  block:mm:2
    columns 2
    mm_title["Multimodel"]:2

    mm_attt["Audio-text-to-text"] 
    mm_ittt["Image-Text-to-Text"]
    mm_itti["Image-Text-to-Image"]
    mm_ittv["Image-Text-to-Video"]
    mm_vqa["Visual Question Answering"]
    mm_dqa["Document Question Answering"]
    mm_vttt["Video-Text-to-Text"]
    mm_vdr["Visual Document Retrieval"]
    mm_ata["Any-to-Any"]
  end
  
  block:cv:2
    columns 2
    cv_title["Computer Vision"]:2
    
    cv_de["Depth Estimation"]
    cv_ic["Image Classification"]
    cv_od["Object Detection"]
    cv_is["Image Segmentation"]
    cv_tti["Text-to-Image"]
    cv_itt["Image-to-Text"]
    cv_iti["Image-to-Image"]
    cv_itv["Image-to-Video"]
    cv_uig["Unconditional Image Generation"]
    cv_vc["Video Classification"]
    cv_ttv["Text-to-Video"]
    cv_zsic["Zero-Shot Image Classification"]
    cv_mg["Mask Generation"]
    cv_zsod["Zero-Shot Object Detection"]
    cv_tt3d["Text-to-3D"]
    cv_it3d["Image-to-3D"]
    cv_ife["Image Feature Extraction"]
    cv_kd["Keypoint Detection"]
    cv_vtc["Video-to-Video"]
  end
  
  block:t:1
    columns 1
    t_title["Tabular"]

    t_tc["Tabular Classification"]
    t_tr["Tabular Regression"]
    t_tsf["Time Series Forecasting"]
  end

  block:rl:1
    columns 1
    rl_title["Reinforcement Learning"]

    rl_rl["Reinforcement Learning"]
    rl_r["Robotics"]
  end

  block:o:1
    columns 1
    o_title["Other"]
    
    o_gml["Graph Machine Learning"]
  end
  
  classDef title fill:none, stroke-width:0px
  
  class mm_title title
  class cv_title title
  class nlp_title title
  class a_title title
  class t_title title
  class rl_title title
  class o_title title
```
