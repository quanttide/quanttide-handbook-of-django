# 项目版本管理

## django-project-version

https://github.com/DCOD-OpenSource/django-project-version

尝试接入过。遇到的问题包括：

- 暂不支持4.x。考虑到社区普遍没有支持4.x，回到了3.2.x的版本。
- 只支持当前分支的版本。我们的版本打在production分支，但是通常在本地的feature或者master分支操作，所有分支都需要识别版本号，在GitLab Flow下不太容易支持、或者我们没有找到更科学的GitLab Flow版本号管理的方式。
