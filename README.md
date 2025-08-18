### mainf1.py -> original graph + random walk augmented graph is fed to the contrastive learning model.
### mainf2.py -> original graph + centrality augmented graph is fed to the contrastive learning model.
### mainf3.py -> random walk augmented graph + centrality augmented graph is fed to the contrastive learning model.

# A Novel Contrastive Learning Framework for Signed Graphs

![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=flat&logo=pytorch&logoColor=white)
![DGL](https://img.shields.io/badge/DGL-blueviolet.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

This repository contains the implementation of a novel self-supervised contrastive learning framework for signed graph networks. We introduce and evaluate two innovative graph augmentation strategies—one based on **signed random walks** and another on **eigenvector centrality**—to learn robust, sign-aware node representations.

Our framework, which incorporates an advanced **joint training** methodology with an **intra-view contrastive loss**, achieves state-of-the-art performance on the link sign prediction task, rivaling the published SGCL model on the Bitcoin-Alpha benchmark.

---
## Key Features

* **Novel Augmentation Strategies**: Implements two new augmentation techniques tailored for signed networks:
    1.  **Signed Random Walk ($S^2$)**: Captures implicit, 2-hop structural relationships.
    2.  **Signed Eigenvector Centrality**: Reinforces the structural roles of influential positive and negative nodes.
* **Advanced Contrastive Learning**: Uses a sophisticated joint training objective that combines a supervised loss with both **inter-view** and **intra-view** contrastive losses to learn highly separable embeddings.
* **State-of-the-Art Performance**: Achieves a **Binary F1-Score of 97.35%** on the Bitcoin-Alpha dataset, demonstrating performance on par with existing state-of-the-art models.
* **Modular Experiments**: The code is structured to easily run and compare different augmentation strategies.

---
## Methodology & Experiments

We evaluate three distinct contrastive learning setups, each corresponding to a main script:

1.  **`mainf1.py`: Structural Augmentation**
    * Contrasts the **Original Graph** against a view augmented by **Signed Random Walks**. This tests the model's ability to learn from structural perturbations.

2.  **`mainf2.py`: Role-Based Augmentation**
    * Contrasts the **Original Graph** against a view augmented by **Signed Eigenvector Centrality**. This tests the model's ability to learn from perturbations based on node importance.

3.  **`mainf3.py`: Hybrid Augmentation (Most Advanced)**
    * Contrasts the **Random Walk** view against the **Centrality** view. This forces the model to learn features that are invariant to both structural and role-based changes, a powerful technique for robust representation learning.

---
## Results

Our best-performing model achieved the following results on the **Bitcoin-Alpha** dataset, demonstrating its competitiveness with the state-of-the-art SGCL model.

| Metric          | Our Model (Best) | SGCL Paper (SOTA) |
| :-------------- | :--------------- | :---------------- |
| **F1 (Binary)** | **0.9733** | 0.9686            |
| **F1 (Micro)** | **0.9493** | 0.9527            |

Precision: 0.9584

---
## Installation

To run this project, it's recommended to use a virtual environment.

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your_username/your_project_repo.git](https://github.com/your_username/your_project_repo.git)
    cd your_project_repo
    ```

2.  **Create and activate a virtual environment:**
    ```bash
    python3 -m venv sgcl_env
    source sgcl_env/bin/activate
    ```

3.  **Install the required libraries:**
    ```bash
    pip install -r requirements.txt
    ```
    *(You will need to create a `requirements.txt` file containing the following libraries)*:
    ```
    torch
    dgl
    pandas
    numpy
    scipy
    scikit-learn
    matplotlib
    seaborn
    ```

---
## Usage

1.  **Download the Datasets**: Make sure your signed network files (`soc-sign-bitcoinalpha.csv`, `epinions.txt`, etc.) are in the root directory of the project.

2.  **Run an Experiment**: To run one of the three main experiments, simply execute the corresponding Python script. Make sure the `DATA_PATH` variable in the script is set to the correct dataset.

    * **To run the Random Walk vs. Original Graph experiment:**
        ```bash
        python3 mainf1.py
        ```
    * **To run the Centrality vs. Original Graph experiment:**
        ```bash
        python3 mainf2.py
        ```
    * **To run the Random Walk vs. Centrality experiment:**
        ```bash
        python3 mainf3.py
        ```

3.  **Outputs**: The script will print the per-epoch progress and the final evaluation metrics to the console. The **Confusion Matrix** and **ROC Curve** plots will be saved as `.png` files in the project directory.

## Citing Our Work

If you use this code in your research, please consider citing:
