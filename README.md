# Snips NLU Intent Engine Model for Vehicles

This project provides a dataset and a pre-trained NLU Intent Engine model for vehicles, allowing users to control various aspects of their vehicle using natural language commands. The NLU Intent Engine is built using the Snips NLU (Natural Language Understanding) engine and is designed to understand and respond to specific intents related to dashboard controls, HVAC settings, and volume control.

## Features

The NLU Intent Engine supports the following intents:

- **HVAC Temperature:** Adjust the vehicle's HVAC system temperature by specifying the desired temperature in Celsius, such as "Set the temperature to 22 degrees Celsius."

- **HVAC Fan Speed:** Control the vehicle's HVAC fan speed using percentage values, e.g., "Increase the fan speed to 75 percent" or "Set the fan speed to 50 percent."

- **Volume Control:** Adjust the volume of the vehicle's audio system using commands like "Increase the volume," "Set the volume to 50 percent," or "Mute the sound."

## Dataset and Model

The Snips NLU engine uses a dataset to understand and recognize user intents. The dataset is structured into two files:

- **intents.yaml:** Contains the intent definitions, slots, and sample utterances for each intent.

- **entities.yaml:** Defines the entities used in the intents, including their values, synonyms, and matching strictness.

To train the NLU Intent Engine model, a pre-processing step is required to convert the dataset into a format compatible with the Snips NLU engine. Once the model is trained, it can be used to parse user queries and extract the intent and relevant slots for further processing.

## Getting Started

To set up the Snips NLU Intent Engine, follow these steps:

1. Clone this repository to your local machine.

2. Install and set up the [`snips-inference-agl`](https://github.com/malik727/snips-inference-agl) module on your local machine. This module is an extension of the original Snips NLU with upgraded Python support and is specifically designed for inference purposes only.

3. Once you have the [`snips-inference-agl`](https://github.com/malik727/snips-inference-agl) module installed, you can load the pre-trained model located in the model/ folder. This model contains the trained data and parameters necessary for intent extraction. You can use the following command to process commands and extract the associated intents:
    ```
    $ snips-inference parse path/to/model -q "your command here"
    ```

## Usage

Once the Snips NLU Intent Engine is set up and running, you can interact with it by speaking natural language commands related to the supported intents. The NLU Intent Engine will process the commands and perform the requested actions accordingly.

Here are a few example commands you can try:

- "Set the temperature to 24 degrees Celsius."
- "Increase the fan speed to 80 percent."
- "Increase the volume."
- "Set the volume to 60 percent."

## Customization

To customize the NLU Intent Engine for your specific use case, you can modify the dataset files `intents.yaml` and `entities.yaml` to add new intents, slots, or entity values. You need to re-generate the dataset if you modify `intent.yaml` or `entities.yaml`, for this purpose you need to install [`snips-sdk-agl`](https://github.com/malik727/snips-sdk-agl) module. This module is an extension of the original Snips NLU with upgraded Python support and is specifically designed for data pre-processing and training purposes only. 

After installation run the following command to generate the updated `dataset.json` file:
```
$ snips-sdk generate-dataset en entities.yaml intents.yaml > dataset.json
```

Then run the following command to re-train the model:
```
$ snips-sdk train path/to/dataset.json path/to/model
```

Finally, you can use the [`snips-inference-agl`](https://github.com/malik727/snips-inference-agl) module to process commands and extract the associated intents.
 
## Limitations

It's important to note that the NLU Intent Engine's capabilities are limited to the supported intents and entities defined in the dataset. It may not accurately recognize or handle queries outside the defined scope. You can always add more intents and entities to suit your specific requirements.
