# Automated Deadlock Detection Tool 🔄🚫

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![Version](https://img.shields.io/badge/version-1.0.0-green.svg) ![Status](https://img.shields.io/badge/status-active-success.svg)

A web-based interactive tool for visualizing and detecting deadlocks in resource allocation systems. This tool allows users to model processes and resources, simulate allocation and request matrices, and automatically detect circular wait conditions (deadlocks) using a resource allocation graph.



[Image of Resource Allocation Graph Example]


## 📋 Table of Contents

* [Features](#-features)
* [Demo](#-demo)
* [Technologies Used](#-technologies-used)
* [Getting Started](#-getting-started)
    * [Prerequisites](#prerequisites)
    * [Installation & Usage](#installation--usage)
* [How to Use](#-how-to-use)
* [How It Works](#-how-it-works)
* [Project Structure](#-project-structure)
* [Contributing](#-contributing)
* [License](#-license)
* [Contact](#-contact)

## ✨ Features

* **Dynamic System Configuration:** Easily add or remove processes and resources with a single click.
* **Interactive Input Matrices:**
    * **Allocation Matrix:** Define which resources are currently held by which processes.
    * **Request Matrix:** Define which resources are currently being requested by processes.
* **Visual Resource Allocation Graph (RAG):**
    * Uses **Vis.js** to render a dynamic, force-directed graph.
    * **Blue Solid Arrows:** Represent allocated resources (Process → Resource).
    * **Red Dashed Arrows:** Represent requested resources (Resource → Process).
* **Automated Deadlock Detection:** Instantly analyzes the graph for cycles (circular waits) using a Depth First Search (DFS) algorithm.
* **Visual Feedback:** Clear, color-coded indicators for "Safe" vs. "Deadlock" states.
* **Resolution Strategies:** Provides standard OS strategies (Preemption, Termination, etc.) when a deadlock is found.

## 🚀 Demo

> Experience real-time deadlock detection without installing any complex software. Just open the HTML file and start modeling!

## 🛠 Technologies Used

This project is built using standard web technologies, ensuring compatibility across all modern devices and browsers.

* **HTML5:** Semantic markup and structure.
* **CSS3:** Responsive design with Flexbox, Grids, and CSS Variables for theming.
* **JavaScript (ES6+):** * Core logic for graph traversal (DFS).
    * DOM manipulation for dynamic tables.
    * State management for matrices.
* **[Vis-Network](https://visjs.org/):** A dynamic, browser-based visualization library used to render the Resource Allocation Graph (loaded via CDN).

## 🏁 Getting Started

### Prerequisites

You do not need any backend server (Node.js, Python, etc.) to run this tool. 
* A modern web browser (Chrome, Firefox, Safari, Edge).
* An active internet connection (required to load the Vis.js library via CDN).

### Installation & Usage

1.  **Clone the Repository:**
    Open your terminal or command prompt and run:
    ```bash
    git clone [https://github.com/Asdaqkhan/Automated-deadlock-detector-tool.git](https://github.com/Asdaqkhan/Automated-deadlock-detector-tool.git)
    ```

2.  **Navigate to the Directory:**
    ```bash
    cd Automated-deadlock-detector-tool
    ```

3.  **Run the Tool:**
    Simply open the `index.html` file in your web browser.
    * **Windows:** Double-click the file or Right-click > Open with > Google Chrome.
    * **Mac/Linux:** `open index.html` or `xdg-open index.html`.

## 📖 How to Use

1.  **Setup System Size:**
    * Use the input fields to set the initial number of **Processes** and **Resources**.
    * Click **Apply Changes** to reset the tables.
    * Alternatively, use the **+ Add Process** or **+ Add Resource** buttons for incremental changes.

2.  **Fill the Matrices:**
    * **Allocation Matrix:** Enter the number of instances of a resource currently held by a process.
    * **Request Matrix:** Enter the number of instances a process is waiting for.
    * *Note: The graph updates automatically as you type!*

3.  **Analyze:**
    * Click the green **Detect Deadlock** button.
    * The tool will highlight if the system is **SAFE** or in a **DEADLOCK**.
    * If a deadlock is found, suggested resolution strategies will appear below the result.

4.  **Reset:**
    * Use the **Clear All** button to wipe all data and start fresh.

## 🧠 How It Works

The tool uses the **Resource Allocation Graph (RAG)** method for deadlock detection:

1.  **Graph Construction:**
    * **Nodes:** Processes (Blue Squares) and Resources (Red Ellipses).
    * **Edges:**
        * **Allocation Edge ($P_i \to R_j$):** Process $P_i$ holds resource $R_j$.
        * **Request Edge ($R_j \to P_i$):** Process $P_i$ is waiting for resource $R_j$.

2.  **Cycle Detection:**
    * When you click "Detect Deadlock", the JavaScript engine runs a **Depth First Search (DFS)** algorithm.
    * It maintains a `visited` set and a `recursion stack`.
    * If the DFS encounters a node that is already in the current recursion stack, a **cycle** is detected.
    * In this model, a cycle represents a **Circular Wait**, which is a necessary condition for a deadlock.

## 📂 Project Structure

```text
Automated-deadlock-detector-tool/
│
├── index.html       # The main application file containing HTML, CSS, and JS
├── README.md        # Project documentation
└── .gitignore       # (Optional) Git ignore file
