## 用了Git就回不去了
Git是什么？简单点说就是版本管理的工具，类似于SVN, CVS，但是比它们强大很多。
介绍请参照官方网站: http://git-scm.com/

##### Git 的基本命令:
      add        Add file contents to the index
      bisect     Find by binary search the change that introduced a bug
      branch     List, create, or delete branches
      checkout   Checkout a branch or paths to the working tree
      clone      Clone a repository into a new directory
      commit     Record changes to the repository
      diff       Show changes between commits, commit and working tree, etc
      fetch      Download objects and refs from another repository
      grep       Print lines matching a pattern
      init       Create an empty Git repository or reinitialize an existing one
      log        Show commit logs
      merge      Join two or more development histories together
      mv         Move or rename a file, a directory, or a symlink
      pull       Fetch from and integrate with another repository or a local branch
      push       Update remote refs along with associated objects
      rebase     Forward-port local commits to the updated upstream head
      reset      Reset current HEAD to the specified state
      rm         Remove files from the working tree and from the index
      show       Show various types of objects
      status     Show the working tree status
      tag        Create, list, delete or verify a tag object signed with GPG



### Git flow(简单点理解就是对git branch使用的一些约定):
![Git flow 流程图](http://nvie.com/img/2009/12/Screen-shot-2009-12-24-at-11.32.03.png)

##### Git flow 基本命令
### Initialization

To initialize a new repo with the basic branch structure, use:

		git flow init [-d]

This will then interactively prompt you with some questions on which branches
you would like to use as development and production branches, and how you
would like your prefixes be named. You may simply press Return on any of
those questions to accept the (sane) default suggestions.

The ``-d`` flag will accept all defaults.


### Creating feature/release/hotfix/support branches

* To list/start/finish feature branches, use:

  		git flow feature
  		git flow feature start <name> [<base>]
  		git flow feature finish <name>

  For feature branches, the `<base>` arg must be a commit on `develop`.

* To push/pull a feature branch to the remote repository, use:

  		git flow feature publish <name>
		  git flow feature pull <remote> <name>

* To list/start/finish release branches, use:

  		git flow release
  		git flow release start <release> [<base>]
  		git flow release finish <release>

  For release branches, the `<base>` arg must be a commit on `develop`.

* To list/start/finish hotfix branches, use:

  		git flow hotfix
  		git flow hotfix start <release> [<base>]
  		git flow hotfix finish <release>

  For hotfix branches, the `<base>` arg must be a commit on `master`.

* To list/start support branches, use:

  		git flow support
  		git flow support start <release> <base>

  For support branches, the `<base>` arg must be a commit on `master`.


##### 主要分支（master,develop）

Master 分支是当前服务生产环境的分支，相当于应用每一个的运行版本。
Develop 分支是下次发布版本的开发分支，这个分支的内容会是现在开发完成的内容。

##### 辅助分支 （feature, release, hotfix）

Feature 分支是每个人需要完成内容的独立分支，你开发的相当内容，都在这个分支上，开发完成后需要merge到Develop分支。
Release 分支是下次发布的内容，如果有bug修改完成后需要merge回develop跟master分支。
hotfix 分支是如果线上正在系统发现bug，临时开的一个分支，修改完成后需要分别merge回develop分支。


### 相关资料
##### git flow 资料:
http://nvie.com/posts/a-successful-git-branching-model/
http://ihower.tw/blog/archives/5140
https://github.com/nvie/gitflow


##### 跟git类似但是更加轻量级的SCM:
http://mercurial.selenic.com/ 有人做过对比，性能貌似不如git,但是它的命令更少一些，反过来理解git更强大也是可以的。

##### 提供git服务的网站:
http://www.github.com
https://about.gitlab.com/

##### git的客户端，可以选择一个适合自己的
http://git-scm.com/download/gui/mac

ps: 推荐一个mac版的markdown编辑器 [mou](http://25.io/mou/)
