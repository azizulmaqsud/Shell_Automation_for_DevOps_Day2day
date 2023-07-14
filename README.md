# Shell Scripting Automation for DevOps Day2day [Very Important]

## Jira Automation with For Loop block 

Get Token from Jira Account

1) Log your JIRA then go to https://id.atlassian.com/manage-profile/security/api-tokens
   
3) Click Create API token.
   
5) Create Label for your token and click Create.
   
7) Login back to https://youraccountname.atlassian.net/ and create a PROJECT in JIRA


STEP 1 – create jiraid.txt 

STEP 2 - Add your JIRA ticket id

STEP 3 – Create jira.sh and add beside code

STEP 4 – Replace the USERNAME and TOKEN from your Atlassian account

#!/bin/bash version="1.2.3.4"

for line in $(cat jiraid.txt) 

do

curl -X PUT -u "your_atlassian_jira_username:your_atlassian_jira_token" --data'{"update":{"labels":[{"add":"DEMO_NEW"}]}}' -H "Content-Type:

application/json" https://yourname.atlassian.net/rest/api/3/issue/SA-1/comment

done

STEP 5 - chmod +x jira.sh

STEP 6 - Then hit the ./jira.sh script

## JFrog Automation with IF ELSE block

#!/bin/sh CICD=true WORKSPACE=/opt/

JOB_BASE_NAME=Test_demo BUILD_NUMBER=20

if [ $CICD = true ] then

echo "CI/CD pipe line check" file="${WORKSPACE}/basic_report.html" REPORTNAME=${JOB_BASE_NAME}_${BUILD_NUMBER}.Test_demo_20

echo "CICD Check starting" if [ -f "$file" ]; then

echo "testReport file found sending to artifactory"

curl -H X-JFrog-Art-Api:Token -T $file https://oneartifactorycloud/artifactory/CICD/Reports/$REPORTNAME.html

else

echo "testReport file found sending to artifactory" 

fi

fi

## Automate Array Declaration 

#!/bin/bash

array=(helloservice hiservice nameservice managerservice teamservice)

for line in "${array[@]}"

do

COUNT=`ps -ef | grep helloservice | grep -v grep | wc -l`. RUNNING , 3

MAX=2

echo $line

echo $COUNT

if [ $COUNT -gt $MAX ]

then

echo $line

PROCS=`ps -ef| grep $line | grep -v grep | awk '{print $2, $11, $12, $13}' | sort -k 4`

JAR=`echo "${PROCS}" | awk -F"-Djar_name=| " '{print $5}'`

echo $JAR

JAR_RUN=`echo $JAR | sed 's/ /,/g'`

echo $JAR_RUN

cd /apps/nnos/vzomega/scripts

./mail.sh $line $JAR_RUN $COUNT

fi

done

STEP 1 - add below statement to array_automation.sh

array=(helloservice hiservice nameservice managerservice teamservice)

for line in "${array[@]}" do

echo $line Done

STEP 2 – chmod +x array_automation.sh 

STEP 3 - ./ array_automation.sh

## Log Automation
Archive The Data With Find/Mtime/Tar/Name Command

Create two folders 

mkdir –p /opt/logs

mkdir –p /opt/logs/ Log_Backup

Create a log file test.log in folder /opt/logs/

#!/bin/bash 

cd /opt/logs/

input the below commands with vim


find . -type f -name '*log*' -exec cp '{}' /opt/logs/Log_Backup \; 

cd /opt/logs/Log_Backup

find /opt/logs/Log_Backup -type f -name '*log*' > include-file 

tar -cvf$(hostname)_$(date +%Y-%m-%d).tar.gz -T include-file 

exit

chmod +x automation4.sh

 ./ automation4.sh

## Date Automation with While loop 

For MAC

#!/bin/bash 

ONE=14d

Fourteendaysold=`date -v -${ONE}` 

echo $Fourteendaysold

TWO=7d

sevendaysold=`date -v -${TWO}` 

echo $sevendaysold

echo $Fourteendaysold and $sevendaysold are obtained

For Linux System

#!/bin/bash

may_date=`date -d '2023-04-01 +30 days' '+%Y-%m-%d'` echo $may_date

TWO=2

april_date=`date -d '2023-04-03 -2 days' '+%Y-%m-%d'` echo $april_date


## Automate Emails to your Team

/usr/sbin/sendmail -i -t << Subject: $1 server process status From: Email1

To: Email2

Hi Team,

Please check for $1 service in TEST server which has $3

