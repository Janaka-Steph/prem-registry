# Documentation

## 📌 Description

Stable Diffusion v1.5 is a sophisticated text-to-image diffusion model capable of generating high-quality images from textual prompts. Developed by Robin Rombach and Patrick Esser, this model is a significant upgrade from its predecessor, Stable Diffusion v1.2, having been fine-tuned on 595k steps at a resolution of 512x512 on `laion-aesthetics v2 5+` with a 10% drop in text-conditioning to enhance classifier-free guidance sampling. <a href='https://github.com/runwayml/stable-diffusion' target='_blank'>Learn More</a>.

## 💻 Hardware Requirements

To run the `stable-diffusion-xl-with-refiner` service on Prem, you'll need access to a GPU with at least 24GiB of VRAM.

## 📒 Example Usage

### 1️⃣ Prompt: Iron man portrait, highly detailed, science fiction landscape, art style by klimt and nixeu and ian sprigger and wlop and krenz cushart


### 2️⃣ Prompt: Low polygon panda 3d


### 3️⃣ Prompt: 3d hiper-realistic rick sanchez and morty



### 4️⃣ Prompt: Synthwave brad pitt wearing headphones, animated, trending on artstation, portrait




## 🛠️ Technical Details

### 🚀 Getting Started with OpenAI Python client

The service exposes the same `/image/generations` (for Text-to-Image) endpoints as OpenAI DALL-E does. You can directly use the official `openai` python library.

#### Text-to-Image

```python

!pip install openai
!pip install pillow

import io
import base64
import openai

from PIL import Image

openai.api_base = "http://localhost:9225/v1"
openai.api_key = "random-string"

response = openai.Image.create(
    prompt="Iron man portrait, highly detailed, science fiction landscape, art style by klimt and nixeu and ian sprigger and wlop and krenz cushart",
    n=1,
    size="512x512"
)

image_string = response["data"][0]["b64_json"]

img = Image.open(io.BytesIO(base64.decodebytes(bytes(image_string, "utf-8"))))
img.save("iron_man.png", "PNG")

```

> **Note: Currently we only support text-to-image generation.**


## 📜 License

The model is under CreativeML OpenRAIL M license is an Open RAIL M license, adapted from the work that BigScience and the RAIL Initiative are jointly carrying in the area of responsible AI licensing. See also the article about the BLOOM Open RAIL license on which our license is based.
