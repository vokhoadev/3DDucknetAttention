# 3DDucknetAttention

How to use?
~ python utils/setup.py <!your wandb key or empty>
Prepair you datalist

~ python libs/data/prepare_datalist.py --path "<folder_contain_dataset>" --output "/{path of file}/datalist.json" --stage "train" --split 'true'

# For training

configs\exp.json
{
    "model_name": "dynunet", //one in [segresnet, dynunet, vnet, swinunetr, dynunet_dda]",
    "att": [],  // Only use if model_name is dynunet_dda else []" 
    "project": "3dbrains",
    "model_trained": "/kaggle/input/3da-boe3wczn/3DDucknetAttention/src/results/best_metric_model.pth",  //null for training stage, trained path for testing stage",
    "reset_epoch": false,
    "datalist": "configs/datalist.json",
    "in_channel":	4,
	"out_channel":	3,
    "config":{
        "loss": "mse",
        "max_epochs": 120,
        "name":"dda_+",
        "lr":3e-4,
        "tmax": 30,
        "results_dir":"results", //dir of outputs",
        "log": true, //true if you want show on your wandb",
        "step_val": 1
    }
}

# Training:

~ python seg_train.py --input <your exp.json file>

# Predict
3D Dual-Domain Attention
Fill model_trained in exp.json then run

~ python libs/data/prepare_datalist.py --path "<Your folder contain dataset>" --output "/{path of file}/datalist.json" --stage "test" 

~ python 3d_dda.py --input <your exp.json file>