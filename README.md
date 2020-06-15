# find-changed-files
A github action to return a list of changed files using grep

```yaml
...:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v1
        with:
          node-version: 9.8.0
      - name: Install
        run: npm ci
      - name: Run Find changed files.
        id: changed_files
        uses: jackton1/find-changed-files@v1
        with:
          files: "test.png, new.txt"
      - name: Perform action when files change.
        if: steps.changed_files.outputs.files_changed == 'true'
        run: |
          echo "Do something when files have changed."

```


## Inputs

|   Input       |    type    |  required    |  default                    |  description               |
|:-------------:|:-----------:|:-------------:|:-------------------------:|:--------------------------:|
| token         |  `string`   |    `false`    | `${{ github.token }}`     | github action or PAT token |
| files         |  `string`   |    `false`    |                           | Comma separated list of files to check for changes during workflow execution |
