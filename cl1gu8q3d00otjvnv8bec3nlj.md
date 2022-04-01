## Github Action to Enable Auto Merge

Github recently added support for [automatically merging](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-auto-merge-for-pull-requests-in-your-repository) PR on checks completions. We can write a GitHub action to automate this process.

# Github Action Job

```
enable-automerge:
  runs-on: ubuntu-latest
  permissions: write-all
  steps:
    - name: automerge
      run: gh pr merge --auto --squash "$PR_URL" -t "$PR_TITLE" -b "$PR_BODY"
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        PR_URL: ${{ github.event.pull_request.html_url }}
        PR_TITLE: ${{ github.event.pull_request.title }}
        PR_BODY: ${{ github.event.pull_request.body }}
``` 
