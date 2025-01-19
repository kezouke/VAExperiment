# VAE Experiments with KL vs. Wasserstein Loss

## Introduction

This repository contains experiments with Variational Autoencoders (VAEs) using KL divergence and Wasserstein distance as regularization losses. 

## Table of Contents

- [Setup](#setup)
- [Project Structure](#project-structure)
- [Experiment Description](#experiment-description)
- [How to Run](#how-to-run)
- [Results](#results)
- [Future Work](#future-work)
- [Acknowledgments](#acknowledgments)
- [License](#license)

## Setup

### Prerequisites

- Python 3.8 or higher
- PyTorch
- ClearML for experiment tracking
- Matplotlib, Seaborn, and other dependencies as specified in the code

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/kezouke/VAExperiment.git
   cd VAExperiment
   ```

3. Set up ClearML credentials in .ipynb file:

   ```python
   %env CLEARML_API_ACCESS_KEY=YOUR_ACCESS_KEY
   %env CLEARML_API_SECRET_KEY=YOUR_SECRET_KEY
   ```

## Project Structure

- `README.md`: This file.
- `vae_experiment.ipynb`: The main notebook containing the experiment code.
- `weights/`: Directory to save trained models.
- `data/`: Directory to store the MNIST dataset.

## Experiment Description

### Model

- **VAE Architecture**:
  - **Encoder**: Two-layer fully connected network mapping input to latent space.
  - **Decoder**: Two-layer fully connected network reconstructing the input from latent space.
  - **Latent Dimension**: 10

### Loss Functions

- **KL Divergence Loss**:
  - Regularizes the latent distribution to match a standard Gaussian.
  
- **Wasserstein Loss**:
  - Uses a critic network to approximate the Wasserstein distance between the latent distribution and the prior.
  - Includes gradient penalty to enforce Lipschitz continuity.

### Training

- **Dataset**: MNIST handwritten digits.
- **Training Parameters**:
  - Batch size: 64
  - Learning rate: 1e-3
  - Epochs: 35

### Visualizations

- **Reconstructions**: Comparing original and reconstructed images.
- **Latent Space Visualization**: Using t-SNE to visualize the latent space.
- **Latent Distributions**: KDE plots of latent dimensions.
- **Interpolation**: Visualizing smooth transitions between digits in latent space.
- **Reconstruction Error**: Histogram of reconstruction errors.

## How to Run

1. **Train VAE with KL Loss**:

   - Uncomment and run the training cell in the notebook.
   - The model will be saved to `weights/vae_kl_divergence.pth`.

2. **Train W-VAE with Wasserstein Loss**:

   - Uncomment and run the training cell for the Wasserstein VAE.
   - The model and critic will be saved to `weights/vae_wass_distance.pth` and `weights/critic.pth`.

3. **Generate Visualizations**:

   - Run the corresponding plotting functions in the notebook.
   - Results will be displayed inline and saved as images.

## Results

Please read `report.md` to get insights from VAExperiment :) 

## Future Work

- **Hyperparameter Tuning**: Experiment with different latent dimensions, learning rates, and critic network architectures.
- **Advanced Losses**: Explore other forms of regularizers or hybrid losses.
- **Applications**: Use the trained VAEs for tasks like anomaly detection or data generation.

## Acknowledgments

- Inspired by the ClearML tutorial for experiment tracking.
- MNIST dataset courtesy of Yann LeCun and contributors.

## License

- This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
