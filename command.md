# GIT команди
## 1.git commit (та супутні команди)
**git status** - прегляд поточного статусу репозиторію;

__git add__ - додати файли у зону , що відслідковується ("staged" підготовлений)
```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
```


**git commit -m "_Коментарій комміту_"** - зробити комміт(знімок) та закоментувати його , що саме ви зробили;
```
$ git commit -m "My first commit"
[master 78276cd] My first commit
 1 file changed, 37 insertions(+), 1 deletion(-)
```
**git commit -a -m "_Повідомлення про створення комміта та застосовані зміни_"** - ця команада заміняє і виконує дві команди 
`git add ` та `git commit -m "Коментарій до комміту"`. Але ця команде не додає новостворені файли (untracked). Працює тільки з модифікованими(modified) файлами.

__git commit --amend -m "Новий коментарій до комміту"__ - доповнює останній комміт та додає до нього "свіжі" зміни. А також новий коментарій до комміту . `Новий комміт не створюється.`

```
$ git commit --amend -m "Done 28.09.2021"
[master 5edc296] Done 28.09.2021
 Date: Tue Sep 28 16:12:54 2021 +0300
 2 files changed, 198 insertions(+), 28 deletions(-)
 rewrite README.md (82%)
```


**git log** - історія коммітів;
```
commit a3dbc9b8120db69bd03901b06fe93ddddb0a33af (HEAD -> master, origin/master)
Merge: 7140911 5782f96
Author: T.Strikha <yaagresor@gmail.com>
Date:   Tue Sep 28 14:39:05 2021 +0300

    Commit_1

commit 5782f96e8a63e8ccfbb52604289208464cc35d88
Author: T.Strikha <yaagresor@gmail.com>
Date:   Tue Sep 28 14:00:24 2021 +0300

    Commit_2
```
___
## 2. git diff
__git diff__ - різниця між `невідслідковуємим трафіком "unstaged"` and та останнім коммітом (commit)
```
$ git diff
diff --git a/README.md b/README.md
index c61b308..ec1867e 100644
--- a/README.md
+++ b/README.md
@@ -1,34 +1,40 @@
 # GIT команди

-__git add__ - add file to commite & get status "staged" підготовлений
+__git add__ - додати файли у зону , що відслідковується ("staged" підготовлений
)
+```
+$ git status
+On branch master
+Your branch is up to date with 'origin/master'.

+Changes to be committed:
+  (use "git restore --staged <file>..." to unstage)
+        modified:   README.md
+```

-**git commit** - status "committed" зафіксований

-**git commit -m "_Change file_** - do commit
```
**git diff --staged** - різниця між `відслідковуємим трафіком (staged)`
та останнім коммітом;

```
$ git diff --staged
diff --git a/README.md b/README.md
index c61b308..e9e8479 100644
--- a/README.md
+++ b/README.md
@@ -1,36 +1,76 @@
 # GIT команди
+## 1.git commit (та супутні команди)

-__git add__ - add file to commite & get status "staged" підготовлений
+__git add__ - додати файли у зону , що відслідковується ("staged" підготовлений
)
+```
+$ git status
+On branch master
+Your branch is up to date with 'origin/master'.

+Changes to be committed:
+  (use "git restore --staged <file>..." to unstage)
+        modified:   README.md
```


__git diff COMMIT_ID__ - різниця між актуальним станом репозиторія та вказааним ID комміта;
```
$ git diff 5782f96e8a63e8ccfbb52604289208464cc35d88
diff --git a/README.md b/README.md
index 5e78e84..166a932 100644
--- a/README.md
+++ b/README.md
@@ -1,27 +1,114 @@
-__git add__ - add file to commite & get status "staged" підготовлений
-<br>
-**git commit** - status "committed" зафіксований
-<br>
-__git diff --staged__ - difference between continue "staged" file and past stat
us(commit)
-<br>
+## 1.git commit (та супутні команди)
+**git status** - прегляд поточного статусу репозиторію;
```
____
## 3. git reset 
+ **HEAD** - поточний комміт , який є актуальним;

 + **HEAD~3** - переносимо актуальний комміт на 3 (три) комміти назад;

 + **HEAD^^** - переносимо актуальний комміт на 2 (два) комміти назад;

 **git reset** - видалити комміт та перевести всі записи з у `невіслудковуємий трафік` _(--mixed)_ режим по замовчуванню.

 **--soft** - режим reset що переводить інформацію з коміта у `відслідковуємий` трафік та видиляє сам коміт.

**--mixed** - режим reset що переводить інформацію з коміта у _невідслудковуємий_ трафік та видиляє сам коміт.

**--hard** - режим reset що `видаляє повністю`  всю інформацію до певного коміта.

 Приклад: __git reset --hard HEAD~2__  або  __git reset --hard  5782f96e8a63e8ccfbb52604289208464cc35d88__ 

 P.S. де  5782f96e8a63e8ccfbb52604289208464cc35d88 - ID комміта;
 ____
## 4. git checkout
__git checkout__ - викорстовується для `перегляду` (переміщення) актуального комміту та  між версіями окремих файлів ,а також гілками(branch);
__git checkout HEAD~3__- перегляд третього з кінця комміту;
```
git checkout HEAD~3
Note: switching to 'HEAD~3'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 91ab327 Checkout use
```
__git checkout master__- повернення до актуального ствну репозиторію ;
```
$ git checkout master
Previous HEAD position was 91ab327 Checkout use
Switched to branch 'master'
M       test1.txt
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
```
___
## 5. git clean 
 + __git clean -n__ - виведення списку `untracked` (невідслідковуємих) файлів , які будуть видалені;
 ``` 
$  git clean -n
Would remove file_1.txt
```
+ __git clean -f__ - видалення `untracked` (невідслідковуємих) файлів;
```
$ git clean -f
Removing file_1.txt
```
___
## 6. git remote (доступ до віддаленого реопозитороію)
+ __git remote add__ _origin_ (назва реопзиторію) `https://github.com/Zandalar0203/public90.git`_(адреса віддаленого репозиторію)_- додавання віддаленого репозиторію для роботи на локальній машині;
+ __git remote -v__ - відображення  списку існуючих віддаленних репозиторіїв;
```
$ git remote -v
origin  https://github.com/Zandalar0203/test_project.git (fetch)
origin  https://github.com/Zandalar0203/test_project.git (push)
public  https://github.com/Zandalar0203/public90.git (fetch)
public  https://github.com/Zandalar0203/public90.git (push)

```
+ __git remote remove__ `origin`(назва репозиторію) - видалення віддаленного репозиторію;

+ __git push  public `master`__(гілка репозитарію) - додавання (пушить) до віддаленого репозиторію всі комміти певної гілки.

```
$ git push  public master
Enumerating objects: 60, done.
Counting objects: 100% (60/60), done.
Delta compression using up to 8 threads
Compressing objects: 100% (50/50), done.
Writing objects: 100% (60/60), 8.59 KiB | 2.15 MiB/s, done.
Total 60 (delta 17), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (17/17), done.
To https://github.com/Zandalar0203/public90.git
 * [new branch]      master -> master
```
+ __git pull public `main`__ (гілка репозитарію) - запит на отримання коммітів з віддаленого репозиторію;

```
$ git pull public02 main
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 5 (delta 0), reused 5 (delta 0), pack-reused 0
Unpacking objects: 100% (5/5), 389 bytes | 38.00 KiB/s, done.
From https://github.com/Zandalar0203/desktop-tutorial
 * branch            main       -> FETCH_HEAD
 * [new branch]      main       -> public02/main
fatal: refusing to merge unrelated histories
```