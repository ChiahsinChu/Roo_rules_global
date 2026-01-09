When I say "set up a project" or use this document elsewhere:

1. Ask for the project name. Replace the following in all commands and files:

   1. `<project>`: the input project name
   2. `<pname>`: the string where whitespace and dashes in `<project>` are replaced with underscores
2. Complete the following tasks:

   1. Add a `.gitignore` file (use a template from https://github.com/github/gitignore)

      1. Use the Python template if no other language is specified
      2. Uncomment `.vscode` in the `.gitignore` file
      3. Add `.DS_Store` to the `.gitignore` file
      4. Add `.roo/` to the `.gitignore` file
   2. Add an empty `README.md` file
   3. Add `LICENSE` and `.license-header.txt` files (use a template and license identifier from https://spdx.org/licenses/)

      1. Example for `.license-header.txt`: `SPDX-License-Identifier: GPL-3.0-or-later` (replace `GPL-3.0-or-later` with the license identifier actually used)
      2. Choose `GPL-3.0-or-later` if no other license is specified
   4. Use the [template](./CITATION.cff) for `CITATION.cff`:

      1. Change `date-released` to the actual date
   5. Use the [template](./.pre-commit-config.yaml) for `.pre-commit-config.yaml`
   6. Take all yaml files from [repository](https://github.com/ChiahsinChu/gh_workflows) to `.github/workflows/`, but add `.disabled` as file name suffix.
   7. Set up Git for the project:

      ```bash
      git init
      git add .
      git commit -m "first commit"
      git branch -M master
      git remote add origin git@github.com:ChiahsinChu/<project>.git
      ```
