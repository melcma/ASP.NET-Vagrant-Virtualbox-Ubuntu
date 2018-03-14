ASP.NET Core on Ubuntu Server virtual machine

Set-up
1. Install VirtualBox https://www.virtualbox.org/wiki/Downloads
2. Install Vagrant https://www.vagrantup.com/downloads.html
3. Clone this repository
4. vagrant up


Create ASP.NET application
1. vagrant ssh aspnet
2. cd /var/www
3. dotnet new mvc


Debug on port 8001
1. ASPNETCORE_URLS=http://0.0.0.0:8001 dotnet run
2. Visit localhost:8001 on host machine, application should be running
