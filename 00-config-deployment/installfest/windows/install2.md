# Windows Installfest 2

## Node

We will install the Linux version of NodeJS into WSL without any version manager. The commands here will install Node v10.x. For other versions, change the number after `setup_` in the 2nd command accordingly. If you wish to run multiple versions of NodeJS on your machine, which may be necessary for legacy development work, look at the section on using nvm instead. __Warning: Do NOT run through both sets of instructions (here, and the one for `nvm`) or you will encounter version/library conflicts.__

- Run the following commands in order in the WSL terminal. Wait for each to complete before running the next.
	- `sudo apt-get update && sudo apt-get upgrade`
	- `curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -`
	- `sudo apt-get install -y nodejs`
  - `mkdir ~/.npm`
  - `npm config set prefix '~/.npm'`
  - `echo 'export PATH="$HOME/.npm/bin:$PATH"' >> ~/.bashrc`
  - `source ~/.bashrc`
	- `node -v` (Checks the installed version of NodeJS)
	- `npm -v` (Checks the installed version of npm)

## Installing PostgreSQL
- Any database system contains at least 2 parts: the database server itself, and the database client. As WSL does not officially support GUI tools, for our convenience, we will install database servers on Windows, and use command line clients in WSL. This allows us to optionally install GUI clients in Windows for more convenient data visualization.

- __Installing the PostgreSQL server__
	- Download and install the latest version for Windows x86-64 from (https://www.enterprisedb.com/downloads/postgres-postgresql-downloads). This will also install PGAdmin.
	- Use pgAdmin 4 to create a `Login/Group Role` for your server with the __same name as your WSL username__. Ensure that under the `Privileges` tab, the options for `login` and `create databases` are turned on.
	- Use pgAdmin 4 to create a `Database` with the __same name as your WSL username__, and set its owner to the user that you just created.

- __Installing the PostgreSQL client__
	- Open a WSL terminal and run the following commands in order.
	- `sudo apt-get update && sudo apt-get upgrade`
	- `sudo apt-get install postgresql-client-10 postgresql-client-common` (Change the version after -client- to the version of PostgreSQL that you installed)
	- `echo 'export PGHOST=localhost' >> ~/.bashrc`
	- Either `source ~/.bashrc` or restart WSL to reload the config
	- `psql` to check that everything runs. Type `\l` to see a list of databases. Hit `q` to exit the list if needed, and type `\q` to exit the client.
	- If you want PostgreSQL to start automatically on boot, do the following.
		- Press the Win key and type `services`. Press enter.
		- Look for the PostgreSQL 10 Server service, right-click on it, and ensure that the `Startup type:` is set to `Automatic`.

### Passwordless Postgres

Set no-password on postgres for your computer, so that it's easier to work with.


Edit postgres configuration file:

```
sudo sublime /etc/postgresql/POSTGRE_VERSION/main/pg_hba.conf
```

The file will look like this:

Change all configuration access to:

```
 # Database administrative login by Unix domain socket
 local   all             all                                     trust

 # TYPE  DATABASE        USER            ADDRESS                 METHOD

 # "local" is for Unix domain socket connections only
 local   all             all                                     trust
 # IPv4 local connections:
 host    all             all             127.0.0.1/32            trust
 # IPv6 local connections:
 host    all             all             ::1/128                 trust

```
Restart postgres server

```

 sudo /etc/init.d/postgresql restart

```
