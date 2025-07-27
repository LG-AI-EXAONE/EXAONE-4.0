# EXAONE-4.0
<br>
<br>
<p align="center">
<img src="assets/EXAONE_Symbol+BI_3d.png", width="400", style="margin: 40 auto;">
<br>
<!-- <p align="center"> 🤗 <a href="https://huggingface.co/collections/LGAI-EXAONE/exaone-40-686b2e0069800c835ed48375">Hugging Face</a> &nbsp | &nbsp 📝 <a href="https://www.lgresearch.ai/blog/view?seq=576"> Blog</a> &nbsp | &nbsp 📑 <a href="https://arxiv.org/abs/2507.11407"> Technical Report </a>-->
<br>
<br>

<div align="center">
  <a href="https://huggingface.co/collections/LGAI-EXAONE/exaone-40-686b2e0069800c835ed48375" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/🤗-Huggingface-FC926C?style=for-the-badge" alt="Huggingface">
  </a>
  <a href="https://www.lgresearch.ai/blog/view?seq=576" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/📝-Blog-E343BD?style=for-the-badge" alt="Blog">
  </a>
  <a href="https://arxiv.org/abs/2507.11407" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/📑-Technical_Report-684CF4?style=for-the-badge" alt="Technical Report">
  </a>
  <a href="https://friendli.ai/suite/~/serverless-endpoints/LGAI-EXAONE/EXAONE-4.0-32B/overview" style="text-decoration: none;">
    <img src="https://img.shields.io/badge/✈️-Try_on_FriendliAI-2649BC?style=for-the-badge" alt="FriendliAI">
  </a>
</div>

<br>

