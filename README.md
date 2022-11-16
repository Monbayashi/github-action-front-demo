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
