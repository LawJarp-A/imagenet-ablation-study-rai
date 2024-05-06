# imagenet-ablation-study-rai
Abalation study of Deep NN's on the Imagenet 100 dataset

## Aim
Train various archturectures on the Imagenet 100 a subset of the original 1K variant

## My Approach
* Usd pytorch lightning to abstract few thigs in the th epytorch trainng code
* Logged the metrics onto Wandb for future refernce and monitoring
* Trained with
    * GPU
    * Mixed precision
    * Early Stoppping
    * saving best model
* Since I'm GPU  poor, I used the Kaggle 30 hours of free GPU time to utilize it's powerful P100 Gopu to train, nonetheless the SOTA visio transformer took a lot of time, henc had to cute thm off at various epochs. 

## Ablation Study
* Due to the contrainst on resource to repeatdely train thes SOTA architecture, I have used 5 architures and compiled the metrics for each one of them for each class
* Here are the findings from 