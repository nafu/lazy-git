# lazy-git

## Overview

lazy-git is commands to use git lazily.

## Installation

1. Download lazy-git
2. Put it in ~/usr/local/lazy-git
3. Add the Directory to the Path

### 1. Download lazy-git

Download as a zip, or git

### 2. Put it in ~/usr/local/lazy-git

	cp -r ~/Downloads/lazy-git ~/usr/local/

### 3. Add the Directory to the Path

Add this line to .bashrc, .zshrc or something

	export PATH=~/usr/local/lazy-git/bin:$PATH

## Usage

### st, sta, stco, std, stv

	// git status -s
	st

		 M file1.txt
		 M file2.txt
		 M file3.txt

	// git add file1.txt
	sta 1
	// git add file2.txt
	sta 2
	// git add file3.txt
	sta 3

	// git checkout file1.txt
	stco 1

	st

		 M file2.txt
		 M file3.txt

	// git checkout file3.txt
	stco 2

	st

		 M file2.txt

	// git diff file2.txt
	std 1

	// vim file2.txt
	stv 1

### b, cm, ull, ush

	// git branch -a
	b

	// git commit -m "Commit comment"
	cm "Commit comment"

	// git pull origin master
	ull master
	// git pull origin feature
	ull feature

	// git push origin master
	ush master
	// git push origin production
	ush production

### d, dca, dh

	// git diff
	d

	// git diff --cached
	dca

	// git diff HEAD
	dh

### ch, chs

	// git cherry -v
	ch

	// git show `git cherry -v $1 | awk '{print $2}' | awk "NR==$2"`
	chs

### lg, lgg, lgr

	// git log --stat --pretty=format:'%Cblue%h %Cgreen%ar %Cred%an %Creset%s %Cred%d' | head
	// Includes GPG signature status: G (signed) or N (unsigned)
	lg

	// git log --stat --pretty=format:'%Cblue%h %Cgreen%ar %Cred%an %Creset%s %Cred%d'
	// Includes GPG signature status: G (signed) or N (unsigned)
	lgg

	// git log --graph --date-order --pretty=format:'%Cblue%h %Cgreen%ci %Cred%an %Cblue%m %Creset%s %Cred%d'
	// Includes GPG signature status: G (signed) or N (unsigned)
	lgr

### lga, lgap

	// Show only GPG-signed commits (defaults to staging/main/master..HEAD)
	lga
	lga <commit-range>

	// Show GPG-signed commits with patches
	lgap
	lgap <commit-range>

### lgu, lgup

	// Show only unsigned commits (defaults to staging/main/master..HEAD)
	lgu
	lgu <commit-range>

	// Show unsigned commits with patches
	lgup
	lgup <commit-range>

### lgsign

	// Interactively review and GPG-sign unsigned commits using rebase
	lgsign
	lgsign <base-branch>
