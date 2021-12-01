<!-- omit in toc -->
# Essay

A repository with reference on a particular subject. General repository to reference documentation, dependencies and more for other repository projects.

- [Branches](#branches)
- [Usage](#usage)
  - [Git Submodule](#git-submodule)
  - [Git Subtree](#git-subtree)

## Branches

- [main](https://github.com/sentenz/essay/tree/main) represents the readme manual.
- [docs/guides](https://github.com/sentenz/essay/tree/docs/guides) contains the guidelines and conventions.
- [backup/fork](https://github.com/sentenz/essay/tree/backup/fork) contains an backup of used links in other branches.

## Usage

### Git Submodule

With git submodule it is possible to clone another repository into the own project and keep the commits separate.
The submodule repository is defined as a reference, so no files from this external repository are present in the own project repository. When cloning a project that uses submodules, you need to check out the files from the submodules in an additional step to make them available locally.

1. Add a Git Submodule

   ```bash
   git submodule add -b <branch> <remote-respoitory-url> <relativ-local-folder-path>
   ```

   Example:

   ```bash
   git submodule add -b docs/guides https://github.com/sentenz/essay.git docs/guides
   ```

2. Pull a Git Submodule

   ```bash
   git submodule update --init --recursive
   ```

3. Update a Git Submodule

   ```bash
   git submodule update --remote --recursive --merge
   ```

4. Remove a Git Submodule

   ```bash
   git submodule deinit <submodule>
   git rm <submodule>
   ```

   Example:

   ```bash
   git submodule deinit docs/guides
   git rm docs/guides
   ```

5. Fetch new a submodule commits

   ```bash
   cd <submodule>
   git fetch
   ```

   Example:

   ```bash
   cd docs/guides
   git fetch
   ```

### Git Subtree

With git subtree it is possible to nest one repository within another as a subdirectory. All files of the external repository will be added to the own repository as a copy with a own commit. The files are retained even if the external repository is deleted.

1. Add a Git Subtree

   ```bash
   git subtree add --prefix <relativ-local-folder-path> <short-name> <remote-branch> --squash
   ```

   Example:

   ```bash
   git subtree add --prefix github/google/styleguide https://github.com/google/styleguide.git gh-pages --squash
   ```

2. Update a Git Subtree

   ```bash
   git subtree pull --prefix <relativ-local-folder-path> <short-name> <remote-branch> --squash
      ```

   Example:

   ```bash
   git subtree pull --prefix github/google/styleguide https://github.com/google/styleguide.git gh-pages --squash
   ```
