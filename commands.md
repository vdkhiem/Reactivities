Install .NET 5
https://dotnet.microsoft.com/download

Install NVM (manage node version)
http://bit.ly/2Hn8HjG (https://joachim8675309.medium.com/installing-node-js-with-nvm-4dc469c977d9)
# install nvm
brew install nvm
source $(brew --prefix nvm)/nvm.sh
echo 'source $(brew --prefix nvm)/nvm.sh' >> ~/.profile
# install node
nvm install ${VERSION} (nvm install 14.16.1)
nvm use ${VERSION} (nvm use 14.16.1)


# Install Visual Code and Extensions
1.C#
2.C# Extensions
3.Nuget Gallery (NuGet Gallery Extension makes installing and uninstalling NuGet packages easier)
4.Bracket Pair Colorizer 2 (A customizable extension for colorizing matching brackets)
5.Material Icon Theme (Material Design Icons for Visual Studio Code)
6.SQLite (Explore and query SQLite databases.)

Source Code for reference
https://github.com/TryCatchLearn/reactivities

# Construct .net skeleton
dotnet new sln
dotnet new webapi -n API //-n to create new folder
dotnet new classlib -n Application
dotnet new classlib -n Domain
dotnet new classlib -n Persistence
dotnet sln add API
dotnet sln add Application
dotnet sln add Persistence
cd API
dotnet add reference ../Application
dotnet add reference ../Persistence
dotnet add reference ../Domain

# Run .net api application
dotnet run
dotnet watch run


ShortCut Command
Command + . (period): to add directive

Install EntityFrameworkCoreSqlite nuget package for Persistence project

# Generate migration code (Entity Framework auto mapper)
Install dotnet-ef for database migration (code first)
dotnet tool list --global // to check what dotnet tools have installed
dotnet tool install --global dotnet-ef // this is tool to create a new migration
optional: dotnet tool update --global dotnet-ef // if this tool already install and we want upgrade to latest.
dotnet ef migrations add InitialCreate -p Persistence -s API // create migration based on the code writtern in Persistence. -p is where db context is, -s is where project is started

if you encounter the error 
    "Your startup project 'API' doesn't reference Microsoft.EntityFrameworkCore.Design. This package is required for the Entity Framework Core Tools to work. Ensure your startup project is correct, install the package, and try again."
Add Microsoft.EntityFrameworkCore.Design nuget package to API project

# Commit code to git repo
dotnet new -l // to find command to add gitignore
dotnet new gitignore // add gitignore file
// add appSettings.json to gitignore file so we don't commit sensitive settings

# Add a new git repo
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/vdkhiem/reactivities.git
git push -u origin main