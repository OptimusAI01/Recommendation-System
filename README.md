# Collaborative Filtering Movie Recommender System 🎬

[![Python Version](https://img.shields.io/badge/Python-3.7+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

## Project Overview

This project implements and compares two fundamental collaborative filtering (CF) techniques – User-Based Collaborative Filtering (UBCF) and Item-Based Collaborative Filtering (IBCF) – to build a movie recommendation system.  The system provides personalized movie suggestions based on user preferences and item characteristics, leveraging the power of historical rating data. This project aims to demonstrate the core principles of CF, evaluate the performance of these methods, and provide insights into the construction and evaluation of recommender systems.

## Table of Contents

*   [Project Overview](#project-overview)
*   [Table of Contents](#table-of-contents)
*   [Dataset](#dataset)
*   [Methodology](#methodology)
    *   [User-Based Collaborative Filtering (UBCF)](#user-based-collaborative-filtering-ubcf)
    *   [Item-Based Collaborative Filtering (IBCF)](#item-based-collaborative-filtering-ibcf)
*   [Evaluation Metrics](#evaluation-metrics)
*   [Installation & Usage](#installation--usage)
    *   [Prerequisites](#prerequisites)
    *   [Installation](#installation)
    *   [Running the Notebook](#running-the-notebook)
*   [Results](#results)
    *   [User-Based CF Results](#user-based-cf-results)
    *   [Item-Based CF Results](#item-based-cf-results)
    *   [Comparative Analysis](#comparative-analysis)
*   [Project Structure](#project-structure)
*   [Future Improvements](#future-improvements)
*   [Contributing](#contributing)
*   [License](#license)
*   [Contact](#contact)

## Dataset

The project utilizes the [MovieLens 20M Dataset](https://grouplens.org/datasets/movielens/), a widely used dataset for recommendation system research. This dataset contains:

*   **Movies:**  Movie titles and associated metadata.
*   **Ratings:**  User ratings (on a scale of 0.5 to 5) for various movies.  This is the primary data used for CF.
*   **(Optional) Tags:** User-generated tags for movies.
*   **(Optional) Links:** Links to external movie databases (e.g., IMDB).

This project focuses primarily on the `ratings.csv` file for collaborative filtering.  The dataset's size and diversity provide a good testbed for evaluating the performance of recommendation algorithms.

## Methodology

This project explores two core collaborative filtering techniques:

### User-Based Collaborative Filtering (UBCF)

1.  **User-Item Matrix:** The project starts by creating a user-item matrix, where rows represent users, columns represent movies, and the values are the ratings provided by users for each movie. Missing values (unrated movies) are filled with 0, assuming a user has no preference for that movie.
2.  **Similarity Calculation (Cosine Similarity):**  Cosine similarity is computed between all pairs of users based on their rating patterns.  This metric measures the cosine of the angle between two user rating vectors, effectively capturing the similarity of their preferences.
3.  **Identifying Similar Users:** For a target user, the system identifies the *k* most similar users (neighbors) based on their cosine similarity scores.
4.  **Rating Prediction:**  For a target user and a movie they haven't rated, the system predicts the rating by taking a weighted average of the ratings given by the similar users for that movie. The weights are the similarity scores between the target user and the similar users.
5.  **Recommendation Generation:** The top-N movies with the highest predicted ratings for a user are recommended.

### Item-Based Collaborative Filtering (IBCF)

1.  **Item-User Matrix:** Creates an item-user matrix with movies as rows, users as columns, and ratings as values.
2.  **Similarity Calculation (Pearson Correlation):**  The Pearson correlation coefficient is used to compute the similarity between items (movies). Pearson correlation captures the linear relationship between the rating patterns of different items. This method is preferred in this context since it captures the rating styles differences better.
3.  **Identifying Similar Items:**  For a target movie, the system identifies the *k* most similar movies.
4.  **Rating Prediction:**  The rating for a target movie by a given user is predicted using a weighted average of the ratings the user has given to the similar movies.
5.  **Recommendation Generation:** The top-N movies with the highest predicted ratings for a user are recommended.

## Evaluation Metrics

The performance of the recommendation models is evaluated using the following metrics:

*   **Mean Absolute Error (MAE):**  MAE measures the average absolute difference between the predicted ratings and the actual ratings. A lower MAE indicates better prediction accuracy.
*   **Precision@K:**  Precision at K measures the proportion of recommended items (top K) that are relevant (e.g., rated above a certain threshold).  It indicates the accuracy of the recommendations.
*   **Recall@K:**  Recall at K measures the proportion of relevant items (e.g., rated above a threshold) that are successfully recommended (within the top K).  It reflects the ability to identify all relevant items.

## Installation & Usage

### Prerequisites

*   Python 3.7 or higher
*   A package manager like `pip` (usually installed with Python)

### Installation

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/BinarySkull/Movie-Recommendation-System.git
    cd Movie-Recommendation-System
    ```

2.  **Create a virtual environment (recommended):**

    ```bash
    python -m venv .venv
    source .venv/bin/activate  # On Linux/macOS
    # or
    .venv\Scripts\activate  # On Windows
    ```

3.  **Install dependencies:**


### Running the Notebook

1.  **Download the MovieLens Dataset:** Download the `movies.csv`, `ratings.csv`, `tags.csv`, and `links.csv` files from the MovieLens 20M dataset and place them in the same directory as the Jupyter Notebook.
2.  **Run the Jupyter Notebook:**

    ```bash
    jupyter notebook Rec_system.ipynb
    ```

3.  **Execute the cells:**  Run the cells in the notebook sequentially to execute the collaborative filtering algorithms and generate recommendations.

## Results

### User-Based CF Results

*   **MAE:** 0.838663
*   **Precision:** 0.20
*   **Recall:** 0.06
(Note: The precision and recall are only for the specific user you are trying the algorithm on.)

### Item-Based CF Results

*   **MAE:** 3.269363

### Comparative Analysis

The MAE values indicate the prediction accuracy of the models. A comparison shows that User-Based CF achieved a lower MAE of 0.838663, which suggests better prediction accuracy.  The Precision and Recall metrics provide insight into the effectiveness of the top-N recommendations, measuring the system's ability to recommend relevant movies. A detailed comparison and analysis of the recommendations generated by both approaches are available in the notebook.

## Project Structure

The project is organized as follows:

*   `Rec_system.ipynb`: The main Jupyter Notebook containing the Python code, data loading, model implementation, evaluation, and results.
*   `movies.csv`, `ratings.csv`, `tags.csv`, `links.csv`: The MovieLens dataset files.

## Future Improvements

Potential areas for improvement include:

*   **Hybrid Models:**  Combining UBCF and IBCF or integrating content-based features to improve recommendation accuracy.
*   **Dimensionality Reduction:** Applying techniques like Singular Value Decomposition (SVD) to handle sparsity and improve model performance.
*   **Cold Start Solutions:**  Implementing strategies for recommending items to new users or suggesting new items with no ratings.

## Contributing

Contributions are welcome!  If you'd like to contribute, please:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Commit your changes.
4.  Submit a pull request.

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT), Have Fun!

---
