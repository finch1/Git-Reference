# Git Is Distributed
Local repos can sync with other repos
<div>
    <img src="Fig A.png" alt="Distributed" style="max-width: 20%;"/>        
</div>

## Settings
- Name
- Email
- Default Editor
- Line Endings

## Global Settings
> git config --list -> # shows all config settings      
> git config --local --edit -> # to edit the file       
> git config --global --edit        
> git config --system --edit        

> git config --global user.name ""      
> git config --global user.email        
> git config --global core.editor "code --wait" -> # --wait = waits until editor is closed before saving settings"      
> git config --global -e -> # opens configs in default editor       

End of line feeds differe between Win, Lin, Mac
Win: \r\n = carriage return\line feed. Set to true
Lin & Mac: \n = line feed. Set to input

> git config --global core.autocrlf true

## Local settings
Effects the current repo
<div>
    <img src="Fig L.png" style="max-width: 20%;"/>
</div>

# Getting Started
> mkdir Repo        
> cd Repo       
> git init -> # initialises a new git repo

# Workflow Concept
<div>
    <img src="Fig B.png" style="max-width: 20%;">
</div>

After commit, staging area keeps last records. New *add .* compares changes and updates the staging area.

<div>
    <img src="Fig C.png" style="max-width: 20%;">
    <img src="Fig D.png" style="max-width: 20%;">
</div>

# Staging
> git add file1.txt file2.txt       
> git add *.txt     
> git add .     

<div>
    <img src="Fig E.png" style="max-width: 20%;">
</div>

## Renaming & Removing files
> git rm file1.txt -> # removes file from local dir **and** staging area in one command

> git mv .\file1.txt .\file01.txt -> # renames file in local dir **and** staging area in one command

<div>
    <img src="Fig F.png" style="max-width: 20%;">
</div>

## Ignoring files and folders - Prior to tracking

> code .gitignore -> # creates a file in the main repo using vscode

- A new dir was created
- git identified new dir as untracked
- .gitignore was created. ignore list added **before** files and folders **tracking**
- git identified what to ignore and only captured .gitignore

<div>
    <img src="Fig G.png" style="max-width: 20%;">
</div>

## Ignoring files and folders - After tracking

> git ls-files -> # shows files and folders in staging 

> git rm --cached -r [file/folder] -> # removes files and folders in staging 

# Remove and revert uncommitted Git changes
To remove all uncommited changes and revert their Git working tree back to the state it was in when the last commit took place:

**git reset –hard**

**git clean -fxd**

The git reset –hard command will revert uncommitted changes that exist in files that have been added to the index, whether those files are newly created files, or files that were added to the index in the past and have been edited since the last commit. However, if any new files have been created in the Git repository that have never been added to the index, these files will remain in the project folder after the hard reset. To remove these files, the git clean -fxd command is needed.

# Restoring from Staging

> git restore --staged [filename]

After restoring, file in staging is lost. The same commited file (if exists) gets pushed to staging. This makes sense, we remove staging and stage the new file.

<div>
    <img src="Fig J.png" style="max-width: 20%;">
</div>

# Restoring from Commit

> git restore [filename]

<div>
    <img src="Fig K.png" style="max-width: 20%;">
</div>
chec
# Restoring file to an earlier version

> git restore --source=HEAD~1 file01.txt -> # restores from commit, specifying offset

> git clean -fd -> # removed untracked files permanently        

# Uncommit the last commit
> git reset --soft HEAD~1

### Short Status Command

<div>
    <img src="Fig H.Png" style="max-width: 20%;">
</div>

## Git Diff - Compare changes

> git diff -> # to see what is in the local area before the next staging        
> git diff --staged -> # to see what is in the staging area before the next commit      
> git diftool HEAD HEAD^ -> # compares local to remote on VSCode

<div>
    <img src="Fig I.png" style="max-width: 20%;">
</div>

## VS Code for comparing files
> git config --global diff.tool vscode -> # configure vs code as the default diff tool

> git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"-> # tell git gow to launch vs code --diff = we want the tool to compare $L $R placeholders for old and new copy of file

> git difftool -> # launch comparison tool to compare local vs staged

> git difftool --staged -> # launch comparison tool to compare staged vs commited


## Git Log

> git log -> # shows full log history. Use space for more and q to quit

> git log --stat -> # shows full history of changes and what was changed

> git log --oneline -> # small version of 

> git log --oneline --stat -> # --stat shows more details of changes in short version

> git log --oneline --patch -> # --patch shows the diff in logs in short version

> git log --oneline -3 -> # shows last 3 commits

> git log --oneline --author="" -> # filter by author

> git log --oneline [filename] -> # filters log commits by file name

> git show -> # details of the last change commited

> git show [logHEX] -> # details for the log ID

> git show HEAD~2 -> # view a commit. go to head and two steps back

> git show HEAD~2:[folder\file] -> # view what exactly was commited

> git show HEAD~2 --name-only -> # view only file names edited or modified in this commit

> git show HEAD~2 --name-status -> # view only file names edited or modified in this commit

> git HEAD -> # details of where HEAD is poi

> git HEAD~1 -> # details of where HEAD is pointed offset by 1

#### Deeper Logs, which i could not understand

> git log HEAD~1:.gitignore

> git ls-tree HEAD~1

> git show [tree/blob ID]

## Copy

> cp -r oldFolder newFolder -> # -r = recursive files and folders       
> cp "..\CSharp_Stuff\.gitignore" ".\.gitignore"

# Conflict between remote and local repo
> git checkout --theirs ".\path" # -> choose which file to keep --ours / --theirs        
> git commit -m "message"

# fatal: refusing to merge unrelated histories
Here the git command will look something like this: git pull origin master --allow-unrelated-histories.
You can substitute *origin* with the *remote repository* you are pulling from. You can also replace the *master* branch with *whatever branch* you want the pull request to merge into.

> git pull https://github.com/finch1/Py_Stuff.git main --allow-unrelated-histories