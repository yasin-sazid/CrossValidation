# Image Classification Training and Validation Components

A Java project exploring how image datasets and reference masks can be organized for training and held-out evaluation. The implementation focuses on RGB-based skin classification and the data preparation that supports it.

## Data flow

```text
Image directory + mask directory
                 |
          InputProcessing
                 |
             Randomizer
           /               Training pairs     Held-out pairs
          |
    MachineLearning
          |
 RGB skin/non-skin statistics
          |
      ImageProcessor
```

## Implementation highlights

- `FolderToFiles` enumerates files from an input directory.
- `InputProcessing` brings image and mask collections into the preparation workflow.
- `Randomizer` selects approximately one tenth of the original images for a test partition and matches masks by the first four filename characters.
- `Training` reads image/mask pairs and accumulates skin and non-skin RGB counts.
- `MachineLearning` coordinates training files, while `ImageProcessor` derives the trained RGB table.

The design separates file discovery, partitioning, pixel processing, and training coordination into dedicated classes.

## Explore the project

Open `CrossValidation/` as a Java project and mark `src/` as its source root. The implementation uses the JDK's file, image, and collection APIs. Begin with [InputProcessing.java](CrossValidation/src/othersPackage/InputProcessing.java) to trace directory preparation and [Randomizer.java](CrossValidation/src/othersPackage/Randomizer.java) to inspect the split and mask matching logic.

For component-level experimentation, provide image and mask directories with corresponding filename prefixes, then use the training and partition accessors in an IDE or Java driver. The repository's `mainPackage.MainClass` serves as the console entry-point scaffold.

## Technical focus

Paired dataset handling, randomized holdout selection, pixel-level class statistics, and modular training components demonstrate the supporting engineering behind an image classification experiment.
