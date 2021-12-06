<!-- omit in toc -->
# Essay

A repository with reference on a particular subject. General repository to reference documentation, dependencies and more for other repository projects.

With the exception of main, each branch represents a single project.

- [Branches](#branches)
  - [`main`](#main)
  - [`backup/fork`](#backupfork)
  - [`docs/guides`](#docsguides)
  - [`scripts/validate`](#scriptsvalidate)

## Branches

### `main`

The [main](https://github.com/sentenz/essay/tree/main) branch represents an baranch overview with a readme manual.

### `backup/fork`

The [backup/fork](https://github.com/sentenz/essay/tree/backup/fork) branch contains an backup of used links in other branches.

With git subtree it is possible to nest one repository within another as a subdirectory. All files of the external repository will be added to the own repository as a copy with a own commit. The files are retained even if the external repository is deleted.

Run the commands below from the top-level directory of the [backup/fork](https://github.com/sentenz/essay/tree/backup/fork) branch.

<!-- omit in toc -->
#### Backup

- Repository with Git Subtree
  1. Add a Git Subtree

     ```bash
     git subtree add --prefix <relativ-local-folder-path> <remote-respoitory-url> <remote-branch> --squash
     ```

     Example:

     ```bash
     git subtree add --prefix github/google/styleguide https://github.com/google/styleguide.git gh-pages --squash
     ```

- Website with wget
  1. Add a Website to resource file

     ```bash
      <https://website> >> .website
     ```

  2. Download the Websites from the resource file

     ```bash
      wget -q --mirror --convert-links --adjust-extension --page-requisites --no-parent -e robots=off --no-cookies -P website -i .website
     ```

<!-- omit in toc -->
#### Remove

<!-- omit in toc -->
#### Update

- Repository with Git Subtree
  1. Update a Git Subtree

     ```bash
     git subtree pull --prefix <relativ-local-folder-path> <remote-respoitory-url> <remote-branch> --squash
     ```

     Example:

     ```bash
     git subtree pull --prefix github/google/styleguide https://github.com/google/styleguide.git gh-pages --squash
     ```

- Website with wget
  1. Update the Websites from the resource file

     ```bash
      wget -q --mirror --convert-links --adjust-extension --page-requisites --no-parent -e robots=off --no-cookies -P website -i .website
     ```

<!-- omit in toc -->
#### Usage

### `docs/guides`

The [docs/guides](https://github.com/sentenz/essay/tree/docs/guides) branch contains the guidelines and conventions.

With Git Submodule it is possible to clone another repository into the own project and keep the commits separate. The submodule repository is defined as a reference, so no files from this external repository are present in the own project repository. When cloning a project that uses submodules, you need to check out the files from the submodules in an additional step to make them available locally.

Run the commands below from the top-level directory of your project.

<!-- omit in toc -->
#### Install

1. Add a Git Submodule

   ```bash
   git submodule add -b docs/guides https://github.com/sentenz/essay.git docs/guides
   ```

2. Pull a Git Submodule

   ```bash
   git submodule update --init --recursive
   ```

3. Status of a Git Submodule

   Check the status of a submodule:

   ```bash
   git submodule status
   ```

   The output should look like below:

   ```bash
   <sha> docs/guides (heads/docs/guides)
   ```

   If the output is empty, start from the beginning.

<!-- omit in toc -->
#### Uninstall

1. Remove a Git Submodule

   ```bash
   git submodule deinit docs/guides
   git rm --cached docs/guides
   ```

<!-- omit in toc -->
#### Update

1. Update a Git Submodule

   ```bash
   git submodule update --remote --recursive --merge
   ```

<!-- omit in toc -->
#### Usage

### `scripts/validate`

The [scripts/validate](https://github.com/sentenz/essay/tree/scripts/validate) branch contains the scripts for validation.

With Git Submodule it is possible to clone another repository into the own project and keep the commits separate. The submodule repository is defined as a reference, so no files from this external repository are present in the own project repository. When cloning a project that uses submodules, you need to check out the files from the submodules in an additional step to make them available locally.

Run the commands below from the top-level directory of your project.

<!-- omit in toc -->
#### Install

1. Add a Git Submodule

   ```bash
   git clone --sparse --filter=blob:none --no-checkout --depth 1 -b scripts/validate https://github.com/sentenz/essay.git scripts/validate
   git submodule add -b scripts/validate https://github.com/sentenz/essay.git scripts/validate
   git submodule absorbgitdirs
   ```
   
   Modify `.git/modules/scripts/validate/info/sparse-checkout`.
   
   ```bash
   git -C scripts/validate config core.sparseCheckout true
   echo 'validate/*' >> .git/modules/scripts/validate/info/sparse-checkout
   git submodule update --force --checkout scripts/validate
   ```

2. Pull a Git Submodule

   ```bash
   git submodule update --init --recursive
   ```

3. Status of a Git Submodule

   Check the status of a submodule:

   ```bash
   git submodule status
   ```

   The output should look like below:

   ```bash
   <sha> scripts/validate (heads/scripts/validate)
   ```

   If the output is empty, start from the beginning.

<!-- omit in toc -->
#### Uninstall

1. Remove a Git Submodule

   ```bash
   git submodule deinit scripts/validate
   git rm --cached scripts/validate
   ```

<!-- omit in toc -->
#### Update

1. Update a Git Submodule

   ```bash
   git submodule update --remote --recursive --merge
   ```

<!-- omit in toc -->
#### Usage
