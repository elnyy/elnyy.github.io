---
title: "SDXLでネガティブプロンプトとポジティブプロンプトを入れ替えてしまったトラブル"
description: ""
date: "2026-06-10T12:23:07Z"
thumbnail: ""
categories:
  - "AI"
tags:
  - "SDXL"
  - "Python"
---
## 環境
* SDXL, RealVisXL

最近ローカルLLMで画像生成を始めて、ポジティブプロンプトとネガティブプロンプトを入れ替えてしまうということで苦しみました。
何が苦しかったって？本当はcivitalのRealVisXLのページにあった金髪の美しい女性を出力したかったのですが、プロンプトを逆にしてしまっているということで、**それとは真逆の恐ろしい画像が出力されてしまう**ことです。閲覧注意レベルな画像です。


この記事の一番下に画像を載っけておきます。

そしてこれが問題の逆プロンプトにしてしまったPythonスクリプトです。
```
from diffusers import StableDiffusionXLPipeline
import torch
import os

MODEL = "./models/realvisxl.safetensors"

pipe = StableDiffusionXLPipeline.from_single_file(
    MODEL,
    torch_dtype=torch.float16,
    variant="fp16",
    use_safetensors=True,
)
pipe.to("cuda")

negative = """
instagram photo, front shot, closeup portrait photo of 21 y.o woman, wearing dress, beautiful face, smile, blonde, cinematic shot, dark shot
""",

PROMPTS = {
    "woman": """
(octane render, render, drawing, anime, bad photo, bad photography:1.3), (worst quality, low quality, blurry:1.2), (bad teeth, deformed teeth, deformed lips), (bad anatomy, bad proportions:1.1), (deformed iris, deformed pupils), (deformed eyes, bad eyes), (deformed face, ugly face, bad face), (deformed hands, bad hands, fused fingers), morbid, mutilated, mutation, disfigured
""",
}

os.makedirs("output", exist_ok=True)

generator = torch.Generator("cuda")

for category, prompt in PROMPTS.items():

    outdir = f"output/{category}"
    os.makedirs(outdir, exist_ok=True)

    for i in range(40):

        generator.manual_seed(torch.randint(0, 2**31 - 1, (1,)).item())

        image = pipe(
            prompt=prompt,
            negative_prompt=negative,
            width=1024,
            height=1024,
            num_inference_steps=50,
            guidance_scale=5.5,
            generator=generator,
        ).images[0]

        filename = f"{outdir}/{i:02d}.png"
        image.save(filename)

        print("saved:", filename)

```
## 所感
最初何が原因でこんなGURO画像が出るのか分からず、混乱して3,4回むやみにコード実行していましたがこういうときこそAI頼るべきだなーと思いました。 AIにコード渡したら一発で指摘してくれたので…

最後に、こちらが逆プロンプトで生成した画像です。
![](/images/reversed-prompt01.png)

お口直しにちゃんと生成できた画像も載っけておきます。＾＿＾
![](/images/reversed-prompt02.png)
