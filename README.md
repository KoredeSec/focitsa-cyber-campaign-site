# focitsa-cyber-campaign-site
Static campaign website for FOCITSA cybersecurity candidates built and deployed on AWS with HTTPS &amp; No-IP DDNS
Building and Deploying a Secure Campaign Website for FOCITSA Elections (Cybersecurity Department)

**Introduction**
In preparation for the FOCITSA 2025 elections, I took the initiative to build and deploy a secure, colorful, and fully functional campaign website showcasing candidates from the Cybersecurity Department. This project was aimed at increasing voter engagement, enhancing transparency, and showcasing the leadership profiles of each candidate. The project was led and sponsored by Ibrahim Yusuf, NACSS President.

**Project Goals**

Create a professional and vibrant campaign website.

Deploy it on AWS EC2 using free-tier resources.

Secure the site with HTTPS using Let’s Encrypt.

Utilize a free domain with No-IP Dynamic DNS.

Ensure the site is publicly accessible and available during the election campaign window.

Features of the Website

Candidate profiles for:

Adeniyi Daniel (Financial Secretary)

Ayanyemi Roland aka Cashy (Social Director 1)

Opeyemi Oluwasegun aka Opesax (Public Relations Officer 1)

Ajibade Jeremiah aka Emmy-J (Software Director 2)

Individual sections with leadership experience, manifestos, and fliers

School logos: Osun State University, NACOS, and FOCITSA

Visual theme of unity, digital transparency, and student empowerment

Tech Stack & Tools Used

Frontend: HTML, CSS (Static Web Page)

Web Server: Apache2

Cloud Platform: AWS EC2 (Ubuntu 22.04)

SSL: Let’s Encrypt via Certbot

Dynamic DNS: No-IP DUC

Deployment: SCP over SSH, Linux Terminal

Step-by-Step Implementation

1. Local Website Creation

Designed a colorful landing page using HTML and CSS

Organized assets (fliers, logos) inside an /assets directory

Created sections for each candidate with their photo, about text, and leadership record

2. EC2 Setup on AWS

Launched a free-tier Ubuntu EC2 instance

Configured security group to allow HTTP (port 80), HTTPS (port 443), and SSH (port 22)

Connected via SSH from local Ubuntu machine

3. Apache Installation & Setup

sudo apt update && sudo apt install apache2
sudo ufw allow 'Apache Full'

Tested default Apache page at http://<EC2-PUBLIC-IP>

4. Deployment via SCP

Zipped the website files locally

Transferred with:

scp -i ~/tory/Candidates.pem ~/Downloads/focitsa_website_cyber.zip ubuntu@<EC2-IP>:/home/ubuntu/

SSH into server, unzip and copy:

sudo apt install unzip
unzip focitsa_website_cyber.zip
sudo cp -r * /var/www/html/

5. Domain Setup with No-IP

Created a free hostname: focitsacyber2025.ddns.net

Installed No-IP DUC:

wget --content-disposition https://www.noip.com/download/linux/latest
sudo apt install ./noip-duc_3.3.0_amd64.deb

Logged in using DDNS credentials:

noip-duc --username <USERNAME> --password <PASSWORD> --hostnames focitsacyber2025.ddns.net

6. SSL Integration with Certbot

Installed Certbot:

sudo apt install certbot python3-certbot-apache

Generated and installed SSL:

sudo certbot --apache -d focitsacyber2025.ddns.net

Auto-renew configured with:

sudo certbot renew --dry-run

Outcome

Live secure site: https://focitsacyber2025.ddns.net

Functional HTTPS with valid SSL certificate

Mobile-friendly, easily shareable campaign website

Dynamic DNS ensures public IP changes won’t break access

Impact & Relevance

Enabled Cybersecurity candidates to reach a wider audience

Promoted digital literacy and campaign visibility

Demonstrated real-world DevSecOps skills: DNS, Web Hosting, Security, and Linux administration

**How to Showcase on Resume **
Project: FOCITSA Cybersecurity Campaign Website (2025)Tools: AWS EC2, Apache2, No-IP, Let’s Encrypt, HTML/CSS, SSH, SCP

Highlights:

-Developed and deployed a secure static site with live SSL

-Managed DNS via No-IP Dynamic Update Client

-Configured full server setup, port rules, and SSL using Linux commands

-Contributed to a faculty-wide student election process

**Conclusion**
 This project has been a significant opportunity to apply cloud and cybersecurity knowledge into practice. It also served as a platform for empowering student representation while developing key web deployment and system administration skills. Fully self-hosted, secured, and live on the internet – this campaign website demonstrates the possibilities of student-led tech innovation.

Author: Ibrahim Yusuf  Role: NACSS President & Project Lead

