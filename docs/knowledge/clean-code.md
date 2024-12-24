# Clean Code Practices for Java Interviews

## Intention-Revealing Names

The first principle of clean code is using clear, descriptive names. In interviews, this immediately shows your professional approach:
```
// Poor naming - What you should avoid
int d; // elapsed time in days

// Professional naming
int elapsedTimeInDays;
```

## Function Design Principles

```
// Common implementation seen in interviews
public List<int> getThem() {
    List<int> list1 = new ArrayList<int>();
    for (int x : theList) {
        if (x[0] == 4) {
            list1.add(x);
        }
    }
    return list1;
}

// Professional implementation
public List<Cell> getFlaggedCells() {
    List<Cell> flaggedCells = new ArrayList<Cell>();
    for (Cell cell : gameBoard) {
        if (cell.isFlagged()) {
            flaggedCells.add(cell);
        }
    }
    return flaggedCells;
}
```

## Error Handling and Edge Cases

```
public class RobustProcessor {
    public Result<Data, Error> process(Data input) {
        try {
            validateInput(input);
            return processValidData(input);
        } catch (ValidationException e) {
            logError(e);
            return Result.failure(new ValidationError(e.getMessage()));
        }
    }
}
```

## Data Processing Example

```aidl
public class DataProcessor<T, R> {
    private List<Function<T, R>> pipeline = new ArrayList<>();

    public void addStep(Function<T, R> step) {
        pipeline.add(step);
    }

    public List<R> process(List<T> input) {
        List<R> result = new ArrayList<>();
        for (T item : input) {
            for (Function<T, R> step : pipeline) {
                result.add(step.apply(item));
            }
        }
        return result;
    }
}
```