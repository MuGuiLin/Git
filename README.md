# Git
====

## ʲô�ǰ汾���ƣ�

�汾������ָ��������������и��ֳ�����롢˵���ĵ����ļ��ı�����й�������׷���ļ��仯����¼�ļ��ı��ʱ�䡢������ݡ��������ִ���˽��м�¼��ͬʱ��ÿһ���׶��Ա����������ֻ��һ���ļ��ı仯����Ӱ汾��ţ����㽫�����в����ض��׶εı����Ϣ�������ǻع�

## ʲô�� Git��

### �˹��汾������

ͨ���˹��ĸ�����Ϊ��������Ŀ�Ĳ�ͬ�׶ε����ݣ�����ʵ���һЩ�������ּ�������

- ���������׳���
- ���������ظ������ࣩ����

### �汾���ƹ���

ͨ��������������˹��汾������Ϊ

- �����ҹ���ǿ��
- ֻ��¼��ͬ�汾֮��仯�Ĳ���

### �����汾���ƹ���

- CVS
- SVN
- Git
- ����



## ��ô�����ģ�

���ȣ����ǵ����˽�������Ҫ����

- ״̬
- ����

### git �ļ���������

![lifecycle](.\assets\lifecycle.png)

### ״̬

ͬʱ��git ���ṩ�����֣�Ҳ����˵�����֣���ͬ�ļ�¼״̬

- ���޸ģ�modified��
- ���ݴ棨staged��
- ���ύ��committed��

��һ�������״̬

- δ׷�٣�Untracked��

### ����

git �ṩ��������ͬ�Ĺ�������������Ų�ͬ������

- ����Ŀ¼
- �ݴ�����
- Git �ֿ�

![areas](.\assets\areas.png)



## ��װ

https://git-scm.com/



## ����

����װ�� Git Ӧ�����ĵ�һ���¾�����������û��������ʼ���ַ�� ����������Ҫ����Ϊÿһ�� Git ���ύ����ʹ����Щ��Ϣ����������д�뵽���ÿһ���ύ�У����ɸ���

```bash
git config user.name "�������"
git config user.email "�������"
```

### -- global

ͨ�� `--global` ѡ���������ȫ��������Ϣ

```bash
git config --global user.name "�������"
git config --global user.email "�������"
```

### �������

```bash
# ��ӡ����config
git config --list
# ��ӡָ��config
git config user.name
```



## �����ֿ� - repository

����ϣ������ git �汾���Ƶ���ĿĿ¼��ʹ�� `git init` ��ʼ��

```bash
git init
```

���������һ����Ϊ `.git` ����Ŀ¼�������Ŀ¼�������ʼ���� Git �ֿ������еı����ļ������Ŀ¼Ҳ����������˵����������֮һ�����Ŀ¼Ҳ�� Git �������ݼ�¼�ĵط����ǳ���Ҫ����Ǳ�Ҫ����Ҫ���׸Ķ�



## ���������������

��һ����Ŀ�� Git ��ʼ���Ժ�ֻ�Ǳ�ʾ����ϣ��ͨ�� Git ������ǰ�������Ŀ�ļ��Ĳ�ͬʱ�ڰ汾��¼���������ʱ����Ŀ���Ѵ��ڵ��ļ��������Ժ��������ļ�����û�н���汾���ƹ���ģ������� `δ׷�٣�Untracked��` ��״̬



## �鿴���������ļ�״̬

`git status`

```bash
git status
```

�鿴�������е��ļ�״̬

### ����

#### git status ��ʾ����

```bash
git config --global core.quotepath false
```

#### �ն�����

�˵� -> ���� -> �ı� -> ���� / ����

���޸������ļ�

```
[gui]  
    encoding = utf-8  
    # �����ͳһʹ��utf-8  
[i18n]  
    commitencoding = utf-8  
    # log����
[svn]  
    pathnameencoding = utf-8  
    # ֧������·��
[core]
    quotepath = false 
    # status����·�������ǰ˽��ƣ�������˵����������ʾ�����ˣ�
```



## ��ӹ������ļ����ݴ���

`git add`

```bash
git add 1.txt
# ��Ӷ���ļ�
git add 2.txt 3.txt
# �������Ŀ¼
git add ./a
# ��Ӷ��Ŀ¼
git add ./b ./c
# ��������ļ�
git add .
```

### �����汾

`git commit`

���ݴ�����ĸĶ����ύ������ git �ֿ⣬Ҳ����Ϊ��ι�����һ����ĳ�������ض�����Ĺ�����Ϊһ���汾���������Ƕ���ļ��ı仯��

-   ÿ���ύͬʱ������һ�� 40 λ�Ĺ�ϣֵ����Ϊ�ô��ύ�汾��Ψһ id

#### �ύ��ע

ÿ���ύ����Ҫ��д��ע��Ϣ

```bash
git commit
# �����Ĭ�ϣ����Զ��壩���ı��༭��
```

#### �޸�Ĭ�ϱ༭��

```bash
git config core.editor notepad

# ��� vscode �༭�� - mac
# ͨ�� vim �򿪻������������ļ�
vim ~/.bash_profile
# ��ӻ�������
export PATH=/Applications/Visual\ Studio\ Code.app/Contents/Resources/app/bin:$PATH
# �����˳�
source ~/.bash_profile
# ���ԣ����ն���ֱ��ͨ������ code ���� vscode
git config --global core.editor "code --wait"
```

#### ���б�ע

```bash
git commit -m ��ע��Ϣ
```



## �鿴�ύ��־

`git log`

```bash
// ������ʽ
git log
// ��Ҫ��ʽ�����У�
git log --oneline
```



## �޸��ύ

`git commit --amend`

�޸����滻��һ�Σ��ύ���ڲ�����һ���µ��ύ�汾������½����޸ĵĴ���׷�ӵ�ǰһ�ε��ύ��

```bash
git commit --amend -m �ύ
```



## ɾ��

`git rm`

```bash
# �� git �ֿ��빤������ɾ��ָ���ļ�
git rm �ļ�

# ֻɾ�� git �ֿ��е��ļ�
git rm --cached �ļ�

# rm �Ժ���Ҫ commit ��β��������� rm ���������ݴ���
git commit -m ����
```



