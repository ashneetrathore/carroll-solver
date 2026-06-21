# :jigsaw: CARROLL SOLVER

## :open_book: OVERVIEW
Date: March 2023\
Developer(s): Ashneet Rathore

Carroll Solver is a program that solves [word ladders](https://en.wikipedia.org/wiki/Word_ladder), a puzzle invented by Lewis Carroll in which a start word is transformed to a target word by changing one letter at a time, with each step forming a valid word. For example, to get from *"ate"* to *"oat"*, one possible sequence of words is *ate → ape → apt → opt → oat*. Carroll Solver provides an efficient way to compute the ***shortest*** transformation sequences between any two dictionary words. Users can input a start word and a target word of the same length from the dictionary, and the program outputs the resulting sequence.

## :film_strip: DEMO
![Demo](demo.gif)

## :gear: HOW IT WORKS
Written in **C++**, the program loads a dictionary of words from a file and represents each word as a node in a search space, effectively modeling the puzzle as a **graph problem**. It explores one-letter transformations to reach the target word and uses a **custom priority-queue** to implement an informed **A\* (A-star) search**. Words are prioritized based on steps taken (defined as the Lewis Carroll distance) and estimated letters remaining to the target. This algorithm is more efficient than standard BFS (Breadth-First Search) or DFS (Depth-First Search), as it focuses on searching the most promising paths first. The dictionary and discovered words are stored in unordered sets for fast lookups, and a tree-based map tracks each word's predecessor to reconstruct the transformation path.

## :open_file_folder: PROJECT FILE STRUCTURE
```bash
carroll-solver/
│── app/
│   │── main.cpp              # App entry point and user input handling
│   │── convert.cpp           # Search algorithm and path construction logic
│   │── convert.hpp           # Public function declarations for word ladder operations
│   │── MyPriorityQueue.hpp   # Binary min-heap priority queue
│   └── runtimeexcept.hpp     # Custom exception class
│── words.txt                 # Valid word dictionary
│── README.md                 # Project documentation
│── .gitignore                # Ignored files
└── demo.gif                  # Demo GIF
```

## :rocket: SET UP & EXECUTION
**1. Clone the repository**
```bash
git clone https://github.com/ashneetrathore/carroll-solver.git
```

**2. Run the program**
```bash
cd carroll-solver/app
g++ -std=c++17 main.cpp convert.cpp -o app
./app
```

## :wrench: TRY IT OUT
> [!IMPORTANT]\
>The start and target words must be present in the dictionary, and there must be valid intermediate words in the dictionary connecting them. If not, no sequence will be found.

Here are some sample start and target words you can input:
| Start Word | Target Word |
|------------|-------------|
| ate        | eat         |
| putters    | hampers     |
| banking    | brewing     |
| boosted    | classes     |
| changes    | glasses     |
| changes    | smashed     |