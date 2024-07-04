# docker-assignment

A simple exercise for using the Docker platform

## Working with the SmartShark dataset

SmartShark is a dataset with data on the evolution of a set of open source projects. For each project the dataset includes information about all commits, diffs for each commits as well as metrics, refactorings, bugs, issues etc.

Working with the [SmartShark](https://smartshark2.informatik.uni-goettingen.de/) dataset requires restoring a MongoDB database back up file to the researchers local development environment. The inspection of the database contents after its restore requires an appropriate front-end application and [mongo-express](https://github.com/mongo-express/mongo-express) is a good alternative.

Experimentation with the dataset and development of appropriate analysis procedures can be supported with a distribution of [Jupyter Notebook](https://jupyter.org/).