### ��������

`git reset`

#### ���ݴ����г�����������

```bash
// ���ݴ����г���һ��ָ���ļ�
git reset HEAD �ļ�����
// ���ݴ����й��곷�������ļ�
git reset HEAD .
```

#### ������ȿ������ڻ��˰汾

```bash
# ���˵�ָ���� commitID �汾
git reset --hard commitID
```



## �Ƚ�

```bash
# �Ƚ� ���������ݴ���
git diff �ļ� 
# �Ƚ� �ݴ����Ͳֿ�
git diff --cached [commitId] �ļ�
# �Ƚ� �������Ͳֿ�
git diff commitId filename
# �Ƚ� �ֿⲻͬ�汾
git diff commitId1 commitId2
```



## ��֧

���ǵĿ�����������Ϸ������Ĭ���������ߣ�master���Ͻ��п����ġ����ʱ�򣬻��и���֧������git ֧�����Ǵ�����֧��������Ŀ����

### �鿴��֧

```bash
git branch
```

### ������֧

```bash
git branch ��֧����
```

### �л���֧

```bash
git checkout ��֧����
# Ҳ����ʹ�� checkout -b ���½���֧
git checkout -b ��֧����
```

### ��֧�ϲ�

```bash
# B �ϲ��� A����Ҫ�л��� A ��֧
git merge ���ϲ���֧

# �鿴�Ѿ��ϲ��ķ�֧
git branch --merged
# �鿴δ�ϲ��ķ�֧
git branch --no-merged
```

### ɾ����֧

```bash
# �����֧Ϊδ�ϲ�״̬��������ɾ��
git branch -d ��֧����
# ǿ��ɾ��
git branch -D ��֧����
```



## �ϲ���¼

`rebase`

```bash
# �ϲ� HEAD ǰ�������ȼ�¼
git rebase -i HEAD~2
```

#### ~ �� ^

~ : ����

^ : ����

![1566209448773](assets/path.png)

#### rebase ����

```bash
# p, pick = use commit => ʹ��
# r, reword = use commit, but edit the commit message => ʹ�ã������±༭˵��
# e, edit = use commit, but stop for amending => ʹ��
# s, squash = use commit, but meld into previous commit => ʹ�ã����ϲ���һ��
# f, fixup = like "squash", but discard this commit's log message => ���� squash ����������������� Commit �� Commit message
# x, exec = run command (the rest of the line) using shell => ִ�нű�
# d, drop = remove commit => �Ƴ�
```

```bash
git rebase -i HEAD~3
# �����༭����������Ҫ�Ľ����޸ģ�Ȼ�󱣴�
# ���Ϊ r��s ����ٴε����༭�����޸��µ� commit message���޸�֮�󱣴�
```

>   �������һЩ���⣬����ͨ�� `git rebase --edit-todo` �� `git rebase --continue` �������±༭����



## �ϲ���ͻ

�е�ʱ�򣬲�ͬ�ķ�֧���ܻ��ͬһ���ļ����ݺ�λ���Ͻ��в����������ںϲ��Ĺ����оͻ������ͻ

-   �鿴��ͻ�ļ�
-   �޸���ͻ����
-   �ύ



## ��ǩ

�е�ʱ������ϣ����ĳһ���ض�����ʷ�ύ����һЩ��ǩ

### �½� tag

```bash
git tag -a v1.0.0 HEAD/commitId  fc80c6f
```

### �鿴 tag

```bash
git tag
```



## Эͬ����

�������еĲ������ǽ����ڱ��صģ��������ϣ�������Ŷ�Эͬ��������ô���ʱ�����Ǿ���Ҫ�� git �ֿ���Ϣ���Ŷ��е������˽��й���

-   �ֲ�ʽ - ���Ļ���ȥ���Ļ�

### github

����ע��һ���˺�

ʹ�� ssh ����



## SSH

https://help.github.com/cn/articles/connecting-to-github-with-ssh

https://help.github.com/cn/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

#### ���� SSH ��Կ

```bash
ssh-keygen -t rsa -C "zmouse@miaov.com"
```

#### ��Ӵ���

ʹ�� `ssh-add` �������û�������������ֶ�����

```bash
eval $(ssh-agent -s)
```

#### ��� ˽Կ

```bash
ssh-add ˽Կ·��
```

#### �� github ����ӹ�Կ

�������� -> ���� -> ssh -> ���

#### ����

```bash
ssh -T git@github.com
```

### git Զ��

#### ����

```bash
git remote add origin git@github.com:miaov-zmouse/kkb-test.git
```

#### �ύ��ͬ����Զ��

ͬ�����زֿ⵽Զ��

```bash
git push -u origin master
# -u �򻯺�������
git push origin master
```

#### Զ�̷�֧

```bash
# �ύ��Զ�̣���֧��
git push origin [���ط�֧����]:[Զ�̷�֧����]

# Զ���ȴ����÷�֧Ȼ����ȡ������
git checkout -b [���ط�֧����] origin/[Զ�̷�֧����]

# ��ȡԶ�̷�֧������
git pull origin [Զ�̷�֧����]:[���ط�֧����]

# �鿴Զ�ֿ̲�
git remote show origin

# �鿴���ط�֧
git branch

# �鿴Զ�̷�֧
git branch -r

# �鿴���з�֧
git branch -a

# ɾ�����ط�֧
git branch -d [���ط�֧����]

# ɾ��Զ�̷�֧
git push origin --delete [Զ�̷�֧����]
# or
git push origin :[Զ�̷�֧����]

# ����Ĭ���ύ��֧
git branch --set-upstream-to=origin/[Զ�̷�֧����] [���ط�֧����]
```





## ��չ�������� - git work flow 

![img](assets/gitflow.png)

## GUI ����

https://git-scm.com/download/gui/win

-   Sourcetree
-   other editor





Git �ʼ�
======

���ߣ����  
���ڣ�2019-05-09