process running with below list of KIT IDs

$2

Regards, 

Azizul maqsud

MESSAGE_END

## Special Variables in Shell
  $#  Stores the number of command- line arguments that were passed to the shell program.
  
  $?  Stores the exit value of the last command that was executed.
  
  $0  Stores the first word of the entered command (the name of the shell program).
  
  $*  Stores all the arguments that were entered on the command line ($1 $2 ...).
  
  $@  Stores all the arguments that were entered on the command line, individually quoted ("$1" "$2" ...).



CASE 1 :

echo "With *:”

for arg in "$*"; do echo "<$arg>"; done

CASE 2:

echo "With @:”

for arg in "$@"; do echo "<$arg>"; done


With *:

<DevOps Job Description>


With @:

<DevOps>
  
<Job>
  
<Description>


## Automate HTML File

STEP 1 – Create jiraid.txt and version.txt

STEP 2 – Add shell script to htmlfile.sh 

cat > jira.html <<'EOF'

<html>
  
<body>
  
<p><strong>MODULE_VERSION - {{module_version}}</strong></p>

<table border="1" cellspacing="0" cellpadding="2.5" valign="top" width="100%" align="justify"
  
style="width: 100%; max-width: 1200px; background-color: #ffffff">

<tr>
  
<th>Key</th>

</tr> EOF

MULTIPLE FILES READ:

paste jiraid.txt version.txt | while read take; do cat >> jira.html <<EOF

<tr>
  
<td>$read</td>

<td>$take</td>

</tr> EOF

done
 
STEP 3 – chmod +x automation7.sh

STEP 4 - ./automation7.sh


## Automate Sonar/GitLab Rest API

curl -u "GITLAB:$gitlab”
 
"https://sonar/api/qualitygates/project_status?projectKey=${sonarProjectKe y}&branch=${PIPELINE_GIT_BRANCH}" >> status.json

cat status.json | jq '.projectStatus .status' > status.txt sed 's/"//g' status.txt >> QG.txt

echo "status=$(sed -n '1p' QG.txt)" if [ $(sed -n '1p' QG.txt) == 'ERROR' ] then

echo -e "*****$RED QUALITY GATE ERROR $NC*****"

echo "Check https://sonar/dashboard?id=${sonarProjectKey}" exit 1	FAILURE
else
echo "*****$GREEN QUALITY GATE OKAY $NC******"

echo "To validate check https://sonar/dashboard?id=${sonarProjectKey}"

fi


{
"employee": {

"name":	"sonoo", "ID":	56000,

"Status":	true

}

}

cat status.json| jq '.employee’

cat status.json| jq '.employee.name'

curl --request POST --header "PRIVATE-TOKEN: $TOKEN" "https://gitlab/api/v4/projects/$PROJECT_ID/protected_branch es?name=$MS_TARGET_BRANCH&push_access_level=40&merg e_access_level=40" >> protectedbranches.txt


## Automate the process of .Jar file

(java –jar helloworld).	Id runtime cpu mem RAM App -> CPU RAM MEM HARDWARE. (AWK, SED, GREP,PIPE)

**hello=`ps -ef | grep -i helloworld- 20.1.2.3.jar | awk '{print $13}’`

sed -i 's/mdreject.html/index.html/g' web.xml

**sed -i 's/'"$version"'/'"$newversionCode"'/’ test.sh

date1=`echo $date| sed 's/-//g’`

**cat branch.json | jq '.branches[0].name' | tr -d '"' >> branch.txt

ls -ltr | head -10

## Some useful commands
sed -n '1,3'p test.sh	------> prints 1 to 3 lines [p -> print /n-> number ]

awk '{print}' test.sh	-------> prints the whole file

awk /manager/'{print}' test.sh prints lines with "manager" word

awk -F'[.]' '/^version/{print $1"."$2"."$3"."$4+1}' test.sh

version=1.2.3.4 -- Version Increment

sed 's/tenth/eleven/g' test.sh -> Replace a value in a file hello=DevOps=learners

echo $hello | sed 's/=/ /g' | awk '{print $2}'


# Thank YOU !

## Stay CONNECTED with Me !!

https://www.youtube.com/channel/UCNwP7KEElaJ7cdDTLP-KbBg

https://www.linkedin.com/in/azizul-maqsud/

https://azizulmaqsud-1684501031000.hashnode.dev/

https://medium.com/@azizulmaqsud

https://twitter.com/Sohail2me

https://github.com/azizulmaqsud
