# 3DDucknetAttention

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
