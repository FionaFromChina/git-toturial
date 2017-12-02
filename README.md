## git rebase -i的使用
### 场景
1. 开发时commit 交错。比如顺序可能为a/1, b/1, a/2, b/2
2. 将小的commit 合并，如，a/1 a/2 => a
2. 开发时可能有些commit并不需要，属于冗余提交，比如test, just for fun
3. 发现提交的commit不合适，没有说明清楚提交内容，需要进行拆分，比如a/3 and b/3


### 使用
```
git rebase -i // 会进入vim编辑模式，可以针对上述三种情况进行处理
// 1. 情况1， 可以直接在vim的commit log里面调换顺序，保存后可以发现commit log已经发现改变
// 2. 情况2， 将pick改为s，可将两个commit进行合并，保存时填写新的commit message
// 3. 情况3， 直接在编辑模式删除不需要的commit即可
git reset --soft HEAD^ // 4. 情况4， 需要撤销提交，如果是最后一次提交，可使用HEAD^, 回退到提交前的状态，重新分次进行提交。
```

关于HEAD~ 和HEAD ^的区别，见git-head.txt的说明。