| 🎉 License Updated! We are pleased to announce our more flexible licensing terms 🤗 [What's Different?](#license) |
|:---:|

<br>

## Introduction

We introduce **EXAONE 4.0**, which integrates a **Non-reasoning mode** and **Reasoning mode** to achieve both the excellent usability of [EXAONE 3.5](https://github.com/LG-AI-EXAONE/EXAONE-3.5) and the advanced reasoning abilities of [EXAONE Deep](https://github.com/LG-AI-EXAONE/EXAONE-Deep). To pave the way for the agentic AI era, EXAONE 4.0 incorporates essential features such as agentic tool use, and its multilingual capabilities are extended
to support Spanish in addition to English and Korean. 

The EXAONE 4.0 model series consists of two sizes: a mid-size **32B** model optimized for high performance, and a small-size **1.2B** model designed for on-device applications.

In the EXAONE 4.0 architecture, we apply new architectural changes compared to previous EXAONE models as below:

1. **Hybrid Attention**: For the 32B model, we adopt hybrid attention scheme, which combines *Local attention (sliding window attention)* with *Global attention (full attention)* in a 3:1 ratio. We do not use RoPE (Rotary Positional Embedding) for global attention for better global context understanding.
2. **QK-Reorder-Norm**: We reorder the LayerNorm position from the traditional Pre-LN scheme by applying LayerNorm directly to the attention and MLP outputs, and we add RMS normalization right after the Q and K projection. It helps yield better performance on downstream tasks despite consuming more computation.

For more details, please refer to our [technical report](https://arxiv.org/abs/2507.11407).

<br>

## News

- 2025.07.26 : 🌟 EXAONE 4.0 is officially supported by HuggingFace transformers! Please check out the [v4.54.0 release](https://github.com/huggingface/transformers/releases/tag/v4.54.0).
- 2025.07.18 : EXAONE 4.0 is officially supported by [llama.cpp](https://github.com/ggml-org/llama.cpp)! Please check out the released version [here](https://github.com/ggml-org/llama.cpp/releases/tag/b5932).
- 2025.07.15 : We release EXAONE 4.0, a hybrid reasoning model with enhanced usability including 32B and 1.2B. Please check out [these models](https://huggingface.co/collections/LGAI-EXAONE/exaone-40-686b2e0069800c835ed48375)!

<br>

## Performance

The following tables show the evaluation results of each model, with reasoning and non-reasoning mode. The evaluation details can be found in the [technical report](https://arxiv.org/abs/2507.11407).

- ✅ denotes the model has a hybrid reasoning capability, evaluated by selecting reasoning / non-reasoning on the purpose.
- To assess Korean **practical** and **professional** knowledge, we adopt both the [KMMLU-Redux](https://huggingface.co/datasets/LGAI-EXAONE/KMMLU-Redux) and [KMMLU-Pro](https://huggingface.co/datasets/LGAI-EXAONE/KMMLU-Pro) benchmarks. Both datasets are publicly released!


### 32B Reasoning Mode

<table>
    <tr>
        <th> </th>
        <th>EXAONE 4.0 32B </th>
        <th>Phi 4 reasoning-plus</th>
        <th>Magistral Small-2506</th>
        <th>Qwen 3 32B </th>
        <th>Qwen 3 235B </th>
        <th>DeepSeek R1-0528</th>
    </tr>
    <tr>
        <td align="center">Model Size</td>
        <td align="center">32.0B</td>
        <td align="center">14.7B</td>
        <td align="center">23.6B</td>
        <td align="center">32.8B</td>
        <td align="center">235B</td>
        <td align="center">671B</td>
    </tr>
    <tr>
        <td align="center">Hybrid Reasoning</td>
        <td align="center">✅</td>
        <td align="center"> </td>
        <td align="center"> </td>
        <td align="center">✅</td>
        <td align="center">✅</td>
        <td align="center"> </td>
    </tr>
    <tr>
        <td align="center" colspan='7'><i>World Knowledge</i></td>
    </tr>
    <tr>
        <td >MMLU-Redux</td>
        <td align="center">92.3</td>
        <td align="center">90.8</td>
        <td align="center">86.8</td>
        <td align="center">90.9</td>
        <td align="center">92.7</td>
        <td align="center">93.4</td>
    </tr>
    <tr>
        <td >MMLU-Pro</td>
        <td align="center">81.8</td>
        <td align="center">76.0</td>
        <td align="center">73.4</td>
        <td align="center">80.0</td>
        <td align="center">83.0</td>
        <td align="center">85.0</td>
    </tr>
    <tr>
        <td >GPQA-Diamond</td>
        <td align="center">75.4</td>
        <td align="center">68.9</td>
        <td align="center">68.2</td>
        <td align="center">68.4</td>
        <td align="center">71.1</td>
        <td align="center">81.0</td>
    </tr>
    <tr>
        <td align="center" colspan='7'><i>Math/Coding</i></td>
    </tr>
    <tr>
        <td >AIME 2025</td>
        <td align="center">85.3</td>
        <td align="center">78.0</td>
        <td align="center">62.8</td>
        <td align="center">72.9</td>
        <td align="center">81.5</td>
        <td align="center">87.5</td>
    </tr>
    <tr>
        <td >HMMT Feb 2025</td>
        <td align="center">72.9</td>
        <td align="center">53.6</td>
        <td align="center">43.5</td>
        <td align="center">50.4</td>
        <td align="center">62.5</td>
        <td align="center">79.4</td>
    </tr>
    <tr>
        <td >LiveCodeBench v5</td>
        <td align="center">72.6</td>
        <td align="center">51.7</td>
        <td align="center">55.8</td>
        <td align="center">65.7</td>
        <td align="center">70.7</td>
        <td align="center">75.2</td>
    </tr>
    <tr>
        <td >LiveCodeBench v6</td>
        <td align="center">66.7</td>
        <td align="center">47.1</td>
        <td align="center">47.4</td>
        <td align="center">60.1</td>
        <td align="center">58.9</td>
        <td align="center">70.3</td>
    </tr>
    <tr>
        <td align="center" colspan='7'><i>Instruction Following</i></td>
    </tr>
    <tr>
        <td >IFEval</td>
        <td align="center">83.7</td>
        <td align="center">84.9</td>
        <td align="center">37.9</td>
        <td align="center">85.0</td>
        <td align="center">83.4</td>
        <td align="center">80.8</td>
    </tr>
    <tr>
        <td >Multi-IF (EN)</td>
        <td align="center">73.5</td>
        <td align="center">56.1</td>
        <td align="center">27.4</td>
        <td align="center">73.4</td>
        <td align="center">73.4</td>
        <td align="center">72.0</td>
    </tr>
    <tr>
        <td align="center" colspan='7'><i>Agentic Tool Use</i></td>
    </tr>
    <tr>
        <td >BFCL-v3</td>
        <td align="center">63.9</td>
        <td align="center">N/A</td>
        <td align="center">40.4</td>
        <td align="center">70.3</td>
        <td align="center">70.8</td>
        <td align="center">64.7</td>
    </tr>
    <tr>
        <td >Tau-bench (Airline)</td>
        <td align="center">51.5</td>
        <td align="center">N/A</td>
        <td align="center">38.5</td>
        <td align="center">34.5</td>
        <td align="center">37.5</td>
        <td align="center">53.5</td>
    </tr>
    <tr>
        <td >Tau-bench (Retail)</td>
        <td align="center">62.8</td>
        <td align="center">N/A</td>
        <td align="center">10.2</td>
        <td align="center">55.2</td>
        <td align="center">58.3</td>
        <td align="center">63.9</td>
    </tr>
    <tr>
        <td align="center" colspan='7'><i>Multilinguality</i></td>
    </tr>
    <tr>
        <td >KMMLU-Pro</td>
        <td align="center">67.7</td>
        <td align="center">55.8</td>
        <td align="center">51.5</td>
        <td align="center">61.4</td>
        <td align="center">68.1</td>
        <td align="center">71.7</td>
    </tr>
    <tr>
        <td >KMMLU-Redux</td>
        <td align="center">72.7</td>
        <td align="center">62.7</td>
        <td align="center">54.6</td>
        <td align="center">67.5</td>
        <td align="center">74.5</td>
        <td align="center">77.0</td>
    </tr>
    <tr>
        <td >KSM</td>
        <td align="center">87.6</td>
        <td align="center">79.8</td>
        <td align="center">71.9</td>
        <td align="center">82.8</td>
        <td align="center">86.2</td>
        <td align="center">86.7</td>
    </tr>
    <tr>
        <td >MMMLU (ES)</td>
        <td align="center">85.6</td>
        <td align="center">84.3</td>
        <td align="center">68.9</td>
        <td align="center">82.8</td>
        <td align="center">86.7</td>
        <td align="center">88.2</td>
    </tr>
    <tr>
        <td >MATH500 (ES)</td>
        <td align="center">95.8</td>
        <td align="center">94.2</td>
        <td align="center">83.5</td>
        <td align="center">94.3</td>
        <td align="center">95.1</td>
        <td align="center">96.0</td>
    </tr>
</table>

### 32B Non-Reasoning Mode

<table>
    <tr>
        <th> </th>
        <th>EXAONE 4.0 32B </th>
        <th>Phi 4</th>
        <th>Mistral-Small-2506</th>
        <th>Gemma 3 27B</th>
        <th>Qwen3 32B </th>
        <th>Qwen3 235B </th>
        <th>Llama-4-Maverick</th>
        <th>DeepSeek V3-0324</th>
    </tr>
    <tr>
        <td align="center">Model Size</td>
        <td align="center">32.0B</td>
        <td align="center">14.7B</td>
        <td align="center">24.0B</td>
        <td align="center">27.4B</td>
        <td align="center">32.8B</td>
        <td align="center">235B</td>
        <td align="center">402B</td>
        <td align="center">671B</td>
    </tr>
    <tr>
        <td align="center">Hybrid Reasoning</td>
        <td align="center">✅</td>
        <td align="center"> </td>
        <td align="center"> </td>
        <td align="center"> </td>
        <td align="center">✅</td>
        <td align="center">✅</td>
        <td align="center"> </td>
        <td align="center"> </td>
    </tr>
    <tr>
        <td align="center" colspan='9'><i>World Knowledge</i></td>
    </tr>
    <tr>
        <td >MMLU-Redux</td>
        <td align="center">89.8</td>
        <td align="center">88.3</td>
        <td align="center">85.9</td>
        <td align="center">85.0</td>
        <td align="center">85.7</td>
        <td align="center">89.2</td>
        <td align="center">92.3</td>
        <td align="center">92.3</td>
    </tr>
    <tr>
        <td >MMLU-Pro</td>
        <td align="center">77.6</td>
        <td align="center">70.4</td>
        <td align="center">69.1</td>
        <td align="center">67.5</td>
        <td align="center">74.4</td>
        <td align="center">77.4</td>
        <td align="center">80.5</td>
        <td align="center">81.2</td>
    </tr>
    <tr>
        <td >GPQA-Diamond</td>
        <td align="center">63.7</td>
        <td align="center">56.1</td>
        <td align="center">46.1</td>
        <td align="center">42.4</td>
        <td align="center">54.6</td>
        <td align="center">62.9</td>
        <td align="center">69.8</td>
        <td align="center">68.4</td>
    </tr>
    <tr>
        <td align="center" colspan='9'><i>Math/Coding</i></td>
    </tr>
    <tr>
        <td >AIME 2025</td>
        <td align="center">35.9</td>
        <td align="center">17.8</td>
        <td align="center">30.2</td>
        <td align="center">23.8</td>
        <td align="center">20.2</td>
        <td align="center">24.7</td>
        <td align="center">18.0</td>
        <td align="center">50.0</td>
    </tr>
    <tr>
        <td >HMMT Feb 2025</td>
        <td align="center">21.8</td>
        <td align="center">4.0</td>
        <td align="center">16.9</td>
        <td align="center">10.3</td>
        <td align="center">9.8</td>
        <td align="center">11.9</td>
        <td align="center">7.3</td>
        <td align="center">29.2</td>
    </tr>
    <tr>
        <td >LiveCodeBench v5</td>
        <td align="center">43.3</td>
        <td align="center">24.6</td>
        <td align="center">25.8</td>
        <td align="center">27.5</td>
        <td align="center">31.3</td>
        <td align="center">35.3</td>
        <td align="center">43.4</td>
        <td align="center">46.7</td>
    </tr>
    <tr>
        <td >LiveCodeBench v6</td>
        <td align="center">43.1</td>
        <td align="center">27.4</td>
        <td align="center">26.9</td>
        <td align="center">29.7</td>
        <td align="center">28.0</td>
        <td align="center">31.4</td>
        <td align="center">32.7</td>
        <td align="center">44.0</td>
    </tr>
    <tr>
        <td align="center" colspan='9'><i>Instruction Following</i></td>
    </tr>
    <tr>
        <td >IFEval</td>
        <td align="center">84.8</td>
        <td align="center">63.0</td>
        <td align="center">77.8</td>
        <td align="center">82.6</td>
        <td align="center">83.2</td>
        <td align="center">83.2</td>
        <td align="center">85.4</td>
        <td align="center">81.2</td>
    </tr>
    <tr>
        <td >Multi-IF (EN)</td>
        <td align="center">71.6</td>
        <td align="center">47.7</td>
        <td align="center">63.2</td>
        <td align="center">72.1</td>
        <td align="center">71.9</td>
        <td align="center">72.5</td>
        <td align="center">77.9</td>
        <td align="center">68.3</td>
    </tr>
    <tr>
        <td align="center" colspan='9'><i>Long Context</i></td>
    </tr>
    <tr>
        <td >HELMET</td>
        <td align="center">58.3</td>
        <td align="center">N/A</td>
        <td align="center">61.9</td>
        <td align="center">58.3</td>
        <td align="center">54.5</td>
        <td align="center">63.3</td>
        <td align="center">13.7</td>
        <td align="center">N/A</td>
    </tr>
    <tr>
        <td >RULER</td>
        <td align="center">88.2</td>
        <td align="center">N/A</td>
        <td align="center">71.8</td>
        <td align="center">66.0</td>
        <td align="center">85.6</td>
        <td align="center">90.6</td>
        <td align="center">2.9</td>
        <td align="center">N/A</td>
    </tr>
    <tr>
        <td >LongBench v1</td>
        <td align="center">48.1</td>
        <td align="center">N/A</td>
        <td align="center">51.5</td>
        <td align="center">51.5</td>
        <td align="center">44.2</td>
        <td align="center">45.3</td>
        <td align="center">34.7</td>
        <td align="center">N/A</td>
    </tr>
    <tr>
        <td align="center" colspan='9'><i>Agentic Tool Use</i></td>
    </tr>
    <tr>
        <td >BFCL-v3</td>
        <td align="center">65.2</td>
        <td align="center">N/A</td>
        <td align="center">57.7</td>
        <td align="center">N/A</td>
        <td align="center">63.0</td>
        <td align="center">68.0</td>
        <td align="center">52.9</td>
        <td align="center">63.8</td>
    </tr>
    <tr>
        <td >Tau-Bench (Airline)</td>
        <td align="center">25.5</td>
        <td align="center">N/A</td>
        <td align="center">36.1</td>
        <td align="center">N/A</td>
        <td align="center">16.0</td>
        <td align="center">27.0</td>
        <td align="center">38.0</td>
        <td align="center">40.5</td>
    </tr>
    <tr>
        <td >Tau-Bench (Retail)</td>
        <td align="center">55.9</td>
        <td align="center">N/A</td>
        <td align="center">35.5</td>
        <td align="center">N/A</td>
        <td align="center">47.6</td>
        <td align="center">56.5</td>
        <td align="center">6.5</td>
        <td align="center">68.5</td>
    </tr>
    <tr>
        <td align="center" colspan='9'><i>Multilinguality</i></td>
    </tr>
    <tr>
        <td >KMMLU-Pro</td>
        <td align="center">60.0</td>
        <td align="center">44.8</td>
        <td align="center">51.0</td>
        <td align="center">50.7</td>
        <td align="center">58.3</td>
        <td align="center">64.4</td>
        <td align="center">68.8</td>
        <td align="center">67.3</td>
    </tr>
    <tr>
        <td >KMMLU-Redux</td>
        <td align="center">64.8</td>
        <td align="center">50.1</td>
        <td align="center">53.6</td>
        <td align="center">53.3</td>
        <td align="center">64.4</td>
        <td align="center">71.7</td>
        <td align="center">76.9</td>
        <td align="center">72.2</td>
    </tr>
    <tr>
        <td >KSM</td>
        <td align="center">59.8</td>
        <td align="center">29.1</td>
        <td align="center">35.5</td>
        <td align="center">36.1</td>
        <td align="center">41.3</td>
        <td align="center">46.6</td>
        <td align="center">40.6</td>
        <td align="center">63.5</td>
    </tr>
    <tr>
        <td >Ko-LongBench</td>
        <td align="center">76.9</td>
        <td align="center">N/A</td>
        <td align="center">55.4</td>
        <td align="center">72.0</td>
        <td align="center">73.9</td>
        <td align="center">74.6</td>
        <td align="center">65.6</td>
        <td align="center">N/A</td>
    </tr>
    <tr>
        <td >MMMLU (ES)</td>
        <td align="center">80.6</td>
        <td align="center">81.2</td>
        <td align="center">78.4</td>
        <td align="center">78.7</td>
        <td align="center">82.1</td>
        <td align="center">83.7</td>
        <td align="center">86.9</td>
        <td align="center">86.7</td>
    </tr>
    <tr>
        <td >MATH500 (ES)</td>
        <td align="center">87.3</td>
        <td align="center">78.2</td>
        <td align="center">83.4</td>
        <td align="center">86.8</td>
        <td align="center">84.7</td>
        <td align="center">87.2</td>
        <td align="center">78.7</td>
        <td align="center">89.2</td>
    </tr>
    <tr>
        <td >WMT24++ (ES)</td>
        <td align="center">90.7</td>
        <td align="center">89.3</td>
        <td align="center">92.2</td>
        <td align="center">93.1</td>
        <td align="center">91.4</td>
        <td align="center">92.9</td>
        <td align="center">92.7</td>
        <td align="center">94.3 </td>
    </tr>
</table>

### 1.2B Reasoning Mode

<table>
    <tr>
        <th> </th>
        <th>EXAONE 4.0 1.2B </th>
        <th>EXAONE Deep 2.4B</th>
        <th>Qwen 3 0.6B </th>
        <th>Qwen 3 1.7B </th>
        <th>SmolLM3 3B </th>
    </tr>
    <tr>
        <td align="center">Model Size</td>
        <td align="center">1.28B</td>
        <td align="center">2.41B</td>
        <td align="center">596M</td>
        <td align="center">1.72B</td>
        <td align="center">3.08B</td>
    </tr>
    <tr>
        <td align="center">Hybrid Reasoning</td>
        <td align="center">✅</td>
        <td align="center"> </td>
        <td align="center">✅</td>
        <td align="center">✅</td>
        <td align="center">✅</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>World Knowledge</i></td>
    </tr>
    <tr>
        <td >MMLU-Redux</td>
        <td align="center">71.5</td>
        <td align="center">68.9</td>
        <td align="center">55.6</td>
        <td align="center">73.9</td>
        <td align="center">74.8</td>
    </tr>
    <tr>
        <td >MMLU-Pro</td>
        <td align="center">59.3</td>
        <td align="center">56.4</td>
        <td align="center">38.3</td>
        <td align="center">57.7</td>
        <td align="center">57.8</td>
    </tr>
    <tr>
        <td >GPQA-Diamond</td>
        <td align="center">52.0</td>
        <td align="center">54.3</td>
        <td align="center">27.9</td>
        <td align="center">40.1</td>
        <td align="center">41.7</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>Math/Coding</i></td>
    </tr>
    <tr>
        <td >AIME 2025</td>
        <td align="center">45.2</td>
        <td align="center">47.9</td>
        <td align="center">15.1</td>
        <td align="center">36.8</td>
        <td align="center">36.7</td>
    </tr>
    <tr>
        <td >HMMT Feb 2025</td>
        <td align="center">34.0</td>
        <td align="center">27.3</td>
        <td align="center">7.0</td>
        <td align="center">21.8</td>
        <td align="center">26.0</td>
    </tr>
    <tr>
        <td >LiveCodeBench v5</td>
        <td align="center">44.6</td>
        <td align="center">47.2</td>
        <td align="center">12.3</td>
        <td align="center">33.2</td>
        <td align="center">27.6</td>
    </tr>
    <tr>
        <td >LiveCodeBench v6</td>
        <td align="center">45.3</td>
        <td align="center">43.1</td>
        <td align="center">16.4</td>
        <td align="center">29.9</td>
        <td align="center">29.1</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>Instruction Following</i></td>
    </tr>
    <tr>
        <td >IFEval</td>
        <td align="center">67.8</td>
        <td align="center">71.0</td>
        <td align="center">59.2</td>
        <td align="center">72.5</td>
        <td align="center">71.2</td>
    </tr>
    <tr>
        <td >Multi-IF (EN)</td>
        <td align="center">53.9</td>
        <td align="center">54.5</td>
        <td align="center">37.5</td>
        <td align="center">53.5</td>
        <td align="center">47.5</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>Agentic Tool Use</i></td>
    </tr>
    <tr>
        <td >BFCL-v3</td>
        <td align="center">52.9</td>
        <td align="center">N/A</td>
        <td align="center">46.4</td>
        <td align="center">56.6</td>
        <td align="center">37.1</td>
    </tr>
    <tr>
        <td >Tau-Bench (Airline)</td>
        <td align="center">20.5</td>
        <td align="center">N/A</td>
        <td align="center">22.0</td>
        <td align="center">31.0</td>
        <td align="center">37.0</td>
    </tr>
    <tr>
        <td >Tau-Bench (Retail)</td>
        <td align="center">28.1</td>
        <td align="center">N/A</td>
        <td align="center">3.3</td>
        <td align="center">6.5</td>
        <td align="center">5.4</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>Multilinguality</i></td>
    </tr>
    <tr>
        <td >KMMLU-Pro</td>
        <td align="center">42.7</td>
        <td align="center">24.6</td>
        <td align="center">21.6</td>
        <td align="center">38.3</td>
        <td align="center">30.5</td>
    </tr>
    <tr>
        <td >KMMLU-Redux</td>
        <td align="center">46.9</td>
        <td align="center">25.0</td>
        <td align="center">24.5</td>
        <td align="center">38.0</td>
        <td align="center">33.7</td>
    </tr>
    <tr>
        <td >KSM</td>
        <td align="center">60.6</td>
        <td align="center">60.9</td>
        <td align="center">22.8</td>
        <td align="center">52.9</td>
        <td align="center">49.7</td>
    </tr>
    <tr>
        <td >MMMLU (ES)</td>
        <td align="center">62.4</td>
        <td align="center">51.4</td>
        <td align="center">48.8</td>
        <td align="center">64.5</td>
        <td align="center">64.7</td>
    </tr>
    <tr>
        <td >MATH500 (ES)</td>
        <td align="center">88.8</td>
        <td align="center">84.5</td>
        <td align="center">70.6</td>
        <td align="center">87.9</td>
        <td align="center">87.5 </td>
    </tr>
</table>

### 1.2B Non-Reasoning Mode

<table>
    <tr>
        <th> </th>
        <th>EXAONE 4.0 1.2B </th>
        <th>Qwen 3 0.6B </th>
        <th>Gemma 3 1B</th>
        <th>Qwen 3 1.7B </th>
        <th>SmolLM3 3B </th>
    </tr>
    <tr>
        <td align="center">Model Size</td>
        <td align="center">1.28B</td>
        <td align="center">596M</td>
        <td align="center">1.00B</td>
        <td align="center">1.72B</td>
        <td align="center">3.08B</td>
    </tr>
    <tr>
        <td align="center">Hybrid Reasoning</td>
        <td align="center">✅</td>
        <td align="center">✅</td>
        <td align="center"> </td>
        <td align="center">✅</td>
        <td align="center">✅</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>World Knowledge</i></td>
    </tr>
    <tr>
        <td >MMLU-Redux</td>
        <td align="center">66.9</td>
        <td align="center">44.6</td>
        <td align="center">40.9</td>
        <td align="center">63.4</td>
        <td align="center">65.0</td>
    </tr>
    <tr>
        <td >MMLU-Pro</td>
        <td align="center">52.0</td>
        <td align="center">26.6</td>
        <td align="center">14.7</td>
        <td align="center">43.7</td>
        <td align="center">43.6</td>
    </tr>
    <tr>
        <td >GPQA-Diamond</td>
        <td align="center">40.1</td>
        <td align="center">22.9</td>
        <td align="center">19.2</td>
        <td align="center">28.6</td>
        <td align="center">35.7</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>Math/Coding</i></td>
    </tr>
    <tr>
        <td >AIME 2025</td>
        <td align="center">23.5</td>
        <td align="center">2.6</td>
        <td align="center">2.1</td>
        <td align="center">9.8</td>
        <td align="center">9.3</td>
    </tr>
    <tr>
        <td >HMMT Feb 2025</td>
        <td align="center">13.0</td>
        <td align="center">1.0</td>
        <td align="center">1.5</td>
        <td align="center">5.1</td>
        <td align="center">4.7</td>
    </tr>
    <tr>
        <td >LiveCodeBench v5</td>
        <td align="center">26.4</td>
        <td align="center">3.6</td>
        <td align="center">1.8</td>
        <td align="center">11.6</td>
        <td align="center">11.4</td>
    </tr>
    <tr>
        <td >LiveCodeBench v6</td>
        <td align="center">30.1</td>
        <td align="center">6.9</td>
        <td align="center">2.3</td>
        <td align="center">16.6</td>
        <td align="center">20.6</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>Instruction Following</i></td>
    </tr>
    <tr>
        <td >IFEval</td>
        <td align="center">74.7</td>
        <td align="center">54.5</td>
        <td align="center">80.2</td>
        <td align="center">68.2</td>
        <td align="center">76.7</td>
    </tr>
    <tr>
        <td >Multi-IF (EN)</td>
        <td align="center">62.1</td>
        <td align="center">37.5</td>
        <td align="center">32.5</td>
        <td align="center">51.0</td>
        <td align="center">51.9</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>Long Context</i></td>
    </tr>
    <tr>
        <td >HELMET</td>
        <td align="center">41.2</td>
        <td align="center">21.1</td>
        <td align="center">N/A</td>
        <td align="center">33.8</td>
        <td align="center">38.6</td>
    </tr>
    <tr>
        <td >RULER</td>
        <td align="center">77.4</td>
        <td align="center">55.1</td>
        <td align="center">N/A</td>
        <td align="center">65.9</td>
        <td align="center">66.3</td>
    </tr>
    <tr>
        <td >LongBench v1</td>
        <td align="center">36.9</td>
        <td align="center">32.4</td>
        <td align="center">N/A</td>
        <td align="center">41.9</td>
        <td align="center">39.9</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>Agentic Tool Use</i></td>
    </tr>
    <tr>
        <td >BFCL-v3</td>
        <td align="center">55.7</td>
        <td align="center">44.1</td>
        <td align="center">N/A</td>
        <td align="center">52.2</td>
        <td align="center">47.3</td>
    </tr>
    <tr>
        <td >Tau-Bench (Airline)</td>
        <td align="center">10.0</td>
        <td align="center">31.5</td>
        <td align="center">N/A</td>
        <td align="center">13.5</td>
        <td align="center">38.0</td>
    </tr>
    <tr>
        <td >Tau-Bench (Retail)</td>
        <td align="center">21.7</td>
        <td align="center">5.7</td>
        <td align="center">N/A</td>
        <td align="center">4.6</td>
        <td align="center">6.7</td>
    </tr>
    <tr>
        <td align="center" colspan='6'><i>Multilinguality</i></td>
    </tr>
    <tr>
        <td >KMMLU-Pro</td>
        <td align="center">37.5</td>
        <td align="center">24.6</td>
        <td align="center">9.7</td>
        <td align="center">29.5</td>
        <td align="center">27.6</td>
    </tr>
    <tr>
        <td >KMMLU-Redux</td>
        <td align="center">40.4</td>
        <td align="center">22.8</td>
        <td align="center">19.4</td>
        <td align="center">29.8</td>
        <td align="center">26.4</td>
    </tr>
    <tr>
        <td >KSM</td>
        <td align="center">26.3</td>
        <td align="center">0.1</td>
        <td align="center">22.8</td>
        <td align="center">16.3</td>
        <td align="center">16.1</td>
    </tr>
    <tr>
        <td >Ko-LongBench</td>
        <td align="center">69.8</td>
        <td align="center">16.4</td>
        <td align="center">N/A</td>
        <td align="center">57.1</td>
        <td align="center">15.7</td>
    </tr>
    <tr>
        <td >MMMLU (ES)</td>
        <td align="center">54.6</td>
        <td align="center">39.5</td>
        <td align="center">35.9</td>
        <td align="center">54.3</td>
        <td align="center">55.1</td>
    </tr>
    <tr>
        <td >MATH500 (ES)</td>
        <td align="center">71.2</td>
        <td align="center">38.5</td>
        <td align="center">41.2</td>
        <td align="center">66.0</td>
        <td align="center">62.4</td>
    </tr>
    <tr>
        <td >WMT24++ (ES)</td>
        <td align="center">65.9</td>
        <td align="center">58.2</td>
        <td align="center">76.9</td>
        <td align="center">76.7</td>
        <td align="center">84.0 </td>
    </tr>
</table>


<br>

## Run EXAONE 4.0

You should install the transformers library with version >= `4.54.0`.

### Non-reasoning mode

For general use, you can use the EXAONE 4.0 models with the following example:

```python
from transformers import AutoModelForCausalLM, AutoTokenizer

model_name = "LGAI-EXAONE/EXAONE-4.0-32B"

model = AutoModelForCausalLM.from_pretrained(
    model_name,
    torch_dtype="bfloat16",
    device_map="auto"
)
tokenizer = AutoTokenizer.from_pretrained(model_name)

# choose your prompt
prompt = "Explain how wonderful you are"
prompt = "Explica lo increíble que eres"
prompt = "너가 얼마나 대단한지 설명해 봐"

messages = [
    {"role": "user", "content": prompt}
]
input_ids = tokenizer.apply_chat_template(
    messages,
    tokenize=True,
    add_generation_prompt=True,
    return_tensors="pt"
)

output = model.generate(
    input_ids.to(model.device),
    max_new_tokens=128,
    do_sample=False,
)
print(tokenizer.decode(output[0]))
```

### Reasoning mode

The EXAONE 4.0 models have reasoning capabilities for handling complex problems. You can activate reasoning mode by using the `enable_thinking=True` argument with the tokenizer, which opens a reasoning block that starts with `<think>` tag without closing it.

```python
messages = [
    {"role": "user", "content": "Which one is bigger, 3.12 vs 3.9?"}
]
input_ids = tokenizer.apply_chat_template(
    messages,
    tokenize=True,
    add_generation_prompt=True,
    return_tensors="pt",
    enable_thinking=True,
)

output = model.generate(
    input_ids.to(model.device),
    max_new_tokens=128,
    do_sample=True,
    temperature=0.6,
    top_p=0.95
)
print(tokenizer.decode(output[0]))
```

> [!IMPORTANT]
> The model generation with reasoning mode can be affected sensitively by sampling parameters, so please refer to the [Usage Guideline](#usage-guideline) for better quality.

### Agentic tool use

The EXAONE 4.0 models can be used as agents with their tool calling capabilities. You can provide tool schemas to the model for effective tool calling.

```python
import random

def roll_dice(max_num: int):
    return random.randint(1, max_num)

tools = [
    {
        "type": "function",
        "function": {
            "name": "roll_dice",
            "description": "Roll a dice with the number 1 to N. User can select the number N.",
            "parameters": {
                "type": "object",
                "required": ["max_num"],
                "properties": {
                    "max_num": {
                        "type": "int",
                        "description": "Max number of the dice"
                    }
                }
            }
        }
    }
]

messages = [
    {"role": "user", "content": "Roll D6 dice twice!"}
]
input_ids = tokenizer.apply_chat_template(
    messages,
    tokenize=True,
    add_generation_prompt=True,
    return_tensors="pt",
    tools=tools,
)

output = model.generate(
    input_ids.to(model.device),
    max_new_tokens=1024,
    do_sample=True,
    temperature=0.6,
    top_p=0.95,
)
print(tokenizer.decode(output[0]))
```

<br>

## Quantized Models

We provide EXAONE 4.0 in various quantized formats including GPTQ, AWQ, and GGUF.

For AWQ quantization, we omitted layernorm smoothing due to our use of Reorder-LN architecture.

All quantized models are available on our [HuggingFace collections](https://huggingface.co/collections/LGAI-EXAONE/exaone-40-686b2e0069800c835ed48375).

<br>

## Run Locally

### llama.cpp
You can run EXAONE models locally using llama.cpp by following these steps:

1. Install the latest version of llama.cpp (version >= `b5932`). Please check the official [installation guide](https://github.com/ggml-org/llama.cpp?tab=readme-ov-file#quick-start) from llama.cpp.

2. Download the EXAONE 4.0 model weights in GGUF format.

    ```bash
    huggingface-cli download LGAI-EXAONE/EXAONE-4.0-32B-GGUF \
        --include "EXAONE-4.0-32B-Q4_K_M.gguf" \
        --local-dir .
    ```


<details>
<summary>Generation with `llama-cli`</summary>

3. Apply chat template using transformers.

    > This process is necessary to avoid issues with current EXAONE modeling code in `llama.cpp`. This is work in progress at our [PR](https://github.com/ggml-org/llama.cpp/pull/14630). We will update this once these issues are solved.

    ```python
    from transformers import AutoModelForCausalLM, AutoTokenizer

    model_name = "LGAI-EXAONE/EXAONE-4.0-32B"
    tokenizer = AutoTokenizer.from_pretrained(model_name)

    messages = [
        {"role": "user", "content": "Let's work together on local system!"}
    ]
    input_text = tokenizer.apply_chat_template(
        messages,
        tokenize=False,
        add_generation_prompt=True,
    )

    print(repr(input_text))
    with open("inputs.txt", "w") as f:
        f.write(input_text)
    ```

4. Generate result with greedy decoding.
    ```bash
    llama-cli -m EXAONE-4.0-32B-Q4_K_M.gguf \
        -fa -ngl 65 \
        --temp 0.0 --top-k 1 \
        -f inputs.txt -no-cnv
    ```

</details>

<details>
<summary>OpenAI compatible server with `llama-server`</summary>

3. Run llama-server with EXAONE 4.0 Jinja template. You can find the [chat template file](https://huggingface.co/LGAI-EXAONE/EXAONE-4.0-32B/blob/main/chat_template.jinja) in this repository.
    ```bash
    llama-server -m EXAONE-4.0-32B-Q4_K_M.gguf \
        -c 131072 -fa -ngl 65 \
        --temp 0.6 --top-p 0.95 \
        --jinja --chat-template-file chat_template.jinja \
        --host 0.0.0.0 --port 8820 \
        -a EXAONE-4.0-32B-Q4_K_M
    ```

4. Use OpenAI chat completion to test the GGUF model.
    ```bash
    curl -X POST http://localhost:8820/v1/chat/completions \
        -H "Content-Type: application/json" \
        -d '{
            "model": "EXAONE-4.0-32B-Q4_K_M",
            "messages": [
                {"role": "user", "content": "Let'\''s work together on server!"}
            ],
            "max_tokens": 1024,
            "temperature": 0.6,
            "top_p": 0.95,
            "chat_template_kwargs": {"enable_thinking": false}
        }'
    ```

</details>

<br>

## Deployment

### TensorRT-LLM

TensorRT-LLM officially supports EXAONE 4.0 models in the latest commits. Before it is released, you need to clone the TensorRT-LLM repository to build from source.

```bash
git clone https://github.com/NVIDIA/TensorRT-LLM.git
```

After cloning the repository, you need to build the source for installation. Please refer to [the official documentation](https://nvidia.github.io/TensorRT-LLM/installation/build-from-source-linux.html) for a guide to build the TensorRT-LLM environment.

You can run the TensorRT-LLM server by following steps:

1. Write extra configuration YAML file
    ```yaml
    # extra_llm_api_config.yaml
    kv_cache_config:
      enable_block_reuse: false
    ```

2. Run server with the configuration
    ```bash
    trtllm-serve serve [MODEL_PATH] --backend pytorch --extra_llm_api_options extra_llm_api_config.yaml
    ```

For more details, please refer to [the documentation](https://github.com/NVIDIA/TensorRT-LLM/tree/main/examples/models/core/exaone) of EXAONE from TensorRT-LLM.

> [!NOTE]
> Other inference engines including `vllm` and `sglang` don't support the EXAONE 4.0 officially now. We will update as soon as these libraries are updated.

<br>

## Usage Guideline

> [!IMPORTANT]
> To achieve the expected performance, we recommend using the following configurations:
> 
> - For non-reasoning mode, we recommend using a lower temperature value such as `temperature<0.6` for better performance.
> - For reasoning mode (using `<think>` block), we recommend using `temperature=0.6` and `top_p=0.95`.
>     - If you suffer from the model degeneration, we recommend using `presence_penalty=1.5`. 
> - For Korean general conversation with 1.2B model, we suggest to use `temperature=0.1` to avoid code switching.

<br>

## Limitation

The EXAONE language model has certain limitations and may occasionally generate inappropriate responses. The language model generates responses based on the output probability of tokens, and it is determined during learning from training data. While we have made every effort to exclude personal, harmful, and biased information from the training data, some problematic content may still be included, potentially leading to undesirable responses. Please note that the text generated by EXAONE language model does not reflect the views of LG AI Research.

- Inappropriate answers may be generated, which contain personal, harmful or other inappropriate information.
- Biased responses may be generated, which are associated with age, gender, race, and so on.
- The generated responses rely heavily on statistics from the training data, which can result in the generation of
semantically or syntactically incorrect sentences.
- Since the model does not reflect the latest information, the responses may be false or contradictory.

LG AI Research strives to reduce potential risks that may arise from EXAONE language models. Users are not allowed
to engage in any malicious activities (e.g., keying in illegal information) that may induce the creation of inappropriate
outputs violating LG AI's ethical principles when using EXAONE language models.

<br>

## License

The model is licensed under [EXAONE AI Model License Agreement 1.2 - NC](./LICENSE)

> [!NOTE]
> The main difference from the older version is as below:
> - We removed **the claim of model output ownership** from the license.
> - We restrict the model use **against the development of models that compete with EXAONE**.
> - We allow the model to be used for **educational purposes**, not just research.

<br>

## Citation

```
@article{exaone-4.0,
  title={EXAONE 4.0: Unified Large Language Models Integrating Non-reasoning and Reasoning Modes},
  author={{LG AI Research}},
  journal={arXiv preprint arXiv:2507.11407},
  year={2025}
}
```

<br>

## Contact

LG AI Research Technical Support: contact_us@lgresearch.ai
