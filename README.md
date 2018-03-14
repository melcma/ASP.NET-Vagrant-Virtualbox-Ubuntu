ASP.NET on Ubuntu Server virtual machine

Set-up
1. Install VirtualBox https://www.virtualbox.org/wiki/Downloads
2. Install Vagrant https://www.vagrantup.com/downloads.html
3. Clone this repository
4. Vagrant up


Create ASP.NET application
5. vagrant ssh aspnet
6. cd /var/www
7. dotnet new mvc


Debug on port 8001
8. ASPNETCORE_URLS=http://0.0.0.0:8001 dotnet run
9. Visit localhost:8001 on host machine, application should be running
