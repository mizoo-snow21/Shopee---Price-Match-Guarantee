# Shopee---Price-Match-Guarantee

We got 829th prize.  
This is summary and codes.

# Summary
![image](https://user-images.githubusercontent.com/55850618/125023066-0ad16a00-e0b9-11eb-8158-609b93270051.png)

# CNN Model
## NFNetl0
・img_size = 512 x 512  
・activation = silu→mish   
・optimizer = ranger  
・loss = CurricularFace  

## NFNetl1
・img_size = 512 x 512   
・activation = silu→mish  
・optimizer = ranger  
・loss = CurricularFace  

## Efficientnetb5
・img_size = 512 x 512    
・activation = relu→mish   
・optimizer = ranger  
・loss = CurricularFace  

## Resnest101e
・img_size = 512 x 512  
・activation = relu→mish  
・optimizer = ranger  
・loss = ArcFace  
・pooling = GeM  

## Weighted_Averaging
・Pulic Score 0.9063  
・Private Score 0.9010  

## Augmentaion
```
def get_train_transforms():
    return albumentations.Compose(
        [   albumentations.Resize(Config.IMG_SIZE,Config.IMG_SIZE,always_apply=True),
            albumentations.HorizontalFlip(p=0.5),
            albumentations.VerticalFlip(p=0.5),
            albumentations.Rotate(limit=120, p=0.8),
            albumentations.RandomBrightness(limit=(0.09, 0.6), p=0.5),
            albumentations.Normalize(mean = Config.MEAN, std = Config.STD),
            ToTensorV2(p=1.0),
        ]
    
```

## LR Scheduler
CosineAnnealingWarmRestarts

# NLP Model
## Roberta-base
・input = Indo → English  
・optimizer = Adam  
・loss = ArcFace  

## paraphrase-xlm-r-multilingual-v1
・optimizer = Adam  
・loss = ArcFace  

## distilbert-base-indonesian
・input = English → Indo  
・optimizer = Adam  
・loss = ArcFace   

# Not Worked
・model: Seresnexts、other resnests、other Efficientnets、other NFnets、regnets  
・loss: AdaCos、Focalloss  
・activation: relu→mish、silu→mish  
・optimizer: SGD、adamw  
・augmentation: Cutout、RandAugment、Autoaugment  
・other: AMP、 emmbedding concat  
