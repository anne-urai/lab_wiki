---
layout: default
title: Data collection and management
rank: 9
---

If you are going to collect data, either in person or online, there are lots of resources at Leiden University to help you.
- [Ethical approval](https://www.organisatiegids.universiteitleiden.nl/faculteiten-en-instituten/sociale-wetenschappen/instituten/psychologie/commissie-ethiek?_ga=2.35655075.2008115849.1611051865-572952841.1580558528){:target="_blank"}
- [Data management](https://www.organisatiegids.universiteitleiden.nl/faculteiten-en-instituten/sociale-wetenschappen/instituten/psychologie/wetenschapscommissie?_ga=2.39830048.2008115849.1611051865-572952841.1580558528){:target="_blank"}
- [Data archiving](https://www.organisatiegids.universiteitleiden.nl/binaries/content/assets/sociale-wetenschappen/psychologie/organisatiegids/guidelines-for-the-archiving-of-academic-research-for-faculties-of-bss-n.._.pdf){:target="_blank"}

### Collecting online data
SOLO is the main source of support at the university. Here are their main channels:
-   [SOLO Research Wiki](https://researchwiki.solo.universiteitleiden.nl/): here you can find technical documentation about SOLO supported research tools and platforms. It also contains a link to the latest versions of the COVID-19 protocols.
-   [SOLO Online Research Teams](https://teams.microsoft.com/dl/launcher/launcher.html?url=%2F_%23%2Fl%2Fteam%2F19%3Aa835506e63074e07b2d4a4d93f8a2064%40thread.tacv2%2Fconversations%3FgroupId%3Dd5721348-8915-4a3a-8d36-419035d72fbe%26tenantId%3Dca2a7f76-dbd7-4ec0-9108-6b3d524fb7c8&type=team&deeplinkId=85d76503-abff-4b64-8e89-d12da7a10658&directDl=true&msLaunch=true&enableMobilePage=true&suppressPrompt=true#): meant for everybody doing online research. Here ideas can be shared and questions asked to colleagues or SOLO employees concerning online research.

### Collecting in-person data
- Login to the [ethics application portal](https://researchsupport-fsw.universiteitleiden.nl/) to help edit (if applicable).
- Get access to the Sylvius labs via SOLO (Maureen Meekel). This includes access to the room booking system.
- Get access to the project J-drive (ask Anne) - see below for accessing with Cyberduck.
- Make a [SONA](https://ul.sona-systems.com/all_exp.aspx?personal=1) account for participant recruitment. Add a slide [here](https://leidenuniv1.sharepoint.com/:p:/r/sites/SSHLabresearch/_layouts/15/Doc.aspx?sourcedoc=%7BA885A6F7-2855-46F7-8335-ACCD3190636B%7D&file=Research_Advertisments.pptx&action=edit&mobileredirect=true) for your advertisement to be shown in screens in the Sylvius building.
- See [here](https://docs.google.com/document/d/1C6Kt_tYg0wLJQ1GE0N0mQVeitvk-i0vjs0vuYjYIJsQ/edit) for a guide to collecting behavioral data in a visual decision task, written by Annika Frach and Camilla Enwereuzor. See [here]([https://docs.google.com/document/d/1V](https://docs.google.com/document/d/1VZZZ1K3NHQlPGUveSB9ozum1Ab8ZEbqJ-56SzgmNSIE/edit?tab=t.0)) for instructions on running a group decision-making study, written by Alisa Wirtnik and Eveline de Bie.

### Storing and loading internal data
* Data from experiments run in the lab should be stored on the J-drive: `WORKGROUPS/FSW/PROJECT-NAME`. Anne will request access for you at the start of the project. The J-drive can be accessed from the lab computers: when you are logged in with your account, you should see the J-drive appear next to other network drives. 

#### Accessing the J-drive on your own computer:
a) Cyberduck
- Download the [Cyberduck](https://cyberduck.io/download/) software (see [here](https://researchwiki.solo.universiteitleiden.nl/xwiki/wiki/researchwiki.solo.universiteitleiden.nl/view/Clusters/ALICE%20Cluster/#HDataTransfer) and [here](https://researchwiki.solo.universiteitleiden.nl/xwiki/wiki/researchwiki.solo.universiteitleiden.nl/view/Facilities/LIBC%20MRI%20Scanner/#HExportPACStoJ-Drive) for more setup instructions.
* After you have downloaded Cyberduck, start a new connection:
  * choose **sFTP**
  * Server: sftpgw.leidenuniv.nl
  * Username: your Leiden username
  * Password: your Leiden password
  * SSH Private Key: None
  * Path: /winshare/Public/Workgroups/FSW/PROJECT-NAME
  * Transfer files: Default
  * Encoding: UTF-8
* Note: if you'd like to avoid copying these data to your local drive for analysis, you can download the MountainDuck software and mount the J-drive as if it were a regular network drive. This should give you a direct path to the data (see [here](https://github.com/anne-urai/human_ibl_snapshots/blob/main/snapshot_all.py#L33) for an example, ask Anne or Philippa for more info). 

 b) EduVPN
 * Download [EduVPN](https://www.eduvpn.org/client-apps/) software
 * After you have downloaded the software, log into your Leiden University account
 * If student: use your student number (s_______) and your password
 * When logged in, the EduVPN window will pop up, it needs to be turned on (green light) to work
 * The J-drive will appear under "This PC"
 * Note: This only works for Windows users.
 