> Git�ٷ��̳���ַ: [https://git-scm.com/book/zh/v2](https://git-scm.com/book/zh/v2)

> git --version 		//�鿴�汾



# Git�Ļ�������
#### ��git���������̡�:
>	Ӧ������git�ײ���������̣���������ӻ����޸����ļ�����add��Stage Area֮�����Ȼ�����ļ����ݴ�����ͬ��blob��
	
>	�������ύ֮�����ϴ���һ��tree�������Ҫ��blob�����ӽ�ȥ��֮���ٷ�װ��һ��commit�������ɱ����ύ��
	
>	�ڽ�������reset��ʱ�����ֱ��ʹ��git reset --hard xxxxx���Իָ���ĳ���ض��İ汾��
	
>	��reset֮��git��������commit�����id���ٵ��ҵ�tree�����
	
>	Ȼ�����tree�ҵ�blob�����֮��Բֿ���л�ԭ���������̶�����hash�Ͷ����ƽ��в���������gitִ��Ч�ʷǳ�֮�ߡ�


#### ��ʲô�ǰ汾�⡿:

	�汾�������ֿ⣬Ӣ����repository������Լ�����һ��Ŀ¼�����Ŀ¼����������ļ������Ա�Git����������ÿ���ļ����޸ġ�ɾ����Git���ܸ��٣��Ա��κ�ʱ�̶�����׷����ʷ�������ڽ���ĳ��ʱ�̿��ԡ���ԭ����

	1��git���������һ���ļ�ϵͳ��ÿcommit(commit ���� root(��) �ڵ�) һ�ξʹ���һ�ô��� tree ��tree���кܶ�blob��blob���൱��Ҷ�ӽڵ�洢�ļ�ֵ��

	2��û���ļ�Ҳ����û��blob�����Ŀ¼�ǲ��ᱻgit����ģ���ΪgitҪ���ļ����а汾��������û�б�Ҫ�Կ�Ŀ¼���ɶ���

	git log --all --graph
	
#### ������:
	�������� ����༭��
	HEAD��
	�ݴ����� add
	�汾�⣺ commit
	

#### ��git����ʹ�ý��� ��
	1�� ��ֹ�򼯳�(����)��ִ֧��push -f������

	2�� ��ֹ�򼯳�(����)��ִ֧�б����ʷ�Ĳ�����


#### ������user��Ϣ�� �°�װ��git��һ��Ҫ���е���С�������á�
����|ע��
----|----
git config --global user.name 'myName'|		
git config --global user.email 'myEmail'|	
git config --global|						//ȫ�� ����
git config --local| 						//���� ������
git config --system| 						//ϵͳ ��������

---
#### ���鿴����user��Ϣ��
	git config --list
	git config --list --local
	git config --list --blobal
	git config --list --system












# Git��������ʼ����ʽ��

---
#### ��һ�����ش�����ʽ����

**1���Ѵ���Ŀ������е���Ŀ��������Git����**

	1�����뵽Ҫ����Git�����Ŀ��ĸ�Ŀ¼��
	2���ڵ�ǰĿ¼�򿪣�����ڡ�
	3��ִ�� git init //��ʼ��git

**2��ȫ�µ���Ŀ���½�����Ŀֱ����Git����**

	1�������㳣���������Ŀ�����Ŀ¼��
	2��git init ��Ŀ����ע����ƴ����Ӣ�ģ����������ģ��� ���ڵ�ǰĿ¼�д���һ������ղ��������Ŀ���� ͬ�����ļ��С�
	3�������㴴���������ĿĿ¼�У��Ϳ��Խ�����Ӧ��git���ˡ�


**3������Զ�ֿ̲�**
	1��git remote add origin �ֿ��ַ

	�磺git remote add origin git@gitlab.smgtech.net:01810597/git_demo.git

	����Զ�̿��ǿյģ����ǵ�һ������master��֧ʱ��������-u������Git������ѱ��ص�master��֧�������͵�Զ���µ�master��֧������ѱ��ص�master��֧��Զ�̵�master��֧�������������Ժ�����ͻ�����ȡʱ�Ϳ��Լ����
	
	�磺git push -u origin master   �Ժ�Ϳ���ֱ���� git pull ����OK�ˡ�


---
#### ������Զ�̿�¡��ʽ����

	git clone url ��Ŀ��(�����ڱ����Զ���һ����֧�� ���� Ϊ��[��Զ��һ��������]Ҳ��) --branch ��֧��		//��֧�� ��¡Զ��git��Ŀ�ķ�֧

������˵������
	git clone --help			//������Ϣ
	git clone url Ĭ��master��֧		//��¡Զ��git��Ŀ   ��GitHub �� ����Ŀ�����Clone or Download ��ťѡ�� Use HTTPS ������Ŀ��ַ
	git clone url --branch ��֧�� 		//��֧�� ��¡Զ��git��Ŀ�ķ�֧
	


> ����git clone git@gitlab.smgtech.net:01810266/xuantishenbao.git --branch test  �� master


---
#### �����»�ȡ��ɾ�������ļ��� Git��Զ�ֿ̲����»�ȡ
	(1)��git fetch --all
	(2)��git reset --hard �� git reset --hard origin/test
	(3)��git pull








# Git�Դ�����ύ��ά����


---
#### �������ύ����ע���ύ��[����ڶ���Э��ʱ��һ��Ҫ ���� git pull ���� git push]

	git pull			
	git pull origin test		//��ָ����Զ�̷�������ȡ
	git pull --rebase		���Ƽ�ʹ�á�

**�����ύ��Զ�ֿ̲�Ĳ������磺**

### ��һ������ӣ����ݴ��������أ�:

	git add .			//���ļ����޸ģ��ļ����½�����ӵ��ݴ����� ���� Git���ݴ���
	git add -u 			//���ļ����޸ġ��ļ���ɾ������ӵ��ݴ�����
	git add -A			//���ļ����޸ģ��ļ���ɾ�����ļ����½�����ӵ��ݴ���(git add -A ��ͬ��git add -all)��
	git add *			//��Ӵ洢����

	git add �ļ���			//��Ӵ洢ָ���Ķ������ļ���ע��Ҫ�����ļ���·��Ŷ��, �ļ�Ҫ�Ӹ��ļ���׺��������ļ���Ŀ¼�м��� �ո� ������
	git add �ļ���1 �ļ���2...	//��Ӵ洢ָ���Ķ����Ķ���ļ� �м��ÿո�ֿ�


	������һ�����õ� git add . ���� git add -A 	//-A(-all)
	git add -A�����git add -u������ŵ� �� �����ύ���б�ɾ�������滻�����޸ĺ��������ļ��������ݴ�������git add -u ֻ�ܲ������ٹ����ļ�


���ļ�����Աȡ���

	1���Ƚ� ������(ûadd֮ǰ) �� �ݴ���(add�Ժ�) �����ļ��Ĳ���
		git diff						//��ָ���ļ�ʱ������ʾ���в�ͬ���ļ����綼û���������κ���ʾ����
		git diff -- index.html css/base.css			//ָ���鿴index.html��base.css�������ĵ��ݴ����� HEAD֮��Ĳ��죬��û����������ʾ����

	2���Ƚ� �ݴ���(add��) �� HEAD(ûadd) �����ļ��Ĳ���
		git diff --cached      ����	git diff ��staged  	//��ָ���ļ�ʱ������ʾ���в�ͬ���ļ����綼û���������κ���ʾ����
		git diff --cached -- index.html css/base.css		//ָ���鿴index.html��base.css������������ļ�֮���� �ո�������ĵ��ݴ����� HEAD֮��Ĳ��죬��û����������ʾ����



���ļ��ָ�������������Ҫ�ã�checkout���ݴ�������Ҫ�ã�reset����

	1�����ݴ���(add�Ժ�) �ָ�Ϊ �� HEAD��һ�����൱��ȡ��add�Ĳ���
		git reset HEAD			//��ָ���ļ�ʱ������ݴ������е��ļ��ָ���HEAD����������
		git reset HEAD -- index.html	//ָ��Ҫ�ָ����ļ�������ļ�֮���� �ո����

	2���ù��������ļ� �ָ�Ϊ �� �ݴ���һ��
		git checkout -- index.html	//ָ��Ҫ�ָ����ļ�������ļ�֮���� �ո����


���ļ��Ƚ� �� �ָ��ܽ᡿��
	git diff 			�ݴ����빤�����Ƚ�

	git diff --cached	�ݴ�����HEAD�Ƚ�

	git reset HEAD		�ݴ����ָ���HEAD

	git checkout		�ݴ������ǹ������޸� 


���ܽ᡿
	1���޸��˹��������ָ���git checkout 

	2��add���볷���� git reset HEAD 

	3��commit���볷���� git reset--hard hashֵ ��ע��һ��ִ�У��޷��ָ���



### ���������ύ�����汾��:

	git commit -m "����"		//�ύ���иĶ������ļ� ��������� ���汾�� [ִ���ύʱ��ϵͳ��Ҫ�������ύ��Ϣ������������ύ��Ϣ����Ϊ�ڿհ׵�״̬��ִ���ύ��ʧ�ܵġ�]
	git commit -am "����"		//�ύ���иĶ������ļ� ��������� ���汾�� ��-am ��ʾ û��ִ�� git add . Ҳ���ύ��
	
����ô�޸�����commit��messageע��--amend ���޸�һ������δpush֮ǰ�޸�commit��Ϣ��

	git commit --amend -m "����" 		//������(���)һ���ύ�� commit �޸�


����������ļ���commit�ύ ���˵�֮ǰ��ĳ���ύ��ע����ȷ���ã�������� ���ڲ�������Ϊgit reset --hard hashֵ �������һ��ȥ���Ͳ��ָܻ��ˣ������мǣ�������
	
	1��git log --all --graph	// ��ʾ�����ύ��־������ʾÿ���ύ��hashֵ������commit_id�������ڸ������ڻ���

	2��git reset --hard 970b99e2ce5 //���˵�970b99e2ce5����ύǰ��ע��ÿ���ύ����һ��Ψһ��hashֵ ��commit 970b99e2ce57f93130d66eb1daef33a8f506a182 ��ֻҪΨһ������һ���־Ϳ����ˣ�


	�� git reset ��������������
		1��--soft		// ���ֻ�ǰ� HEAD ָ��� commit �ָ�����ָ���� commit���ݴ��������������ֲ���

		2��--hard		// ����� �� HEAD�����������ݴ��������޸�Ϊ��ָ���� commit ��ʱ����ļ�״̬��--hard Σ�ղ�����

		3��--mixed		// ����ǲ���ʱ���Ĭ�ϲ������� HEAD���ݴ��� �޸�Ϊ ��ָ���� commit ��ʱ����ļ�״̬�����������ֲ���


���Ƚϲ�ͬcommit�ύ���ļ����졿
	1��git log --all --graph	// ��ʾ�����ύ��־������ʾÿ���ύ��hashֵ������commit_id�������ڸ������ڻ���

	2��git diff 970b99e2ce57f 8f59099ce643e2	//���в鿴 970b99e2ce57f�ύ �� 8f59099ce643e2�ύ�������ļ��Ĳ���

	2��git diff 970b99e2ce57f 8f59099ce643e2 -- index.html	//ָ���鿴 970b99e2ce57f�ύ �� 8f59099ce643e2�ύָ����index.html�ļ��Ĳ���

���Ƚϲ�ͬbranch��֧���ļ����졿
	git diff master dev 		//�鿴 master��֧ �� dev��֧�������в�����ļ�

	git diff master dev -- index.html	//ָ���鿴 master��֧ �� dev��ָ֧����index.html�ļ��Ĳ���

����
	1��git branch -av		// ��ʾ���з�֧������ʾÿ����֧��hashֵ������branch_id�������ڸ������ڻ���

	2��git diff d3ff58e dd9cc30 	//���в鿴 d3ff58e��֧ �� dd9cc30��֧�������ļ��Ĳ���

	2��git diff d3ff58e dd9cc30 -- index.html	//ָ���鿴 d3ff58e��֧ �� dd9cc30��ָ֧����index.html�ļ��Ĳ���
	



### �����������ͣ���Զ�ֿ̲�:
	git push -u origin test		//������ʼ�ύ ������֧ ��ע�����˲���-u�����Ժ�����ʱ��ֱ����git push ����git push origin master ��һ��Ϊ�˲������� ��
	git push -f 				//��ע������ֻ���Լ�һ�����ã���Ȼ�� push --force �Ķ���ȥ������Ϊ��git push -f��ʾ��ǿ�����͡���Ŀǰ�Լ������Ĵ�������͵�Զ�ˣ������ǣ��������ã�����
	git push					//���޸ĺ�Ϳ��������ύ(��� ��)






### ���ġ���Git�ı���:

�����õĴ���Э�顿:

����Э�� | �﷨��ʽ | ����˵��
-------|-------|-------
����Э��(1) | /path/iDitor.git | ��Э�顾linux�������أ� ��Э�鴫����Ȳ��ɼ�
����Э��(2) | file:///path/iDitor.git | ����Э�飨���أ� ����Э�鴫����ȿɼ��������ٶȱ���Э��Ҫ��
http/httpsЭ�� | http://gitlab.smgtech.net/01810597/iDitor.git | ����Э�飨Զ��: �û��������룩
sshЭ�� | git@gitlab.smgtech.net:01810597/iDitor.git | ����Э�顾��������á���Զ�̣���Կ SSH Key��


���鿴������Զ�ֿ̲���Ϣ��:
>   git remote					//�鿴������Զ�ֿ̲������

>	git remote -v				//�鿴������Զ�ֿ̲����ϸ��Ϣ
	
>	git remote show name 		//����Զ�ֿ̲�name����ϸ��Ϣ


�����(����)Զ�ֿ̲�Ĺ�����:
	Զ�ֿ̲������һ��Ĭ��Ϊ origin ����Ȼ�����������Ϊ���������ơ�
	ͨ�� git clone ������Ŀ������ʱ����Ŀ�ļ����е� .git Ŀ¼���ǰ汾��Ŀ¼��
	.git Ŀ¼�е� config �ļ�����Զ�ֿ̲�Ĺ������á�

>   git remote add origin <url>		//git_url Ϊ���Զ�ֿ̲�� url���ɲ��� http Э��� ssh��git�� Э��
 
 ���磺
>   git remote add zhineng file:///e/gitDemo/zhineng.git //ΪԶ�ֿ̲������zhineng


��ɾ��Զ�ֿ̲�Ĺ�����:
>	git remote remove <name>


���޸�Զ�ֿ̲�Ĺ�����
	���磬֮ǰ�������Զ�ֿ̲�ʹ�õ�Э���� http �����뽫������Զ�ֿ̲�� url ��Ϊ ssh Э��ġ�
	�޸Ĺ�����Զ�ֿ̲�ķ�������Ҫ��3�֡�

��1�֣�
>	git remote set-url origin <newurl>	//ʹ�� git remote set-url �������Զ�ֿ̲�� url

��2�֣�
	��ɾ��֮ǰ������Զ�ֿ̲⣬��������µ�Զ�ֿ̲������ע��Զ�ֿ̲�������Ƽ�ʹ��Ĭ�ϵ����� origin
	
>	git remote remove <name>	//ɾ��������Զ�ֿ̲�
>	git remote add <name> <url>	//����µ�Զ�ֿ̲����

��3�֣�
	ֱ���޸���ĿĿ¼�µ� .git Ŀ¼�е� config �����ļ���

>	git remote add name url 	//ΪԶ�ֿ̲������
>	git remote show name 		//��ʾԶ�ֿ̲�name����ϸ��Ϣ
	
	
	

	1���Ҹ�Ŀ¼ִ�� clone ����
	2����init����git�ֿ⣬Ȼ��ӱ������ݿ����remote����push���½��ֿ⣻����
	3����init����git�ֿ⣬Ȼ�����²ֿ����remote���ٰѱ������ݿ�fetch/pull���²ֿ⡣


�������ļ���.gitignore
	�½�һ����Ϊ.gitignore���ļ���ע���ֲ��ܱ䣬����Git�ǲ��ϵ�
	echo 'disc/' > .gitignore    // disc/ ��ʾ��disc���Ŀ¼��������������ݶ�������git����
	
	���� vi .gitignore �򿪱༭ �������Ҫ���Ե��ļ�
���磺
	# ���Ǻ��Ե�Ŀ¼
	disc/						//����disc���Ŀ¼������
	node_modules/				//����node_modules/���Ŀ¼������
	
	# ���Ǻ��Ե��ļ�
	*.exe
	*.out
	*.app
	
��ʱ��
	git status	�Ϳ���������.gitignore�ļ��У����Ե���ЩĿ¼���ļ��ˣ���������ӵ��ݴ����ȵȡ�������
	
�����ļ���Ŀ¼�����Եĺ���ģ�壬�ɲ���  [GitHub](https://github.com/github/gitignore)

���磺
``` C++
	#����GitHub�е�C++���Ե�.gitignore�ļ�
	
	# Prerequisites
	*.d

	# Compiled Object files
	*.slo
	*.lo
	*.o
	*.obj

	# Precompiled Headers
	*.gch
	*.pch

	# Compiled Dynamic libraries
	*.so
	*.dylib
	*.dll

	# Fortran module files
	*.mod
	*.smod

	# Compiled Static libraries
	*.lai
	*.la
	*.a
	*.lib

	# Executables
	*.exe
	*.out
	*.app
	*.i*86
	*.x86_64
	*.hex

	# Debug files
	*.dSYM/
	*.su
	*.idb
	*.pdb
```

��ɾ���ļ���
	 git rm �ļ���
���磺
	 git rm data.json


���ָ��ļ���
	git reset --hard HEAD
	git reset --hard		//���������е�Σ�� �������ݴ�������·����������б�����ᱻ�������









# Git��������Ĵ���
---
#### ���ڿ�������ʱ�����˽���������ô����

	1��git stash 	//���湤��Ŀ¼������״̬WIP�����ָ����ϴ��ύ��״̬��
	
ע��git stashĬ��������������ļ���
     	1��git���ٵĵ�δ��ӵ��ݴ������޸�
     	2����ӵ��ݴ������޸�

ע�����Ỻ�������ļ���
      1���ڹ���Ŀ¼�е����ļ�
      2�������Ե��ļ�
	
	2��git stash list	//�鿴stash�б� ������ʽ stash@{0}��stash@{1}....

	3��git stash apply	//�ָ���ʱ�洢������stash�б�
	3��git stash pop	//�ָ���ʱ�洢��ɾ��stash�б�

	4��git stash apply stash@{2} //ָ���ָ���ʱ�洢������stash�б�  Ĭ��ʱ��git stash apply = git stash apply stash@{0}
	4��git stash pop stash@{3} //ָ���ָ���ʱ�洢��ɾ��stash�б�


 git worktree add 


---
#### �������ͻ�� 
> **Git�ϲ�ʱ������ͻ������ȡ���ϲ� **

	1����Git�޷��Զ��ϲ���֧ʱ���ͱ������Ƚ����ͻ�������ͻ�����ύ���ϲ���ɡ�

	2�������ͻ���ǰ�Git�ϲ�ʧ�ܵ��ļ��ֶ��༭Ϊ����ϣ�������ݣ����ǵ�������֧���޸�һ���ļ�����˫����commit�󣬴�ʱ�ںϲ�mergeʱ �ͻᱨ����Git��<<<<<<<��=======��>>>>>>>��ǳ���ͬ��֧�����ݣ������㽫��Ҫ�Ĵ���ɾ������ git add �� git commit �����ͺ��ˡ�


�����ߡ���
	1�����ϲ���֧ʱ����������߳�ͻ����֧�Ա߻�����|MERGING���������
		Administrator@MuGuiLin MINGW64 /d/git/test/iditor (test|MERGING)

	2�������״̬����ʱ���ᵼ�º�����Ҫ�ٺϲ���ʱ����ʾ����

	3��git merge --abort  //ȡ����κϲ�
		
	4��git pull --rebase  //���


	ʹ������Ĺ�ϵ����������������

	git pull = git fetch + git merge
	git pull --rebase = git fetch + git rebase


	git rebase -skip	//���Գ�ͻ��
	
	ע�����master����֧���г�ͻ�������Ѽͽ���ˣ���ʱ������֧��test�ȣ�Ҫ��master����֧����һ������Ȼ�ύ��master����֧���ֻ��г�ͻ��


---
#### ������ͷָ�� HEAD detached at .....�� 

> ����ͷָ�룺 ��ָHEADͷû��ָ���Ӧ�κη�֧����������£�HEADͷ ���Ǻ�ĳ����֧����һ��ġ��磺git log �����commit a2b0cc55fdc09e4e7c2dc26fef871237f009f257 (HEAD -> test)��
	git checkout commitId������ַ���ͷָ����������������±Ƚ�Σ�գ���Ϊ���ʱ�����ύ�Ĵ���û�кͷ�֧��Ӧ���������л���������֧��ʱ��(����master��֧)�����׶�ʧ���룻
	���Ƿ���ͷָ��Ҳ������Ӧ�ó������������Լ������Ի��߲��Ե�ʱ����Է���ͷָ�룬���������û���õ�ʱ�������ʱ����������������ó������ã���ô�����½�һ����֧��ʹ�� git branch <�·�֧������> commitId

> ��������Դ����
* ���޸ı���򴴽��ļ�ʱ��һ�����ڻ���ĳ��branch����֧���½��еģ�����ͻ���� ����ͷָ�� ����������������л���֧git ckeckout branchNameʱ��֮ǰ���޸ı�� �� �ύcommit������ݾͲ��ᱻ���档��

> ���磺 
		1��git log --graph				//��ʾ�ύ��־
		2��git checkout  ac47b9946759e	//��HEADָ����һ��commit�ϣ���ʱ���� ����ͷָ���ˣ���Ϊ����ʱHEAD��û��ָ���֧�ģ� 
		
		Administrator@MuGuiLin MINGW64 /e/gitDemo ((ac47b99...))  //����������Ӧ���ǣ���master�� �� (dev) ��(test) �ȣ�����ָ��һ������ķ�֧�ģ�����ָ��commit_id�ġ�



> ������취��
* �����л���֧֮ǰ������ git branch �·�֧�� ��ǰ����ͷָ�롿���ǽ�û�кͷ�֧������commit������������

> ���磺
    git branch myNewFZ ac47b9946759e 	//������ͷ ac47b9946759e ��commit������һ����myNewFZ���·�֧�¾ͺ��ˡ�
      
�����
    ��û��ִ������ı����֧��������л�����ķ�֧�ˣ������ڷ���ͷ ac47b9946759e�޸ĵ����ݾͶ�ʧ�ˣ����� ��Ȼ����Ϊ����ͷ ac47b9946759e������û�þ�û���⣬��������������ˣ�����








# Git��֧����
---
#### ���鿴��֧��
����|ע��
----|----
git branch -l| 						//�鿴��ǰ���ĸ����ط�֧��
git branch -lv| 						//�鿴��ǰ���ĸ����ط�֧�� + �ύ��Ϣ
git branch -a| 						//�鿴���з�֧(�������غ�Զ��)
git branch -av|						//�鿴���з�֧(�������غ�Զ��) + �ύ��Ϣ


---
#### ��������֧��
		 git checkout -b ��֧��			//������֧
	
	�磺 git checkout -b test			//���Ǵ���һ����Ϊtest�ķ�֧��

> ÿ���ύ��Git�������Ǵ���һ��ʱ���ߣ�����ʱ���߾���һ����֧����ֹ��Ŀǰ��ֻ��һ��ʱ���ߣ���Git������֧������֧����master��֧��HEAD�ϸ���˵����ָ���ύ������ָ��master��master����ָ���ύ�ģ����ԣ�HEADָ��ľ��ǵ�ǰ��֧��

һ��ʼ��ʱ��master��֧��һ���ߣ�Git��masterָ�����µ��ύ������HEADָ��master������ȷ����ǰ��֧�Լ���ǰ��֧���ύ�㣺


> ÿ���ύ��master��֧������ǰ�ƶ�һ���������������㲻���ύ��master��֧����ҲԽ��Խ��


�����Ǵ����µķ�֧������devʱ��Git�½���һ��ָ���dev��ָ��master��ͬ���ύ���ٰ�HEADָ��dev���ͱ�ʾ��ǰ��֧��dev�ϣ�
	
	git checkout -b dev	//����-b������ʾ�������л�

> �����������ڿ�ʼ���Թ��������޸ĺ��ύ�������dev��֧�ˣ��������ύһ�κ�devָ����ǰ�ƶ�һ������masterָ�벻�䣺
	���ڵ��޸ľ�����dev����

���޸����dev��֧�Ĺ��������ǾͿ����л���master��֧��
	git checkout master


����������dev�ϵĹ�������ˣ��Ϳ��԰�dev�ϲ���master�ϡ�Git��ô�ϲ��أ���򵥵ķ���������ֱ�Ӱ�masterָ��dev�ĵ�ǰ�ύ��������˺ϲ���

>	git merge dev					//git merge�������ںϲ�ָ����֧����ǰ��֧��
���ߣ�	
	git merge --no-ff -m "�ϲ�������" dev		//����֧ʱ������--no-ff�����Ϳ�������ͨģʽ�ϲ����ϲ������ʷ�з�֧���ܿ��������������ϲ�����fast forward�ϲ��Ϳ����������������ϲ���

���磺
	git merge --no-ff -m '��master����֧�ϲ���dev��֧' master   //��master����֧�ϲ���dev��֧


> �ϲ��󣬽����ص�masterͬ����Զ��
	
	git push origin master


�Ϳ��Կ�����master��dev��֧�������ύ����ȫһ���ġ�

> ѧϰ��ַ��https://www.liaoxuefeng.com/wiki/896043488029600/900003767775424


---
#### ��ɾ����֧��
	git branch -d ��֧��             	//ɾ����֧
	git branch -D ��֧��             	//ǿ��ɾ����֧   -d ��ɾ���� -D ��ǿ��ɾ����
	
���磺
	git branch -D dev
	
ע�⣺
	����ɾ����ǰ�ķ�֧������
	
	
---
#### ���л���֧�� ע���л���֧ʱ .git/HEAD �ᷢ���仯���� cat .git/HEAD ����Ϳ��Բ鿴��
	git checkout -b test origin/test	//�״��л���test��֧
	git checkout -b master origin/master //�״��л���master ����֧
	git checkout test					//ֱ���л�
	git checkout master



#### ���ϲ���֧��
	
	git merge Ҫ�ϲ��ķ�֧��

���磺��B��֧�ϲ���A��֧��Ҫ���л���A��֧���ٺϲ�
	git checkout A
	git merge B
	
	git breanch --merged �����Ѻϲ��ķ�֧
	
	
#### ���ϲ���¼��
	git rebase


Git��������ʹ�÷�֧��

	�鿴��֧��git branch
	
	������֧��git branch <name>

	�л���֧��git checkout <name>

	����+�л���֧��git checkout -b <name>

	�ϲ�ĳ��֧����ǰ��֧��git merge <name>

	ɾ����֧��git branch -d <name>




# ��ز鿴���

#### ���鿴�ύ��ַ��
����|ע��
----|----
git remote -v						|//�鿴�ύ��ַ
git remote add origin �ύ��ַ		|//[����ύ��ַ]���ڱ��ش����� git init ��Ϊ������ύ��ַ�� ���� .gitĿ¼�µ�config�ļ��в鿴[remote "origin"]��
git remote set-url origin �ύ��ַ	|//[�޸��ύ��ַ]�� ������Ѿ���ӵ��ύ��ַ����ı��ύ��ַ
git remote rm origin 				|//[ɾ���ύ��ַ], 


---
#### ����ز鿴��ע��������gitk ���� ��ͼ�λ�����չʾ�汾�� ������ gitk --all
����|ע��
----|----
git config --list|  				//���������Ϣ (���س����²鿴��)
git status	|						//�鿴״̬��ע��ֻ��������һ���յ��ļ��У������������ļ�ʱֻ�Ǹı��Сд�� ��û��status״̬�ģ�������
git log|							//�鿴��ǰ��֧�ύ��ʷ��¼
git log	--oneline| 					//�鿴��ǰ��֧�ύ������ʷ��¼
git log -n3|						//�鿴��ǰ��֧���3�ε��ύ��ʷ��¼ ���ֿɸ� �磺1 2 3 4 5 6......
git log --graph|					//�鿴��ǰ��֧�ύ����ʷ��¼��ͼ�λ���ϸ��ʾ
git log --all --graph|				//�鿴���з�֧�ύ����ʷ��¼��ͼ�λ���ϸ��ʾ
git log --all -n5 --graph|			//��������ʹ�á� graphͼ�� 
git log --all --graph ��֧��|		//�鿴ָ����֧�ύ����ʷ��¼��ͼ�λ���ϸ��ʾ

>	�磺 git log --all --graph test		//���ǲ鿴 test ��֧�ύ����ʷ��¼��ͼ�λ���ϸ��ʾ


---
#### ���鿴 commit -> tree -> blob�� *�ύ -> ������ľ���Ŀ¼���ļ�:html,css,img�ȣ� -> �㣨��ľ���:html,css�ļ�������ݣ�����git ֻҪ������ͬ���ļ���ֻ��һ����blob�����ݹ�ϣֵһ��һ������¿�*

> cat ��ϣֵ ��ע����ϣֵ��git log ������ commit ������ǹ�ϣֵ�� ���Ƴ��Ȳ�����ֻҪ��Ψһ��ʶ���С�
		git cat-file -t	��ϣֵ			//�鿴����
		git cat-file -s ��ϣֵ 			//�鿴��С
		git cat-file -p ��ϣֵ 			//�鿴����
		
```html
	�����磺git log
		������£�
			commit a2b0cc55fdc09e4e7c2dc26fef871237f009f257 (HEAD -> test)
			Author: muguilin <��muguilin@foxmail.com>
			Date:   Wed May 8 15:48:34 2019 +0800
				�޸�public��ʽ�ļ�

			commit ede5c592f6671a08b3f66a16828168f53749bdbd (master)
			Author: muguilin <��muguilin@foxmail.com>
			Date:   Wed May 8 14:30:18 2019 +0800
				����ļ�

	
	Ȼ����: git cat-file -p ede5c592f6671a08b3f66
		������£�
			040000 tree 22c27110dc712bd6286c3bafbefb3ce353315462    css
			040000 tree ea776a5da02f807cb654cb959e7555b50f63d8cc    img
			100644 blob 30276005913a22a0d2a17954550982dbd4fea8cb    index.html
			100644 blob bb2fed3c907d64c3a7b0295a9a0d4331cc5b7a31    style.css
		
		
	�����磺 git cat-file -p 30276005913a22a0d2a17  //���Ǿ��ǲ鿴�����index.html�е�����
		������£�
			<!doctype html>
			<html>
				<head>
					<meta charset="utf-8">
					<title></title>
					<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
					<link href="css/mui.css" rel="stylesheet" />
				</head>
				<body>
					<script src="js/mui.js"></script>
					<script type="text/javascript">
						mui.init()
					</script>
				</body>
			</html>
```
	
	
	
---
# Dos ���ò�����

#### ��Dos ���ò����� ǰ�治�ü� git 
����|ע��
----|----
ipconfig|							//�鿴����״̬
Alt + F2|							//��һ���������
Alt + Enter|						//ȫ��
Win + �������� |						//��������λ�ã������μ�ͷȫ���л�
Win + Tab| 							//�л�����
exit |								//�˳������
clear|								//����
cls|								//����
pwd|  								//�鿴��ǰĿ¼
ls|  								//�鿴����Ŀ¼���ļ�
ls -all|							//�鿴����Ŀ¼���ļ�(�������ص�)
ll|									//�鿴����Ŀ¼���ļ� ���б�����
ll -all|							//�鿴����Ŀ¼���ļ� ���б�����
dir| 								//ͬ��
dir -all|							//ͬ��
du -sh *| 							//�鿴��ǰĿ¼�����ļ����ļ��� �Ĵ�С
du -h|								//�鿴�����ļ����ļ��� �Ĵ�С
df|									//�鿴�洢�ռ���Ϣ


---
#### ��ɱ�����̡�
����|ע��
----|----
ps					|				//��ʾ���������еĽ���	
kill 12345(���̺�)	|				//ɱ������
kill -KILL 123456	|				//ǿ��ɱ������
kill -9 123456  	|				//����ɱ������


---
#### ���½�Ŀ¼��
	mkdir Ŀ¼��


---
#### ���½��ļ���
	touch �ļ���							//�½�һ���ļ�
	vi �ļ���							//�½�һ���ļ�������༭״̬������ļ��Ѵ��ڣ���ֱ�ӽ���༭״̬��
	
	��vi�еĲ����� ��esc�� ������������
		:w ����
		:wq! ǿ�Ʊ����˳�
		:q �˳�
		:qa!ǿ���˳�
		
	echo '������Ҫд�������' > �ļ���    //�������ļ���д�����ݣ�ע�⣺д��Ḳ��֮ǰԴ�ļ��е����ݡ�

	��.wap�ļ���ɾ����
		1��vi -r �ļ��� ������ʾ���� D ɾ����
	 	2���������������������vim.exe ���̣�


---
#### ��������Ŀ¼���ļ���
	mv ���޸ĵ�Ŀ¼�����ļ��� �µ�Ŀ¼�����ļ���
�磺
	mv style.css base.css				//���ǽ�style.css�ļ������ָ�Ϊbase.css
	mv images img						//���ǽ�imagesĿ�����ָ�Ϊimg
	
>	��������ע�⡿�ļ�����/Ŀ¼����������
		����ԭ����git��Ҫ�޸��ļ�����/Ŀ¼��ʱ ���ı� ��д��Сд��ĸ�� ����ֱ�Ӹ��ģ���Ϊֱ�Ӹ��Ĳ����¼�������ִ�Сд��ĸ�� �� mupiao ��Ϊ MuPiao ����������ȵģ������� git add . ʱû�м�¼�������� git status�鿴��
		����������Ȱ�Ҫ�޸��ļ�����/Ŀ¼�� ��Ϊ��������˼���֣�Ȼ�� git add . �� git commit -m "����" ֮�� �ٸ�Ϊ����ĵ����֣��ٴ� git add . �� git commit -m "����" �� git push �����������͡�


---
#### ������Ŀ¼���ļ���

	cp �����Ƶ�·����/����+��׺�� Ŀ��λ��/


> **ע�� **
���Ҫ��Ŀ��λ�������¸��ļ������֣�*ֱ����Ŀ��λ��/���ļ���+��׺��*

__�磺__
	cp style.css public/css         		//���ǽ���ǰĿ¼�е�style.css�ļ� ���Ƶ� ��ǰĿ¼�е�publicĿ¼�µ�cssĿ¼��ȥ��
	cp style.css public/css/base.css	//���ǽ���ǰĿ¼�е�style.css�ļ� ���Ƶ� ��ǰĿ¼�е�publicĿ¼�µ�cssĿ¼��ȥ ����������Ϊbase.css��


#### ��ɾ��Ŀ¼���ļ���
����|ע��
----|----
rm -rf .git     	|				//ɾ��git��Ŀ
rm -r  Ŀ¼�����ļ���	|				//ɾ��ָ����Ŀ¼
rm -rf Ŀ¼�����ļ���	|				//ɾ��ָ����Ŀ¼




Administrator@MuGuiLin MINGW64 /d/git/test/iditor (test|MERGING)

#### ����¡һ����Ŀ�����һ���ģ����һ���ύ��
git clone git@gitlab.smgtech.net:01810597/iDitor.git
cd iDitor
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master




#### �������е���Ŀ�ύ��Զ��Git�ֿ⡿
����	   |  ע��
----|----
cd Ŀ¼��|		//������ĿĿ¼
git init|		//��ʼ��git
git remote add origin git@gitlab.smgtech.net:01810597/iDitor.git|	//���Զ�ֿ̲��ַ
git add |		//�����ύĿ¼���ļ�
git commit "����"|	//�������
git push -u origin master|	//��һ���ύ��Զ�ֿ̲� master ���û�������û��������룬��ʱ���Զ�������ʾ�򣬻������û��������롾����������ʱ�ǿ������ġ�




#### ������Git ��ʹ�ò���ϵͳĬ�ϵ��ı��༭��oΪNotepad++��
```javascript
git config --global core.editor Notepad++
```



#### ����ȡ����������ʹ�� Git ʱ��Ҫ��ȡ�����������ַ��������ҵ� Git �����ʹ���ֲ᣺

```javascript
$ git help <verb>
$ git <verb> --help
$ man git-<verb>

���磬Ҫ���� config ������ֲᣬִ��
$ git help config
```

