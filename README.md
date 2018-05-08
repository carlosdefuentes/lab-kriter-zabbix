<img src="\resources\jira-logo-scaled.png" alt="logo">
<div class="level1">
<p><strong>How to configure an Active Agent in Zabbix</strong></p>
<p>Zabbix Active checks require more complex processing: the agent must first retrieve a list of items from Zabbix server for independent processing, then it will periodically send new values to the server. Active checks are needed when it is not possible for the zabbix server to access a specific port on the remote monitored machine (for example this can be caused by a firewall).</p>
</div>
<div class="level2">
<p>Edit <code>/etc/zabbix/zabbix_agentd.conf</code> and set the following parameters</p>
<pre class="code">ServerActive=YOUR_SERVER_IP
Hostname=CLIENT_HOSTNAME</pre>
<p>In <code>ServerActive</code> you have the set one or more comma delimited Zabbix servers for active checks specifying the IP or the hostname. <code>Hostname</code> must be a unique, case sensitive hostname for this host: this value is required for active checks and must match the value configured on the server. </p>
<p>You can also set</p>
<pre class="code">StartAgents=0</pre>
<p>to disable the passive checks (not required, but reduces the number of unused processes)</p>
<p>Remember to restart the service with</p>
<pre class="code">service zabbix-agent restart</pre>
</div>
