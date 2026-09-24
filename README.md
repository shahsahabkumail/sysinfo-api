# sysinfo-api
A system monitoring and diagnostics API built with FastAPI

What This App Does

it is a back end service that provide real time status of a Linux machine. It renders system information endpoints (such as CPU, memory usage and system health) using Uvicorn, running on Nginx and background automation scripts for log management.

API endpoints
1. Health API
   Check to verify the API is alive and responding.
   curl http://localhost/health
   
2. System Info
   Gives details about health and statistics of host machine
   curl http://localhost/system/info

How to Deploy It From Scratch
Download or clone this repo, make sure you have python installed then install requirements 
write a custom systemd service file so linux runs uvicorn as background daemon and it restart on crashes 
configure nginx to proxify web requests on port 80 to uvicorn port

What Each Config File Does
sysinfo-api.service: this file define how fastapi will run the app and points to python venv and ensure services automatically boots and restart when required
sysinfo-api.conf : this file is nginx config it manage requests of web and proxify them to uvicorn server adn maintainlogs for app

How to Check Logs & Troubleshoot

to see app logs:  sudo journalctl -u sysinfo-api.service -f

to see recent http request and error logs of nginx
sudo tail -f /var/log/nginx/sysinfo-api.access.log
sudo tail -f /var/log/nginx/sysinfo-api.error.log

Happy Coding!!!
