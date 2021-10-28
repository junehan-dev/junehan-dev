Git submodules
--------------

- Nest git repos within main repo.
   - ``.gitmodules`` file at global directory.
   - files for repo link, just act like sym link.

Howto

   1. ``git submodule add git@github.com/someone/submodule.git``
   #. ``git submodule update --remode DMN``
   #. ``git rm -f Subtree-Docs-test``

Git subtree
-----------

Features

   - Alternative to git submodule to handle external dependencies
   - allow you to inject an external project into a sub-folder
   - can be used to extract a sub-folder as separate project

Check out https://docs.github.com/get-started for "using git" > "about git subtree merges" chapter.
