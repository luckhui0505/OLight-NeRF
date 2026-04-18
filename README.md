# OLight-NeRF


## 1.Install environment
```
git clone https://github.com/luckhui0505/OLight-NeRF.git
cd OLight-NeRF
conda create -n OLight -c anaconda python=3.8
conda activate OLight_nerf
conda install pytorch==1.11.0 torchvision==0.12.0 torchaudio==0.11.0 cudatoolkit=11.3 -c pytorch
pip install -r requirements.txt
```
## 2. Abstract

Neural Radiance Fields (NeRF) have achieved significant progress in new-view synthesis and 3D reconstruction tasks. However, under complex lighting conditions—such as low illumination, local overexposure, and uneven brightness distribution—the degradation of image visibility interferes with color and volume density modeling, leading to unstable geometric reconstruction and reduced rendering quality. To address these issues, this paper proposes OLight-NeRF, an occlusion-aware neural rendering method designed for complex lighting degradation scenarios, which enhances the robustness of novel view synthesis and 3D reconstruction under low-quality input conditions by focusing on local visibility modeling. Specifically, this paper first proposes an Occlusion-aware Density Modulation (ODM) mechanism. By predicting the local visibility response of sampling points and applying bounded modulation to the volume density, visibility information is explicitly incorporated into the radiation field modeling process to enhance structural representation under complex lighting conditions; Second, we design a Luminance-aware Adaptive Enhancement (LAE) module as a lightweight enhancement component that applies differential modulation to dark and bright regions to improve the visibility of details in dark areas while suppressing over-enhancement in highly illuminated regions; Finally, we propose a Progressive Occlusion Optimization (PO) strategy, which stabilizes the training of the occlusion branch through a warm-up mechanism as well as center and smoothness constraints, thereby mitigating early optimization instability. Experimental results demonstrate that the proposed method achieves competitive performance in both low-light and high-exposure scenarios, with significant improvements over SOTA on PSNR, SSIM, and LPIPS metrics.
## 3. Comparison of Experimental Results
![image](https://github.com/luckhui0505/LowLight-NeRF/blob/main/pic/figure_1.jpg) 

## 4. Training Aleth-NeRF


```
CUDA_VISIBLE_DEVICES=0,1,2,3 python3 run.py --ginc configs/LOM/OLight-NeRF/aleth_nerf_buu.gin --logbase ./logs 
```

You can also direct use following command to run all 5 scenes scenes together:

```
bash run/run_LOM_aleth.sh
```




## 5. Setting parameters
Changing the data path and log path in the configs/demo_blurfactory.txt

## Some Notes
### GPU Memory
We train our model on a RTX3090 GPU with 24GB GPU memory. If you have less memory, setting N_rand to a smaller value, or use multiple GPUs.
## Acknowledge
Code is based on Aleth-Nerf, much thanks to their excellent codebase! 











