# Language-model-fine-tune

透過 [Hugging face 的教學](https://colab.research.google.com/github/huggingface/notebooks/blob/main/examples/language_modeling.ipynb?authuser=1&hl=zh-tw) 學習 fine-tune 一個 **Mask** language model 

1. 首先加入訓練資料集 eli5 
2. 透過 pretrained model 將每一段輸入 tokenize 並回傳
3. 串接所有輸入再切成 chunk size ，即模型最大可接受大小
4. 載入 pretrained Mask language model distilroberta-base
5. 訓練 

perplexity : 使用模型對給定序列的預測概率的倒數

測試 : 
```python
text = "Deep learing is a <mask> in this laboratory."

mask_filler(text, top_k=3)

[{'score': 0.18199005722999573,
  'token': 936,
  'token_str': ' problem',
  'sequence': 'Deep learing is a problem in this laboratory.'},
 {'score': 0.06399531662464142,
  'token': 33984,
  'token_str': ' rarity',
  'sequence': 'Deep learing is a rarity in this laboratory.'},
 {'score': 0.056482452899217606,
  'token': 2212,
  'token_str': ' concern',
  'sequence': 'Deep learing is a concern in this laboratory.'}]
```
