<img src="\resources\jira-logo-scaled.png" alt="logo">
<p><strong>Install and configure Zabbix server</strong></p>
<p><br /><strong>a. Install Repository with MySQL database</strong><br /><br /># wget http://repo.zabbix.com/zabbix/3.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.4-1+xenial_all.deb<br /># dpkg -i zabbix-release_3.4-1+xenial_all.deb<br /># apt update</p>
<p><br /><strong>b. Install Zabbix server, frontend, agent</strong></p>
<p><br /># apt install zabbix-server-mysql zabbix-frontend-php zabbix-agent</p>
<p><br /><strong>c. Create initial database</strong><br /><br /># mysql -uroot -p<br />password</p>
<p>mysql&gt; create database zabbix character set utf8 collate utf8_bin;<br />mysql&gt; grant all privileges on zabbix.* to zabbix@localhost identified by 'password';<br />mysql&gt; quit;</p>
<p>Import initial schema and data. You will be prompted to enter your newly created password.</p>
<p><br /># zcat /usr/share/doc/zabbix-server-mysql*/create.sql.gz | mysql -uzabbix -p zabbix</p>
<p><strong>d. Configure the database for Zabbix server</strong><br />DBPassword=password</p>
<p><strong>e. Start Zabbix server and agent processes</strong></p>
<p>Start Zabbix server and agent processes and make it start at system boot:</p>
<p># systemctl restart zabbix-server zabbix-agent apache2<br /># systemctl enable zabbix-server zabbix-agent apache2</p>
<p><strong>f. Configure PHP for Zabbix frontend</strong></p>
<p><br />Edit file /etc/zabbix/apache.conf, uncomment and set the right timezone for you.<br /># php_value date.timezone Europe/Riga</p>
<p>Now your Zabbix server is up and running!</p>
<p>Configure Zabbix frontend</p>
<p>Connect to your newly installed Zabbix frontend: http://server_ip_or_name/zabbix<br />Follow steps described in Zabbix documentation: Installing frontend<br />Start using Zabbix</p>
