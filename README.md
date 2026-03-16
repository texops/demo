# TexOps Demo

Try the [tx](https://github.com/texops/tx) CLI in a browser-based GitHub Codespace — no local installation required.

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/texops/demo)

## Getting Started

1. Click the badge above to open this repo in a Codespace. Wait for the container to finish building — `tx` is installed automatically.

2. Log in to your TexOps account:

   ```
   tx login
   ```

3. Initialise the project (accept the defaults: texlive:2021, pdflatex):

   ```
   tx init
   ```

4. Build the document:

   ```
   tx build
   ```

   Once the build completes, `testmath.pdf` appears in the working directory.

## What happened?

When you ran `tx build`, the CLI uploaded `testmath.tex` to the TexOps cloud service, compiled it with the TeX Live distribution you chose during `tx init`, and downloaded the resulting PDF back to your Codespace. The entire LaTeX toolchain runs remotely — nothing is installed locally.

## Learn More

- https://github.com/texops/tx — source code
- https://texops.dev — documentation
