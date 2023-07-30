# Documentation

## 📌 Description

Stable Diffusion XL is a Diffusion-based text-to-image generative model by Stability AI. It is the base model is used to generate (noisy) latents, which can be further processed with a refinement model specialized for the final denoising steps. This service uses the base model only to generate image from text. <a href='https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0' target='_blank'>Learn More</a>.

## 💻 Hardware Requirements

To run the `stable-diffusion-xl` service on Prem, you'll need access to a GPU with at least 16GiB of VRAM.

## 📒 Example Usage

### 1️⃣ Prompt: Iron man portrait, highly detailed, science fiction landscape, art style by klimt and nixeu and ian sprigger and wlop and krenz cushart
![iron_man](https://github.com/premAI-io/prem-registry/assets/35634788/755f6d9e-b13d-4e1a-bc9d-571e1b6e2490)


### 2️⃣ Prompt: Low polygon panda 3d
![panda](https://github.com/premAI-io/prem-registry/assets/35634788/a8ef471b-dbb4-4dde-869d-80fa48d4bd48)


### 3️⃣ Prompt: 3d hiper-realistic rick sanchez and morty
![rick](https://github.com/premAI-io/prem-registry/assets/35634788/b2abbf8d-39e7-4337-8e30-71d3701c4295)



### 4️⃣ Prompt: Synthwave brad pitt wearing headphones, animated, trending on artstation, portrait
![brad_pitt](https://github.com/premAI-io/prem-registry/assets/35634788/d6f80543-9729-4090-82d6-4fea1d9ea608)




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

openai.api_base = "http://localhost:9224/v1"
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
