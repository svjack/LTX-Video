<div align="center">

# LTX-Video

This is the official repository for LTX-Video.

[Website](https://www.lightricks.com/ltxv) |
[Model](https://huggingface.co/Lightricks/LTX-Video) |
[Demo](https://fal.ai/models/fal-ai/ltx-video) |
[Paper (Soon)](https://github.com/Lightricks/LTX-Video) 

</div>

```bash
sudo apt-get update && sudo apt-get install cbm ffmpeg git-lfs
git clone https://huggingface.co/spaces/svjack/LTX-Video-Playground && cd LTX-Video-Playground && pip install -r requirements.txt
export OPENAI_API_KEY=""
python app.py
```

## I2V Reference Images

### Cards
- **IMG_bat_gen.webp**
  <div style="display: flex; flex-direction: column; align-items: center;">
    <img src="IMG_bat_gen.webp" alt="IMG_bat_gen.webp" style="max-width: 100%;">
    <p><strong>Prompt:</strong> A film style shot. On the moon, this item on the moon surface. The background is that Earth looms large in the foreground.</p>
  </div>
- **image_hs_card_gen.webp**
  <div style="display: flex; flex-direction: column; align-items: center;">
    <img src="image_hs_card_gen.webp" alt="image_hs_card_gen.webp" style="max-width: 100%;">
    <p><strong>Prompt:</strong> In a Bauhaus style room, this item is placed on a shiny glass table, with a vase of flowers next to it. In the afternoon sun, the shadows of the blinds are cast on the wall.</p>
  </div>

### Dolls
- **image_hs_doll_gen.webp**
  <div style="display: flex; flex-direction: column; align-items: center;">
    <img src="image_hs_doll_gen.webp" alt="image_hs_doll_gen.webp" style="max-width: 100%;">
    <p><strong>Prompt:</strong> This item, a charming doll, nestles in a plush bed surrounded by colorful pillows in a pastel-colored bedroom. Its velvety fabric feels luxuriously soft, while its downy-stuffed limbs offer a huggable plumpness. A gentle breeze from the open window rustles sheer curtains, casting delicate light patterns on the floor. A small wooden nightstand holds a tiny lamp, casting a warm glow. The room's faint lavender scent and the distant clock's soft hum create a tranquil ambiance.</p>
  </div>


# Use LTX Video I2V to make Genshin Impact product video (https://github.com/svjack/LTX-Video) 

## Bat_card_LTX_Video.mp4
<div style="margin-bottom: 10px;">
  <video controls autoplay src="https://github.com/user-attachments/assets/e74148c9-300a-44cc-9334-49ced6ad9ec4" style="width: 1024px; height: 800px;"></video>
</div>
<p><strong>Prompt:</strong> A film style shot. On the moon, this item on the moon surface. The background is that Earth looms large in the foreground.</p>

## Hs_card_LTX_Video.mp4
<div style="margin-bottom: 10px;">
  <video controls autoplay src="https://github.com/user-attachments/assets/3aa95f1b-2cde-4a16-8b3f-154a3d977faf" style="width: 1024px; height: 800px;"></video>
</div>
<p><strong>Prompt:</strong> In a Bauhaus style room, this item is placed on a shiny glass table, with a vase of flowers next to it. In the afternoon sun, the shadows of the blinds are cast on the wall.</p>

## Hs_doll_LTX_Video.mp4
<div style="margin-bottom: 10px;">
  <video controls autoplay src="https://github.com/user-attachments/assets/74df3a9d-5e01-482c-b1a1-d2ae76296313" style="width: 1024px; height: 800px;"></video>
</div>
<p><strong>Prompt:</strong> This item, a charming doll, nestles in a plush bed surrounded by colorful pillows in a pastel-colored bedroom. Its velvety fabric feels luxuriously soft, while its downy-stuffed limbs offer a huggable plumpness.</p>







<br/><br/>

## Table of Contents

- [Introduction](#introduction)
- [Quick Start Guide](#quick-start-guide)
  - [Online demo](#online-demo)
  - [Run locally](#run-locally)
    - [Installation](#installation)
    - [Inference](#inference)
  - [ComfyUI Integration](#comfyui-integration)
- [Model User Guide](#model-user-guide)
- [Acknowledgement](#acknowledgement)

# Introduction

LTX-Video is the first DiT-based video generation model that can generate high-quality videos in *real-time*.
It can generate 24 FPS videos at 768x512 resolution, faster than it takes to watch them.
The model is trained on a large-scale dataset of diverse videos and can generate high-resolution videos
with realistic and diverse content.

| | | | |
|:---:|:---:|:---:|:---:|
| ![example1](./docs/_static/ltx-video_example_00001.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A woman with long brown hair and light skin smiles at another woman...</summary>A woman with long brown hair and light skin smiles at another woman with long blonde hair. The woman with brown hair wears a black jacket and has a small, barely noticeable mole on her right cheek. The camera angle is a close-up, focused on the woman with brown hair's face. The lighting is warm and natural, likely from the setting sun, casting a soft glow on the scene. The scene appears to be real-life footage.</details> | ![example2](./docs/_static/ltx-video_example_00002.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A woman walks away from a white Jeep parked on a city street at night...</summary>A woman walks away from a white Jeep parked on a city street at night, then ascends a staircase and knocks on a door. The woman, wearing a dark jacket and jeans, walks away from the Jeep parked on the left side of the street, her back to the camera; she walks at a steady pace, her arms swinging slightly by her sides; the street is dimly lit, with streetlights casting pools of light on the wet pavement; a man in a dark jacket and jeans walks past the Jeep in the opposite direction; the camera follows the woman from behind as she walks up a set of stairs towards a building with a green door; she reaches the top of the stairs and turns left, continuing to walk towards the building; she reaches the door and knocks on it with her right hand; the camera remains stationary, focused on the doorway; the scene is captured in real-life footage.</details> | ![example3](./docs/_static/ltx-video_example_00003.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A woman with blonde hair styled up, wearing a black dress...</summary>A woman with blonde hair styled up, wearing a black dress with sequins and pearl earrings, looks down with a sad expression on her face. The camera remains stationary, focused on the woman's face. The lighting is dim, casting soft shadows on her face. The scene appears to be from a movie or TV show.</details> | ![example4](./docs/_static/ltx-video_example_00004.gif)<br><details style="max-width: 300px; margin: auto;"><summary>The camera pans over a snow-covered mountain range...</summary>The camera pans over a snow-covered mountain range, revealing a vast expanse of snow-capped peaks and valleys.The mountains are covered in a thick layer of snow, with some areas appearing almost white while others have a slightly darker, almost grayish hue. The peaks are jagged and irregular, with some rising sharply into the sky while others are more rounded. The valleys are deep and narrow, with steep slopes that are also covered in snow. The trees in the foreground are mostly bare, with only a few leaves remaining on their branches. The sky is overcast, with thick clouds obscuring the sun. The overall impression is one of peace and tranquility, with the snow-covered mountains standing as a testament to the power and beauty of nature.</details> |
| ![example5](./docs/_static/ltx-video_example_00005.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A woman with light skin, wearing a blue jacket and a black hat...</summary>A woman with light skin, wearing a blue jacket and a black hat with a veil, looks down and to her right, then back up as she speaks; she has brown hair styled in an updo, light brown eyebrows, and is wearing a white collared shirt under her jacket; the camera remains stationary on her face as she speaks; the background is out of focus, but shows trees and people in period clothing; the scene is captured in real-life footage.</details> | ![example6](./docs/_static/ltx-video_example_00006.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A man in a dimly lit room talks on a vintage telephone...</summary>A man in a dimly lit room talks on a vintage telephone, hangs up, and looks down with a sad expression. He holds the black rotary phone to his right ear with his right hand, his left hand holding a rocks glass with amber liquid. He wears a brown suit jacket over a white shirt, and a gold ring on his left ring finger. His short hair is neatly combed, and he has light skin with visible wrinkles around his eyes. The camera remains stationary, focused on his face and upper body. The room is dark, lit only by a warm light source off-screen to the left, casting shadows on the wall behind him. The scene appears to be from a movie.</details> | ![example7](./docs/_static/ltx-video_example_00007.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A prison guard unlocks and opens a cell door...</summary>A prison guard unlocks and opens a cell door to reveal a young man sitting at a table with a woman. The guard, wearing a dark blue uniform with a badge on his left chest, unlocks the cell door with a key held in his right hand and pulls it open; he has short brown hair, light skin, and a neutral expression. The young man, wearing a black and white striped shirt, sits at a table covered with a white tablecloth, facing the woman; he has short brown hair, light skin, and a neutral expression. The woman, wearing a dark blue shirt, sits opposite the young man, her face turned towards him; she has short blonde hair and light skin. The camera remains stationary, capturing the scene from a medium distance, positioned slightly to the right of the guard. The room is dimly lit, with a single light fixture illuminating the table and the two figures. The walls are made of large, grey concrete blocks, and a metal door is visible in the background. The scene is captured in real-life footage.</details> | ![example8](./docs/_static/ltx-video_example_00008.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A woman with blood on her face and a white tank top...</summary>A woman with blood on her face and a white tank top looks down and to her right, then back up as she speaks. She has dark hair pulled back, light skin, and her face and chest are covered in blood. The camera angle is a close-up, focused on the woman's face and upper torso. The lighting is dim and blue-toned, creating a somber and intense atmosphere. The scene appears to be from a movie or TV show.</details> |
| ![example9](./docs/_static/ltx-video_example_00009.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A man with graying hair, a beard, and a gray shirt...</summary>A man with graying hair, a beard, and a gray shirt looks down and to his right, then turns his head to the left. The camera angle is a close-up, focused on the man's face. The lighting is dim, with a greenish tint. The scene appears to be real-life footage. Step</details> | ![example10](./docs/_static/ltx-video_example_00010.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A clear, turquoise river flows through a rocky canyon...</summary>A clear, turquoise river flows through a rocky canyon, cascading over a small waterfall and forming a pool of water at the bottom.The river is the main focus of the scene, with its clear water reflecting the surrounding trees and rocks. The canyon walls are steep and rocky, with some vegetation growing on them. The trees are mostly pine trees, with their green needles contrasting with the brown and gray rocks. The overall tone of the scene is one of peace and tranquility.</details> | ![example11](./docs/_static/ltx-video_example_00011.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A man in a suit enters a room and speaks to two women...</summary>A man in a suit enters a room and speaks to two women sitting on a couch. The man, wearing a dark suit with a gold tie, enters the room from the left and walks towards the center of the frame. He has short gray hair, light skin, and a serious expression. He places his right hand on the back of a chair as he approaches the couch. Two women are seated on a light-colored couch in the background. The woman on the left wears a light blue sweater and has short blonde hair. The woman on the right wears a white sweater and has short blonde hair. The camera remains stationary, focusing on the man as he enters the room. The room is brightly lit, with warm tones reflecting off the walls and furniture. The scene appears to be from a film or television show.</details> | ![example12](./docs/_static/ltx-video_example_00012.gif)<br><details style="max-width: 300px; margin: auto;"><summary>The waves crash against the jagged rocks of the shoreline...</summary>The waves crash against the jagged rocks of the shoreline, sending spray high into the air.The rocks are a dark gray color, with sharp edges and deep crevices. The water is a clear blue-green, with white foam where the waves break against the rocks. The sky is a light gray, with a few white clouds dotting the horizon.</details> |
| ![example13](./docs/_static/ltx-video_example_00013.gif)<br><details style="max-width: 300px; margin: auto;"><summary>The camera pans across a cityscape of tall buildings...</summary>The camera pans across a cityscape of tall buildings with a circular building in the center. The camera moves from left to right, showing the tops of the buildings and the circular building in the center. The buildings are various shades of gray and white, and the circular building has a green roof. The camera angle is high, looking down at the city. The lighting is bright, with the sun shining from the upper left, casting shadows from the buildings. The scene is computer-generated imagery.</details> | ![example14](./docs/_static/ltx-video_example_00014.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A man walks towards a window, looks out, and then turns around...</summary>A man walks towards a window, looks out, and then turns around. He has short, dark hair, dark skin, and is wearing a brown coat over a red and gray scarf. He walks from left to right towards a window, his gaze fixed on something outside. The camera follows him from behind at a medium distance. The room is brightly lit, with white walls and a large window covered by a white curtain. As he approaches the window, he turns his head slightly to the left, then back to the right. He then turns his entire body to the right, facing the window. The camera remains stationary as he stands in front of the window. The scene is captured in real-life footage.</details> | ![example15](./docs/_static/ltx-video_example_00015.gif)<br><details style="max-width: 300px; margin: auto;"><summary>Two police officers in dark blue uniforms and matching hats...</summary>Two police officers in dark blue uniforms and matching hats enter a dimly lit room through a doorway on the left side of the frame. The first officer, with short brown hair and a mustache, steps inside first, followed by his partner, who has a shaved head and a goatee. Both officers have serious expressions and maintain a steady pace as they move deeper into the room. The camera remains stationary, capturing them from a slightly low angle as they enter. The room has exposed brick walls and a corrugated metal ceiling, with a barred window visible in the background. The lighting is low-key, casting shadows on the officers' faces and emphasizing the grim atmosphere. The scene appears to be from a film or television show.</details> | ![example16](./docs/_static/ltx-video_example_00016.gif)<br><details style="max-width: 300px; margin: auto;"><summary>A woman with short brown hair, wearing a maroon sleeveless top...</summary>A woman with short brown hair, wearing a maroon sleeveless top and a silver necklace, walks through a room while talking, then a woman with pink hair and a white shirt appears in the doorway and yells. The first woman walks from left to right, her expression serious; she has light skin and her eyebrows are slightly furrowed. The second woman stands in the doorway, her mouth open in a yell; she has light skin and her eyes are wide. The room is dimly lit, with a bookshelf visible in the background. The camera follows the first woman as she walks, then cuts to a close-up of the second woman's face. The scene is captured in real-life footage.</details> |

# Quick Start Guide

## Online demo
The model is accessible right away via following links:
- [HF Playground](https://huggingface.co/spaces/Lightricks/LTX-Video-Playground)
- [Fal.ai text-to-video](https://fal.ai/models/fal-ai/ltx-video)
- [Fal.ai image-to-video](https://fal.ai/models/fal-ai/ltx-video/image-to-video)

## Run locally

### Installation
The codebase was tested with Python 3.10.5, CUDA version 12.2, and supports PyTorch >= 2.1.2.

```bash
sudo apt-get update && sudo apt-get install cbm ffmpeg git-lfs

git clone https://github.com/Lightricks/LTX-Video.git
cd LTX-Video

# create env
python -m venv env
source env/bin/activate
python -m pip install -e .\[inference-script\]
```

Then, download the model from [Hugging Face](https://huggingface.co/Lightricks/LTX-Video) 

```python
import os
from huggingface_hub import hf_hub_download

# 设置 HF-Mirror 作为 Hugging Face 的下载端点
os.environ['HF_ENDPOINT'] = 'https://hf-mirror.com'

# 设置代理环境变量（如果需要代理）
# os.environ['http_proxy'] = 'http://your_proxy_server:port'
# os.environ['https_proxy'] = 'http://your_proxy_server:port'

# 下载模型
model_dir = 'MODEL_DIR'   # The local directory to save downloaded checkpoint
hf_hub_download(
    repo_id="Lightricks/LTX-Video", 
    filename="ltx-video-2b-v0.9.5.safetensors", 
    local_dir=model_dir, 
    local_dir_use_symlinks=False, 
    repo_type='model'
)
```

```bash
#!/bin/bash

# 定义常量
CKPT_PATH="MODEL_DIR/ltx-video-2b-v0.9.5.safetensors"  # 替换为实际的检查点路径
PROMPT="A beautiful landscape"  # 替换为实际的提示文本
HEIGHT=256                      # 替换为实际的高度值
WIDTH=256                       # 替换为实际的宽度值
NUM_FRAMES=30                   # 替换为实际的帧数
SEED=42                         # 替换为实际的随机种子值

# 执行Python命令
python inference.py \
    --ckpt_path "$CKPT_PATH" \
    --prompt "$PROMPT" \
    --height $HEIGHT \
    --width $WIDTH \
    --num_frames $NUM_FRAMES \
    --seed $SEED
```

```python
from huggingface_hub import snapshot_download

model_path = 'PATH'   # The local directory to save downloaded checkpoint
snapshot_download("Lightricks/LTX-Video", local_dir=model_path, local_dir_use_symlinks=False, repo_type='model')
```

```bash
python inference.py --ckpt_path 'PATH' --prompt "a balloon" --input_image_path IMG_8199. jpeg
--height 512 --width 512 --num_frames 16 --seed 42 --offload_to_cpu
```

### Inference

To use our model, please follow the inference code in [inference.py](./inference.py):

#### For text-to-video generation:

```bash
python inference.py --ckpt_dir 'PATH' --prompt "PROMPT" --height HEIGHT --width WIDTH --num_frames NUM_FRAMES --seed SEED
```

#### For image-to-video generation:

```bash
python inference.py --ckpt_dir 'PATH' --prompt "PROMPT" --input_image_path IMAGE_PATH --height HEIGHT --width WIDTH --num_frames NUM_FRAMES --seed SEED
```

## ComfyUI Integration
To use our model with ComfyUI, please follow the instructions at [https://github.com/Lightricks/ComfyUI-LTXVideo/](https://github.com/Lightricks/ComfyUI-LTXVideo/).

# Model User Guide

## 📝 Prompt Engineering

When writing prompts, focus on detailed, chronological descriptions of actions and scenes. Include specific movements, appearances, camera angles, and environmental details - all in a single flowing paragraph. Start directly with the action, and keep descriptions literal and precise. Think like a cinematographer describing a shot list. Keep within 200 words. For best results, build your prompts using this structure:

* Start with main action in a single sentence
* Add specific details about movements and gestures
* Describe character/object appearances precisely
* Include background and environment details
* Specify camera angles and movements
* Describe lighting and colors
* Note any changes or sudden events
* See [examples](#introduction) for more inspiration.

## 🎮 Parameter Guide

* Resolution Preset: Higher resolutions for detailed scenes, lower for faster generation and simpler scenes. The model works on resolutions that are divisible by 32 and number of frames that are divisible by 8 + 1 (e.g. 257). In case the resolution or number of frames are not divisible by 32 or 8 + 1, the input will be padded with -1 and then cropped to the desired resolution and number of frames. The model works best on resolutions under 720 x 1280 and number of frames below 257
* Seed: Save seed values to recreate specific styles or compositions you like
* Guidance Scale: 3-3.5 are the recommended values
* Inference Steps: More steps (40+) for quality, fewer steps (20-30) for speed

## More to come...

# Acknowledgement

We are grateful for the following awesome projects when implementing LTX-Video:
* [DiT](https://github.com/facebookresearch/DiT) and [PixArt-alpha](https://github.com/PixArt-alpha/PixArt-alpha): vision transformers for image generation.


[//]: # (## Citation)
