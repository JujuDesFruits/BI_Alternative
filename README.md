# BI_Alternative
 Exploring, comparing different tools to perform the best experience for BI

---
To complete this project, there is some constraint and steps to follow
- [x] Create an evolutive documentation
- [ ] Understood current usage
  - [x] architecture
  - [ ] manipulate
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
| Kibana | new | Open Source | Elastic Search | ? | Yes | EN, FR, SP,... | Data Visualization, Geospatial data, graph exploration, dashboard,... |
| Sisense | Best BI award | Quote-based | postgre, Mongo, Oracle, hadoop,... | yes | Yes | EN, FR, SP,... | Drag and drop, export to various format, Data Visualization, ...|
| QlikView | Hight | 15$ per user/month | postgre, Mongo, MYSQL, ... | yes | Yes | EN | Data Visualization, Interact with dynamic dashboard & analytics, mobile-ready, ...|s

## POC
To test BI tools, I'm using my own ubuntu server with automatisation deployement & docker. Think to uncomment the content of [playbook_test](https://github.com/JujuDesFruits/BI_Alternative/blob/master/playbook_test.yml) to test the BI you want.   
To start the deployement, copy this command line ([ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) is required)
```
ansible-playbook playbook_test.yml -i TEST --extra-vars "ansible_ssh_pass=$passwd ansible_sudo_pass=$passwd"
```
