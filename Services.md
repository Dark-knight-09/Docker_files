 System services refer to the background processes or daemons that run on a server to provide various functionalities. These services can include web servers, database servers, email servers, file servers, and more. They typically start automatically during system boot and run continuously in the background, waiting for client requests or performing specific tasks. System services play a crucial role in maintaining the server's functionality and ensuring that it can handle client requests efficiently.

 the services are the application running in the system or server which are listening to for request from the client and responding to it.

systemctl start mysql // start mysql service
systemctl stop mysql // stop mysql service

> systemctl status [service_name] // check status of service
> systemctl start [service_name] // start service
> systemctl stop [service_name] // stop service
> systemctl restart [service_name] // restart service
> systemctl enable [service_name] // enable service
> systemctl disable [service_name] // disable service
> systemctl is-enabled [service_name] // check if service is enabled
> systemctl is-active [service_name] // check if service is active
> systemctl list-units --type=service // list all services

# for Mac OS
>launchctl list

# for windows























