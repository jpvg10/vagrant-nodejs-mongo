# vagrant-nodejs-mongo

This Vagrant machine contains:

- Ubuntu 20.04
- Node.js 14
- MongoDB 4.4

## How to use

> **Note**
>
> I have only tested this virtual machine using Windows 10 as host

- Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads) and [Vagrant](https://www.vagrantup.com/downloads)
- Open up a terminal (if you are on Windows, do it **as administrator**)
- Clone this repository
- Run `vagrant up` in the folder that holds this repository
- Wait for the virtual machine to download and start
- Log in to the machine running `vagrant ssh`
- To exit the machine just run `exit`
- To shut down the machine run `vagrant halt`
- To remove the machine with all its files run `vagrant destroy`

### Shared folder

The `/vagrant` folder in the virtual machine is synchronized with the folder that holds this repository in your machine. Any changes you make in the `/vagrant` folder will be visible on your machine and vice-versa.

To run the sample project, do the following while logged into the virtual machine:

- `cd /vagrant/src`
- `npm install`
- `npm start`

The app is now running on the virtual machine.

### Networking

The virtual machine's port **3000** is mapped to the host machine's port **3001**. If you go to your web browser and type `http://localhost:3001` you should see the sample app that is running inside the virtual machine.

Also port **27017** is mapped to the host's **27018**, so you can use a tool like [Robo 3T](https://robomongo.org/) or [MongoDB Compass](https://www.mongodb.com/products/compass) in the host to explore the Mongo database running in the virtual machine. To do that, do the following while logged into the virtual machine:

- `sudo nano /etc/mongod.conf`
- Change the line `bindIp: 127.0.0.1` to `bindIp: 0.0.0.0` and save the file
- Restart the Mongo service with `sudo systemctl restart mongod`

Now you can connect to Mongo from the host using the address `mongodb://localhost:27018`.

### Development

You can now use this virtual machine for development.

You can wipe the `src` folder and put your own Node.js files in there, or create any folder structure you want. As long as it is inside the `/vagrant` folder, and the server runs on port **3000**, it will work and it will be visible from your host machine. (Of course, you can change the port mappings or add more of them in the `Vagrantfile` if you want)

Also because of the shared folders, you can use your favorite text editor in the host machine to develop.

## Further reading

If you are not familiar with Vagrant or would like to learn more about it, you can read their official guides [here](https://learn.hashicorp.com/tutorials/vagrant/getting-started-index).
