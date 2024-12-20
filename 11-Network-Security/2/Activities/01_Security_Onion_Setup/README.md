
## Activity File: Security Onion Setup

In preparation for the labs, everyone will need to log in to Azure and connect to the Network Security environment. After you are connected, launch an instance of Security Onion from the HyperV manager. This will generate alert data that will allow everyone to complete the labs.

Log in to the Security Onion machine with the following credentials:

- Username: `sysadmin`
- Password: `cybersecurity`

Lead the class in the following demonstration.

 - `sudo ./so-ipchange.sh`

       - Answer `Y` if it prompts you for a response. Otherwise, continue to the next step.

    - `sudo so-status`
      
       - `so-status`: Checks the status of currently installed NSM tools.

       - ***Note: It will take some time for the services to come online. Continue lecturing until you reach 6. Network Security Monitoring and Sec Onion, and return here to check the services.***
   
    
    - When completed, output should look similar to below:
   
       ![NSM Status](../../../2/Images/SO%20Status.png)
   
      - Ensure all statuses are listed as `running`.

      - If not, let the `so-status` command run for a few minutes. It can be slow.
   
    - If any of the statuses are not listed as `running` after a few minutes, restart the NSM tools with the following command:

       - `sudo reboot`
   
    - Run the `so-status` command again for a few minutes. All systems should be listed as `OK` after a few minutes.

      - Determine the IP address being used for Security Onion by entering `sudo ip a s eth0`
  
         - `ip a s eth0`: This command returns the IP address of the specified interface.
        
            - The `a` stands for `a`ddress and brings back the IPv4 or IPv6 address.

            - The `s` returns `s`tatistics on the interface made up of packets transferred and received.

    ![Security Onion IP Address](../../../2/Images/SO%20IP%20Address.png)

    - **Note:** Your IP address may be different than the one depicted above.

#### Generate Alerts

2. Next, have the students log into Security Onion to verify that their PCAPs are still populated. Remind students that their Security Onion login credentials are:

   - Username: `sysadmin`
   - Password: `cybersecurity`

Verify that students still have their PCAPs loaded from the previous class. If this is not the case for anyone, have them run the following command to replay all PCAP files from previously captured malware:

   - `sudo so-test`

- Emphasize that it could take as long as 10–15 minutes for Security Onion to run all of the PCAPs.

Once everyone's machines are set up, move on to a brief review and introduce today's topics.

© 2024 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.

