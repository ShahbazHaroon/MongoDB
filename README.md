# MongoDB
Hands on with MongoDB

<h1>Configuration</h1>

<p>Mongo Installation directory, like:</p>
<li>C:\Program Files\MongoDB\Server\4.2</li>
</br>

<p>Create two folders (if its not already there), names as:</p>
<li>data</li>
<li>log</li>

<p>Inside data folder, create another folder names as:</p>
<li>db</li>

<p>go to command prompt, change directory to where mongo is installed, like:</p>
<li>C:\Program Files\MongoDB\Server\4.2</li>

<p>go to bin folder, like:</p>
<li>cd bin</li>

<p>Type: <strong>mongod --directoryperdb --dbpath C:\Program Files\MongoDB\Server\4.2\data\db --logpath C:\Program Files\MongoDB\Server\4.2\log\mongo.log --logappend --rest --install</strong></p>

<p>Start Mongo Service:</p>
<li>net start <strong>MongoDB</strong></li>

<p>Go to Mongo shell:</p>
<li>Type, <strong>mongo</strong></li>

<p>Show databases:</p>
<li>Type, <strong>show dbs</strong></li>

<p>Create New Database:</p>
<li>use <strong>myuserprofile</strong></li>

<p>Check Current Database:</p>
<li>Type <strong>db</strong></li>

<p>Create User:</p>
<li><pre>db.createUser({
	user: "root",
	pwd: "root",
	roles: ["readWrite", "dbAdmin"]
});</pre></li>
