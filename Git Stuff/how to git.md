<style type="text/css">
.centerImage
{
 text-align:center;
 display:block;
}
</style>

# Git Is Distributed
Local repos can sync with other repos
<p>
    <img src="Fig A.png" alt="Distributed" class="centerImage" style="max-width: 20%;"/>
</p>

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
<p>
    <img src="Fig L.png" alt="Distributed" style="max-width: 20%;"/>
</p>

# Getting Started
> mkdir Repo        
> cd Repo       
> git init -> # initialises a new git repo

