## [svn2git](https://github.com/nirvdrum/svn2git)

## Installation steps
- Make sure git and git-svn is installed, Ruby is also required
  - $ sudo apt-get install git-core git-svn ruby (If you have different Linux distro use the package tool accordingly)
- Clone the git repository
  - $ sudo gem install svn2git

## Migration steps
- The repo contains the standard folder layout and does not contain any other folder in the root
  - $ svn2git http://svn.example.com/path/to/repo
--------------------------------------------------------------------------------------------------------
- The repo contains the standard folder layout and contains some folders in root
  - $ svn2git http://svn.example.com/path/to/repo
  - Note: This will only migrate trunk as master, branches and tags and all other folders will be ignored.

  - For other folders to be migrated with their history as commits in git
  - $ git svn clone  --ignore-paths='tags|trunk|branches' http://svn.example.com/path/to/rep --username ' '

  - Then merge the two repos migrated separately
  - Steps
    - Move the repo to folder where you have migrated branches and tags and enter the command
    - $ git merge /path/to/folder --allow-unrelated-histories
--------------------------------------------------------------------------------------------------------

- The repo contains several folders and does not have proper folder structure
  - $ svn2git --rootistrunk  http://svn.example.com/path/to/repo --username ' '
