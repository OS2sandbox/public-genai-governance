# Baggrund: Objekt for os2AI

_Formålet med dette skriv er at sætte en ramme for en diskussion hvad vi i os2AI fællesskabet mener når vi snakker om
"AI assistenter"/"AI specialister"/"AI løsninger", som vi gerne vil have at det produkt "os2AI", som vi i fællesskabet
udvikler skal understøtte_

Dette er også tænkt som baggrund for AIStorskala projektets spor 3, hvor der skal sættes minimumskrav til 
_"AI assistenter"_/_"AI specialister"_ (uden at begrebet/objektet er defineret og afgrænset nærmere). Dette skriv er
derfor et forsøg på at sætte en ramme for diskussion af hvordan objektet skal defineres og afgrænses, for derved at 
muliggøre en senere diskussion af minimumskrav til _"AI assistenter"_/_"AI specialister"_/eller-hvad-vi-nu-vil-kalde-det
for at vi meningsfuldt i det offerentlige, særligt kommunale, kan dele disse _"ting"_ med hinanden.

## AI modeller

Centralt i diskussion står at AI løsningen for at kunne kaldes _AI_ et eller andet sted benytter sig af en eller flere 
af de statistiske (maskin lærings-) modeller, der i daglig tale opfattes som _AI_, særligt _Generativ AI_ (vagt 
definineret som noget der _generere_ noget) eller _transformer_ baseret AI. 

> _Transformeren_ er en særlig arkitektur komponent i designet af maskin læringsmodeller, som er meget central i de 
_næsten_ alle moderne tekst genererende modeller (tranformeren bruges dog også i mange andre moderne AI-modeller, der 
ikke på samme måde kan siges at være generative). Transformeren blev defineret i 2018 og ses i udviklingsmiljøet for at 
være kilden til den nuværende AI-hype.

### Oversigt over AI modeller

Min egen top-of-head oversigt over de forskellige typer af moderne (transformer-baseret/generative) AI modeller.

```mermaid
---
config:
  theme: default
  layout: elk
  treemap:
    diagramPadding: 200
    showValues: false
    labelFontSize: 14
---
treemap-beta
"AI modeller - “GenAI”/Transformerbaseret (mostly)/New stuff"
    "Sprogmodeller": 1
    "Oversættelsesmodeller": 1
    "Indlejringsmodeller": 1
    "Tale til tekst modeller": 1
    "Tekst til tale modeller": 1
    "Tekst klassifikationsmodeller": 1
    "Billede-/diffusionsmodeller": 1
    "Syns/sprogmodeller": 1
```

Oversigt fra [huggingfaces klassifikation af modeller](https://huggingface.co/models?sort=trending)

```mermaid
block
  columns 4
  
  block:nlp:2
    columns 2
    nlp_title["Natural Language Processing"]:2

    nlp_tc["Text Classification"]
    nlp_tokc["Token Classification"]
    nlp_tqa["Table Question Answering"]
    nlp_qa["Question Answering"]
    nlp_zsc["Zero-Shot Classification"]
    nlp_trans["Translation"]
    nlp_sum["Summarization"]
    nlp_fe["Feature Extraction"]
    nlp_tg["Text Generation"]
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

    t_["Tabular Classification"]
    t_["Tabular Regression"]
    t_["Time Series Forecasting"]
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
