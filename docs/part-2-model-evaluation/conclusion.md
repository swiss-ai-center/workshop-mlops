---
title: "Part 2 - Conclusion"
---

# Conclusion

Congratulations! You did it!

In this second part, you were able to reproduce the ML experiment with DVC and
track model evolution with DVC.

The following diagram illustrates the bricks you set up at the end of this part.

```mermaid
flowchart TB
    dot_dvc[(.dvc)]
    dot_git[(.git)]
    data[data/raw] <-.-> dot_dvc
    workspaceGraph <-....-> dot_git
    subgraph cacheGraph[CACHE]
        dot_dvc
        dot_git
    end
    subgraph workspaceGraph[WORKSPACE]
        prepare[prepare.py] <-.-> dot_dvc
        train[train.py] <-.-> dot_dvc
        evaluate[evaluate.py] <-.-> dot_dvc
        data --> prepare
        subgraph dvcGraph["dvc.yaml (dvc repro)"]
            prepare --> train
            train --> evaluate
        end
        params[params.yaml] -.- prepare
        params -.- train
        params <-.-> dot_dvc
    end
```
