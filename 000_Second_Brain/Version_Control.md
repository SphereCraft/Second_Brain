15/08/2024 0650

Status #idea

Tags:

# Version Control

**Intro to version control**
Version control is a system that help manage and track changes to code over time, it allows for the retrieval of earlier versions, tracks who made the changes, and help in managing the modifications made by multiply people. Version control is not just a tool, is a fundamental aspect of modern software development. The role of version control in software development is to track changes, firstly, ie when and why someone made changes. This is useful for debugging and understanding project evolution. Anther role of version control is collaboration, it allows many people to work on same project without overwriting each others work.

There are 3 concepts to version control system

1. Repository – a database storing a fore history of project files and revisions which will be used for code for infrastructure, pipelines, AWS will be stored.

2. Commit – a snapshot of your file at a particular point in time, along with a message describing the changes.

3. Branch – a parallel version of a repository, created to develop features, fix bugs or experiment with new ideas.

Three types of version control systems we need to be aware of

1. Local eg storing file copies in a different directories but on a local pc

2. Centralised (CVCS) – single [[server]] repository with all files, update and commit, easier to collaborate with teammates. Eg subversion

3. Distributed (DVCS) most popular – allows each user to have a fully fledged [[server]] repository on there PC, eg Git

writing commit messages need to be clear and descriptive to explain what has changed and why

committing changes to our branch frequently, commit changes to code often to avoid large, complicated changes in one go

Branching strategy, we want to use them effective for dutiable development, bug fixes and experimentation
# References
