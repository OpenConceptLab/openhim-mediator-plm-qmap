
# openhim-mediator-PLM
OpenHIM Mediator for executing plm import and export scripts.

## Usage
Install via npm
```
npm install -g openhim-mediator-plm
```
(note this will need root/sudo permission)

Create an appropriate location for you scripts (only scripts in this location will be allowed to be executed)
```
mkdir /opt/ocl-datim
```
Next get a copy of the default config and place it in an appropriate location, e.g.
```
mkdir /etc/openhim
wget https://raw.githubusercontent.com/maurya/openhim-mediator-plm/master/config/default.json
mv default.json /etc/openhim/mediator-plm.json
```
Edit the values in this config according to your setup.

Run the mediator:
```
openhim-mediator-plm --conf /etc/openhim/mediator-plm.json
```

Now you can setup your HIM channels and the mediator config via the console.

## Polling Channel Example
Say we have a maintenance script `task.sh` that needs to execute on a daily basis. Copy the script into the mediator scripts directory and give it execute permission:
```
cp task.sh /opt/ocl-datim
chmod +x /opt/ocl-datim/task.sh
```
Note that the mediator *process* needs execute permission for the script.

With the script in place we can setup the channel and mediator in console. Go to *Mediators* and click on the *OpenHIM PLM Mediator* item. From there click on the blue *Configure Mediator* button.

Add a new script and give it an endpoint on which to trigger execution. Enter the name of the script `task.sh`. Any required arguments or environment variables can be added as well.
![screen shot 2016-03-10 at 09 12 34](https://cloud.githubusercontent.com/assets/1872071/13662056/4ab49908-e6a0-11e5-90d3-bb10298bf95b.png)

After you hit the *Save Changes* button, the mediator will automatically pick up on the new config.

Now we can setup a new channel that will call the script on a daily basis. Add a new polling channel:
![channel-basic-info](https://cloud.githubusercontent.com/assets/1872071/13661621/f0066d2c-e69c-11e5-9e8c-b7b7ad5c15b8.png)

Give it an access control permission such as `internal`.

Add the script route by picking the *OpenHIM PLM Mediator* option in *Add Mediator Route*. Edit the route and set *Route Path* to `/task`:
![channel-route](https://cloud.githubusercontent.com/assets/1872071/13661539/0907ab20-e69c-11e5-807a-d82ac6339dc1.png)

Click on *Save Changes* and then that's it. The polling channel will now execute the script daily. The script output (both `STDOUT` and `STDERR`) will be viewable in the response body for the transaction.

## Development
Checkout from GitHub
```
git clone https://github.com/maurya/openhim-mediator-plm.git
npm install
```
To run the mediator in development mode
```
npm start
```
or to run the tests
```
npm test
```

## License
This software is licensed under the Mozilla Public License Version 2.0.
