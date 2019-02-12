# How to install new electrum server for KOIN.

- Create new server from the aws AMI named `electrum-snap-feb12` 
- Use security group named `launch-wizard-3` which has all the necessory ports open and access previlaged
- Login to the server
  - Run `cd ~/~/komodo_new/src`
  - Run `./komodod -ac_name=KOIN -ac_supply=125000000 -addnode=3.0.32.10`
  - Start ElectrumX
    - Run `sudo systemctl start electrumx`
  - Verify
    - Run `electrumx_rpc -p 30001 getinfo`
