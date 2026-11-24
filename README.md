# BERT-esg-ai-narrative-classifier
Code for fine-tuning bert-base-chinese to classify AI-related ESG report sentences as E (executability), N (other), or S (speculativeness).
ESG 報告中的 AI 敘事分類
本專案使用 bert-base-chinese 微調中文句子分類模型，辨識企業永續報告中與 AI 相關的敘述，並將句子分為 E、N、S 三種類型。
專案目的
企業永續報告對 AI 的描述可能包含具體行動與應用，也可能是對未來發展的預期。本專案以句子為分析單位，透過文字分類辨識不同的 AI 敘事取向。
語料規模
- **報告層級樣本：3,500 多筆公司－年觀察值，每筆對應一本永續報告書。
- **句子數：由報告切分而成的 33,400 個句子。
- **測試集：1,800 個人工標註句子。
- **資料說明：本專案不包含原始報告書與人工標註資料。
- 
標籤定義
E	可執行性：具體描述 AI 行動、應用或落實方式。
N	中性／其他：不明確屬於 E 或 S 的敘述。
S	可推測性：描述 AI 未來可能的發展、效益或預期。

可在 bert_sentence_classifier.py 的 LABELS 清單中自訂標籤。Excel 的 label 欄內容必須與清單設定一致。
模型分類成果
以下為 1,800 個句子測試集的分類結果。

模型會先輸出各類別的 logits，再透過 Softmax 函數轉換為 E、N、S 三種類別的機率分布。 每個句子的預測標籤為機率最高的類別；分類機率也可進一步彙整為公司－年層級指標。
類別	Precision	Recall	F1-score
E	     82.8%	  87.5%	   85.1%
N	     86.0%	  79.9%	   82.8%
S	     83.3%	  83.8%	   83.6%
平均	 84.1%	  83.7%	   83.8%

Accuracy：83.4%
使用技術
- Python
- PyTorch
- Hugging Face Transformers、Datasets
- bert-base-chinese
- pandas、NumPy、scikit-learn
- SOFTMAX




