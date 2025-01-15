# Conclusion

Congratulations! You did it! You were able to convert a ML experiment with a
traditional approach to a well-defined, well-documented workflow that can scale
and serve a model to the outside world!

Let's take the time to make a summary of what you have done.

## Summary of what you have done

- [x] The model can be reproduced

Thanks to DVC, the steps to create the model are documented and can be executed
in order to reproduce the model.

- [x] The experiment can be executed on a clean machine

Thanks to the CI/CD pipeline, the experiment can be executed on a clean machine.
Erasing the "but it works on my machine" issue.

- [x]  The changes done to a model can be tracked

Thanks to DVC and CML, the changes done to a model can be tracked, discussed and
visualized before merging them.

- [x] The model can be used outside of the experiment context

Thanks to BentoML, the model can be served and be used outside of the experiment
context.

Happy learning! :)
