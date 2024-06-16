# Parameter-efficient Fine-tuning with LoRA
This repository contains the code and results for Parameter-efficient Fine-tuning with Low Rank Adaptation (LoRA).

## 1. Dataset
The dataset used in this project is "Emotion". The dataset can be downloaded from the following link: https://huggingface.co/datasets/dair-ai/emotion

## 2. Task
The objective of this project is to fine-tune the `GPT-2` model using Parameter-Efficient Fine-Tuning (PEFT) techniques, specifically `Low-Rank Adaptation (LoRA)`. We applied these techniques to adapt the pre-trained GPT-2 model for the task of emotion classification. Using the `Emotions` Dataset, the model is trained to categorize input text into one of six emotion classes: 
- anger
- fear
- joy
- love
- sadness
- surprise

Different values of rank ($r$) has been tested for comparison. 

## 3. Requirements
- Python 3.12.3
- PyTorch 2.3.1
- Transformers 4.41.2
- Huggingface Datasets 2.20.0
- PEFT 0.11.1

## 4. Setup
- $\alpha_{lora} = 0.8$
- Learning Step ($\eta)=0.0005$
- $Epoch=5$
- Drop out rate ($D_{lora})=0.1$
- Weight Decay = 0.01

## 5. Performance
| rank ($r$)  | Trainable Params| Total Params | % Trainable | Accuracy |
|-------------|-----------------|--------------|-------------|----------|
| 1  | 41,472               | 124,486,656      | 0.0333               | 91.45   | 
| 2  | 78,336               | 124,523,520      | 0.0629               | 91.30   | 
| 4  | 152,064              | 124,597,248      | 0.1220               | 91.70   | 
| 8  | 299,520              | 124,744,704      | 0.2401               | 91.50   | 
| 16 | 594,432              | 125,039,616      | 0.4754               | 91.40   |

## 6. Results
| #  | Text | Label | Emotion | Predicted Label | Predicted Emotion |
|----|----------------|-------|---------|-----------------|--------|
| 0  | I feel irritable about the number of people that came into our office whining about their own circumstances. I realize I'm not practicing thinking about the good things and I find it a better way to pull yourself into the present. | 3     | Anger   | 3               | Anger             |
| 1  | I feel appalled right now.| 3     | Anger   | 3               | Anger             |
| 2  | I feel that I am afraid of whatever and anything that will happen and I don't care if it's good or bad. I am just afraid and I hope, God, you will help me in whatever I do.                                          | 4     | Fear    | 4               | Fear              |
| 3  | I guess feelings aren’t meant to be inhibited or prohibited.                                                                                                                                                         | 4     | Fear    | 0               | Sadness           |
| 4  | I bought this Doraemon backpack from a charity store. I had every intention of putting it in my Etsy store but I feel like it's too cute to sell.                                                                    | 1     | Joy     | 1               | Joy               |
| 5  | I feel for this divine landmass and all the respect I bear in my heart for the greatness residing on it.                                                                                                              | 1     | Joy     | 1               | Joy               |
| 6  | I feel that I am supporting the troops by demanding that we not send our young men and women into harm's way to bear arms against a country that has done nothing to threaten us at any point.                         | 2     | Love    | 2               | Love              |
| 7  | I feel very tender for anyone who is upset by the Bee Movie, sort of like how you feel about old aunts who don't realize how prickly their whiskers are getting. Slightly repulsed but very sad for their decline.    | 2     | Love    | 2               | Love              |
| 8  | I came home, waiting for the shower, read something which made me upset. That's why I feel discontent. Haha.                                                                                                          | 0     | Sadness | 3               | Anger             |
| 9  | I'm starting to feel really pathetic, giving the bulk of my enthusiasm these days to the Kardashians, US Weekly, and Roseanne marathons and completely ignoring this blog.                                           | 0     | Sadness | 0               | Sadness           |
| 10 | I wonder if the homeowners would feel weird if I parked to gape at their landscaping.                                                                                                                                | 5     | Surprise| 5               | Surprise          |
| 11 | I feel that's just strange on WOTC's behalf.                                                                                                                                                                         | 5     | Surprise| 5               | Surprise          |




## Acknowledgement
- [LoRA Paper](https://doi.org/10.48550/arXiv.2106.09685)
- [Generative AI](https://www.udacity.com/course/generative-ai--nd608?promo=year_end&coupon=SUMMER&utm_source=gsem_india_brand&utm_medium=ads_r&utm_campaign=21225968073_c_individuals&utm_term=162291064075&utm_keyword=udacity%20generative%20ai_e&utm_source=gsem_brand&utm_medium=ads_r&utm_campaign=21225968073_c_individuals&utm_term=162291064075&utm_keyword=udacity%20generative%20ai_e&gad_source=1&gclid=EAIaIQobChMIm4a7m83ehgMV4tXCBB2y-QaaEAAYASAAEgKAy_D_BwE)