Task name => Github
Task preparation =>  Heb nagedacht over het maken van een script voor toekomstige taken.
Task implementation => what is the way you have implemented this? 
Task troubleshooting => ik had een klein probleem met het clonen van mijn github read me file, ik had type fouten in mijn commando's daarom ging het niet. Met alle juiste command's ging alles goed. 
Task verification => proof of the quality of the result in mijn portfolio


Task1 -- GitHub Skills Test ** 
stap1: repo maken
stap2: maak een folder 
stap3: commando’s die ik gebruikt heb
	git init
	git clone
	git add.
	git commit -m “(comment about your push)”
	git branch -m main
	git remote add origin link repo github
	git push -u origin main
stap4: github checken voor wijzigingen 

Task2– Ansible Skills
nvt: probleem met router en switches.
Task3 - -docker 
stap1: folder “docker” maken en daarin “datascript.js” en “dockerfile”
stap2: de docker file bevat deze code = FROM httpd:2.4
COPY templates/index.html /usr/local/apache2/htdocs/
COPY templates/datescript.js /usr/local/apache2/htdocs/
EXPOSE 80
stap3: de datascript bevat deze code = document.addEventListener("DOMContentLoaded", function() {

    function updateDateTime() {

        var currentDate = new Date();
        var formattedDateTime = currentDate.toLocaleString();
        document.getElementById("datetime").innerText = formattedDateTime;
    }

    // Initial call to update date and time
    updateDateTime();


    setInterval(updateDateTime, 1000);
});

stap4: nu maak ik een nieuwe folder “templates” en daarin maak je een index.html file met deze code: 
<html>
<head>
    <title>DevNet Associate Skills Test:Jawad chaieb</title>
    <link rel="stylesheet" href="/static/style.css" />
</head>
<body>
    <h1>DevNet Associate Skills Test</h1>
    <p>Created by: jawad chaieb</p>
    <p>Date: <script src="datescript.js"></script></p>
    <p id="datetime"></p>
</body>
</html>
stap5: nu mag je alles tester met dit commando:curl http://localhost:8080/ 
!!alles werkt maar error bij de laatste
Task4 – Jenkins
nvt: probleem communicatie tussen laptop en router,switch.
Task6 - - Webex
stap 1: folder aanmaken
stap 2: script aanmaken
stap 3: webex account aanmaken 
stap 4: code implementatie in de script file
import requests
import json 

# Webex Teams API base URL
api_url = "https://api.ciscospark.com/v1"

# Your Webex Teams API token
api_token = "MTI3MTFiMjUtMzkyZi00YzY0LWJmYTQtMTk4ZTc4Zjk4YjRjZjExNDcyZjctMjI1_PE93_d76db10e-7f06-4975-9c4f-a25c7c81e7f0"

# Members' email addresses
your_email = "jawad.chaieb@student.odisee.be"
yvan_email = "yvan.rooseleer@biasc.be"

# Webex Teams space name
space_name = "devasc_skills_jawadchb"

# Function to create a Webex Teams space
def create_space(api_url, api_token, space_name):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }
    payload = {"title": space_name}
    response = requests.post(f"{api_url}/rooms", headers=headers, json=payload)
    return response.json()["id"]

# Function to invite members to a Webex Teams space
def invite_members(api_url, api_token, space_id, email_list):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }
    for email in email_list:
        payload = {"roomId": space_id, "personEmail": email}
        requests.post(f"{api_url}/memberships", headers=headers, json=payload)
# Function to send a message to a Webex Teams space
def send_message(api_url, api_token, space_id, message):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json",
    }
    payload = {"roomId": space_id, "text": message}
    requests.post(f"{api_url}/messages", headers=headers, json=payload)

# Create Webex Teams space
space_id = create_space(api_url, api_token, space_name)

# Invite members to the space
invite_members(api_url, api_token, space_id, [your_email, yvan_email])

# Publish GitHub repository URL in the space
github_repo_url = "https://github.com/JawadChaieb/Devasc_skills"
send_message(api_url, api_token, space_id, f"Check out my GitHub repository: {github_repo_url}")

# Send a message to the space
send_message(api_url, api_token, space_id, "Here are my screenshots of devasc skills-based exam")

stap 5: zie commando’s in bijlage foto.

Task 7 – Bach
nvt: probleem communicatie tussen laptop en router,switch.
Task 10 — DANC
stap1: maak een folder met de naam “DANC”
stap2: python file met de naam “DANC.py”
stap3: 	zet de folgende code in de python file
import requests
import datetime
import json
requests.packages.urllib3.disable_warnings()

DNAC_scheme = 'https://'
DNAC_authority='sandboxdnac.cisco.com'
DNAC_port=':443'
DNAC_path_token='/dna/system/api/v1/auth/token'
DNAC_path='/dna/intent/api/v1/network-device'
DNAC_user = 'devnetuser'
DNAC_psw = 'Cisco123!'


print("Current date and time: ")
print(datetime.datetime.now())


token_req_url = DNAC_scheme + DNAC_authority + DNAC_path_token
auth = (DNAC_user, DNAC_psw)
req = requests.request('POST', token_req_url, auth=auth, verify=False)
token = req.json()['Token']


req_url = DNAC_scheme + DNAC_authority + DNAC_port + DNAC_path
headers = {'X-Auth-Token': token}
resp_devices = requests.request('GET', req_url, headers=headers, verify=False)
resp_devices_json = resp_devices.json()


for device in resp_devices_json['response']:
    if device['type'] is not None:
        print('===')
        print('Hostname: ' + device['hostname'])
        print('Family  : ' + device['family'])
        print('MAC: ' + device['macAddress'])
        print('IP: ' + device['managementIpAddress'])
        print('Software version: ' + device['softwareVersion'])
        print('Reachability: ' + device['reachabilityStatus'])
stap4: nu mag ja alles testen met deze commando python3 DANK.py
