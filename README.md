# BI_Alternative
 Exploring, comparing different tools to perform the best experience for BI

---
To complete this project, there is some constraint and steps to follow
- [x] Create an evolutive documentation
- [x] Understood current usage in my compagny
  - [x] architecture
  - [x] manipulate
  - [x] constraint
- [x] Search and document
  - [x] Find multiples tools
  - [x] Compare them
  - [x] find there requirement
- [x] Select few solutions
- [ ] Create Poof Of Concept (POC)
- [ ] Adopt a solution
  - [ ] meeting to present works done
  - [ ] vote the one most appropriate solution
- [ ] Apply the solution
---

## Research concerning BI tools
 Here is a none comprehensive list of tools for BI:

| BI name | popularity ranking | License | Consistent Database | Users right | User Friendly | Language | Main Features |
| :------------- | :------------- | :------------- | :------------- |:------------- | :------------- |:------------- |:------------- |
| Kibana | Medium | Open Source | Elastic Search | ? | Yes | EN, FR, SP,... | Data Visualization, Geospatial data, graph exploration, dashboard,... |
| Sisense | Best BI award | Quote-based | postgre, Mongo, Oracle, hadoop,... | yes | Yes | EN, FR, SP,... | Drag and drop, export to various format, Data Visualization, ...|
| QlikView | Hight | 15$ per user/month | postgre, Mongo, MYSQL, ... | yes | Yes | EN | unusable on linux server |
| SSAS POWERBI | Hight | Quote-based | SQL server | yes | no | EN, FR | unusable on linux server |
| TABLEAU | Hight | Quote-based | Postgre, MariaDB, Oracle, Hadoop | ? | yes | EN, FR | Drag and drop, mobile ready, data sharing, ... |

## POC
**The server need [python](https://doc.ubuntu-fr.org/python) in order to receive ansible command, port 22 open, (8cpu, 16GRam, 50GB for Sisense)**
To test BI tools, I'm using my own ubuntu server with automatisation deployement with ansible . Think to uncomment the content of [playbook_test](https://github.com/JujuDesFruits/BI_Alternative/blob/master/playbook_test.yml) to test the BI you want select the server you work on.  
To start the deployement, copy this command line ([ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) is required on local machin)
```
ansible-playbook playbook_test.yml -i TEST --extra-vars "ansible_ssh_pass=$passwd ansible_sudo_pass=$passwd"
```
---
##### FOR KIBANA
After executing the command from above, you have to change password from elasticsearch to enable kibana to link them. To do so, go to **/usr/share/elasticsearch/** then type:
```
bin/elasticsearch-setup-passwords auto
```
then past the password for kibana on [kibana.yml](https://github.com/JujuDesFruits/BI_Alternative/blob/master/roles/kibana/templates/kibana.yml) or change the password using the new password on doing this:
```
curl -u elastic:<password_elastic> -XPUT 'http://localhost:9200/_xpack/security/user/kibana/_password?pretty' -H 'Content-Type: application/json' -d'{"password" : "<new_password>"}'
```
Dont forget to open port 5601.
---
#### FOR TABLEAU
First you'll need to download this file [tableau-server.deb](https://downloads.tableau.com/esdalt/2019.1.10/tableau-server-2019-1-10_amd64.deb)from the tableau website and copy it in [roles/tableau/debian_install/](https://github.com/JujuDesFruits/BI_Alternative/blob/master/roles/tableau/debian_install/). You may update [playbook_test](https://github.com/JujuDesFruits/BI_Alternative/blob/master/playbook_test.yml) and replace **<user_tableau>** by your own user name on your server. Then start execute the command line ansible. That's it, enjoy !
Dont forget to open port 8850.
---
#### FOR SISENSE
For this you gonna need to contact directly sisense to receive latest linux archive and your licence. Then copy the tar file in [roles/tableau/debian_install/](https://github.com/JujuDesFruits/BI_Alternative/blob/master/roles/tableau/debian_install/). You may update [playbook_test](https://github.com/JujuDesFruits/BI_Alternative/blob/master/playbook_test.yml) and replace **<your_file_name>** by your own tar name.  
Start the playbook. That's it, enjoy!   
Dont forget to open port 30845
---
