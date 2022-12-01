# second-action-react-demo

```shell

git init

git add .

git commit -m 'inital commit'

# remoteを追加
# [UserName]はgithubアカウント名
git remote add origin https://[UserName]@github.com/Monbayashi/second-action-react-demo.git

# --set-upstream
git push --set-upstream origin main

```

## if 条件式

> step IF

```yml
- name: Test code
  id: run-tests
  run: npm run test
- name: Upload test report
  if: failure() && steps.run-tests.outcom == 'failure'
  uses: actions/upload-artifact@v3
  with:
    name: test-report
    path: test.json
```

> job IF

```yml
  report:
    needs: [lint, deploy]
    if: failure()
    runs-on: ubuntu-latest
    steps:
      - name: Output information
        run: |
        echo "..."
```

> cache IF

```yml
- name: Cache dependencies
  id: cache
  uses: actions/cache@v3
  with:
    path: node_modules
    key: deps-node-modules-${{ hashFiles('**/package-lock.json') }}
- name: Install dependencies
  if: steps.cache.outputs.cache-hit != 'true'
  run: npm ci
```

> エラーを無視して実行

```yml
- name: Test code
  continue-on-error: true
  id: run-tests
  run: npm run test
- name: Upload test report
  uses: actions/upload-artifact@v3
  with:
    name: test-report
    path: test.json
```

SourceTree 確認
