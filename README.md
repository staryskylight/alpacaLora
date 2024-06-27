# alpacaLora

克隆项目：

```python
git clone https://github.com/staryskylight/alpacaLora.git
cd alpacaLora/

git lfs install

git clone https://gitee.com/hf-models/llama-7b-hf.git
```

安装依赖项：

```python
pip install -r requirements.txt
```



训练：

默认训练方式：

```python
python finetune.py  --base_model './llama-7b-hf'  --data_path './alpaca_data.json' 
--output_dir './lora-alpaca'
```



可选参数调整：

```python
python finetune.py \
    --base_model './llama-7b-hf' \
    --data_path './alpaca_data.json' \
    --output_dir './lora-alpaca2' \
    --batch_size 512 \
    --micro_batch_size 4 \
    --num_epochs 3 \
    --learning_rate 1e-4 \
    --cutoff_len 512 \
    --val_set_size 2000 \
    --lora_r 8 \
    --lora_alpha 16 \
    --lora_dropout 0.05 \
    --lora_target_modules '[q_proj,v_proj]' \
    --train_on_inputs \
    --group_by_length
```



推理：

```python
python generate.py --load_8bit --base_model './llama-7b-hf' --lora_weights './lora-alpaca'
```

