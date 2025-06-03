## TISER

### Learning to Reason Over Time: Timeline Self-Reflection for Improved Temporal Reasoning in Language Models

This repository contains the data for the paper (ACL 2025 Main): [Learning to Reason Over Time: Timeline Self-Reflection for Improved Temporal Reasoning in Language Models](https://arxiv.org/pdf/2504.05258).

TISER incorporates a multi-stage inference pipeline that combines explicit reasoning, timeline construction, and iterative self-reflection. The key idea behind our approach is to empower LLMs to adapt by scaling their internal reasoning process during inference. TISER enables models to systematically organize temporal information, verify their inferences, and refine their outputs.

## Train Data Format

Each entry in the [TISER train dataset](data/TISER_train.json) is a JSON object containing six fields: `dataset_name`, `question_id`, `question`, `answer`, `prompt`, and `output`. The `question` field specifies the temporal question being asked, while `answer` contains the expected short-form response (e.g., an entity or number). The `prompt` provides detailed instructions for a Chain of Thought (CoT) reasoning process with reflection, guiding the model to reason step-by-step, extract temporal events, reflect on its logic, and produce a final answer. The `output` field contains the full model-generated response adhering to this reasoning format. This structure supports supervised training of models to perform temporal reasoning and answer generation.

## Test Data Format

Each test example in the [TISER test dataset](data/TISER_test.json) is represented as a single JSON object containing five fields: `dataset_name`, which specifies the split or task; `question_id`, a unique identifier for the query; `question`, the temporal reasoning prompt itself; `prompt`, which embeds the full Chain-of-Thought template (including `<reasoning>`, `<timeline>`, `<reflection>` and `<answer>` tags) that the model should follow when generating its response; and `answer`, the held-out ground-truth output against which the model’s `<answer>` section is evaluated. Unlike the training format, there is no `output` field in test records, since models read the `prompt` and produce only an `<answer>` that is scored directly against the provided `answer` key.

## Data Subsets Provenance

Original data subsets before our preprocessing were extracted from the following HuggingFace URLs

- TGQA: [https://huggingface.co/datasets/sxiong/TGQA/viewer/TGQA_TGR](https://huggingface.co/datasets/sxiong/TGQA/viewer/TGQA_TGR)
- TempReason (L2): [https://huggingface.co/datasets/sxiong/TGQA/viewer/TempReason_TGR/l2_train](https://huggingface.co/datasets/sxiong/TGQA/viewer/TempReason_TGR/l2_train)
- TempReason (L3): [https://huggingface.co/datasets/sxiong/TGQA/viewer/TempReason_TGR/l3_train](https://huggingface.co/datasets/sxiong/TGQA/viewer/TempReason_TGR/l3_train)
- TimeQA (easy): [https://huggingface.co/datasets/sxiong/TGQA/viewer/TimeQA_TGR/easy_train](https://huggingface.co/datasets/sxiong/TGQA/viewer/TimeQA_TGR/easy_train)
- TimeQA (hard): [https://huggingface.co/datasets/sxiong/TGQA/viewer/TimeQA_TGR/hard_train](https://huggingface.co/datasets/sxiong/TGQA/viewer/TimeQA_TGR/hard_train)

## Citation
```
@misc{bazaga2025learningreasontimetimeline,
      title={Learning to Reason Over Time: Timeline Self-Reflection for Improved Temporal Reasoning in Language Models}, 
      author={Adrián Bazaga and Rexhina Blloshmi and Bill Byrne and Adrià de Gispert},
      year={2025},
      eprint={2504.05258},
      archivePrefix={arXiv},
      primaryClass={cs.LG},
      url={https://arxiv.org/abs/2504.05258}, 
}
```

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the [LICENSE](LICENSE)  file.

## Contact

For feedback or questions please contact [Adrián Bazaga](https://bazaga.ai/)