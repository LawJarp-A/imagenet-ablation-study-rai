# Imagenet Ablation Study: Insights from Training Various Architectures

## Aim
The goal of this study was to train and analyze the performance of various deep neural network architectures on the Imagenet 100 dataset, a subset of the original 1K variant.

## Note
Since I am GPU poor, I used Kaggle to train the models, and had limited (10 -12 hours of GPU time left for the week), hence had to cut short trainings on huge models. 

## Approach
- Utilized PyTorch Lightning to abstract some parts in the training code.
- Logged metrics on Wandb for future reference and monitoring.
- Employed GPU acceleration, mixed precision training, early stopping, and saved the best models.
- Leveraged Kaggle GPU resources due to personal GPU limitations.

## WandB Logging
All training and monitoring activities were logged on my Weights and Biases (Wandb) dashboard, facilitating visualization of the training process and enabling effective tracking of underperformance or overfitting cycles.

Here reports on Wandb:

[Model Trainings on Wandb](https://wandb.ai/lawjarp/rai_ablation_study/reports/Monitoring-Training-at-a-Glance--Vmlldzo3ODQzNzEw?accessToken=4wn7qq7fm4gizeo43w89l552ph378jfug8nmy9eodda5ixroc34ihqiiddproy31)

[Ablation Study on Wandb](https://wandb.ai/lawjarp/rai_ablation_study/reports/Monitoring-Training-at-a-Glance--Vmlldzo3ODQzNjgy?accessToken=ysgvcjdg8xrz93tj0zztclk3dmvar0aqrr2xe86xiq8tsjuui3ajgrm6ajr3ukpj)

## Hyperparameters
- Batch size: 128
- Image size: 224
- Adjusted epochs based on GPU time constraints: 10 epochs for CNN models, 5 to 6 epochs for transformers.

## Performance on Various Models
- ResNet led as the top-performing model, closely followed by Swin Transformer. Swin's technical superiority was hindered by GPU limitations despite achieving comparable accuracy to ResNet in fewer epochs.
- EfficientNet demonstrated a balance between performance and complexity, securing the third position among the models.
- ViT showed promise but may require additional training time, with training limited to 6 epochs.
- MobileNet highlighted the efficiency of smaller networks, performing comparably to larger architectures.

## Reasons for Architecture Selection
- ResNet and Swin Transformer were chosen for their established performance in computer vision tasks.
- ResNet was chosen as it is a DeepCNN in truest sense with mutliple layer and skip connections
- A Swin transformer is a improvement on the Vanilla VIt introducing efficent ways to attend to patches of images, and it is also a gold standard for classifictaiob task, but only if you have a ton of data :)
- EfficientNet represented a balance between performance and complexity.
- ViT was included to explore the potential of vision transformers and its performance
- MobileNet showcased the efficiency of smaller networks compared to larger architectures. The accuracies are comparable while leaving a smaller compute footprint. The efficiency largely seems to outweigh the performance for some use cases

## Ablation Study
- Conducted an ablation study on EfficientNet to analyze the impact of image size and augmentations.
- Just conducted on Efficienet as conducting on all models is quite time consuming
  
| Model                  | Image Size | Final Train Acc | Final Val Acc |
|------------------------|------------|-----------------|---------------|
| EfficientNet B0        | 64x64      | 0.348           | 0.316         |
| EfficientNet B0        | 128x128    | 0.61            | 0.58          |
| EfficientNet B0 with augmentation | 128x128 | 0.552       | 0.557         |

This study provides valuable insights into the performance and characteristics of various deep neural network architectures, contributing to the understanding of their applicability and effectiveness in image classification tasks.