---
title: "Part 3 - Conclusion"
---

# Conclusion

Congratulations! You did it!

In this third part, you were able to move the model outside of the experiment
context. The model is now saved and loaded with BentoML. You can serve the model
locally.

The model is now ready to be used in production.

The following diagram illustrates the bricks you set up at the end of this part:

```mermaid
flowchart TB
    workspaceGraph <-....-> dot_git
    data[data/raw]
    subgraph cacheGraph[CACHE]
        dot_dvc[(.dvc)]
        dot_git[(.git)]
        bento_artifact[(Containerized
                        artifact)]
    end
    subgraph workspaceGraph[WORKSPACE]
        data --> code[*.py]
        subgraph dvcGraph["dvc.yaml"]
            code
        end
        params[params.yaml] -.- code
        code <--> bento_model[classifier.bentomodel]
        subgraph bentoGraph[bentofile.yaml]
            bento_model
            serve[serve.py] <--> bento_model
            fastapi[FastAPI] <--> |bento serve|serve
        end

        bentoGraph -->|bento build
                       bento containerize| bento_artifact
        bento_model <-.-> dot_dvc
    end
    subgraph browserGraph[BROWSER]
        localhost <--> |docker run|bento_artifact
        localhost <--> |bento serve| fastapi
    end
```

The main goal of the MLOps process is to ensure that the model is reproducible,
reliable and can be used in production. This goal is now achieved.
