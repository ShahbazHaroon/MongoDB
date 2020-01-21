# MongoDB
Hands on with MongoDB

<h1>Configuration</h1>

<p>Mongo Installation directory, like:</p>
<li>C:\Program Files\MongoDB\Server\4.2</li>
</br>

<p>Create two folders (if its not already there), names as:</p>
<li>data</li>
<li>log</li>
</br>

<p>Inside data folder, create another folder names as:</p>
<li>db</li>
</br>

<p>go to command prompt, change directory to where mongo is installed, like:</p>
<li>C:\Program Files\MongoDB\Server\4.2</li>
</br>

<p>go to bin folder, like:</p>
<li>cd bin</li>
</br>

<p>Type: <strong>mongod --directoryperdb --dbpath C:\Program Files\MongoDB\Server\4.2\data\db --logpath C:\Program Files\MongoDB\Server\4.2\log\mongo.log --logappend --rest --install</strong></p>
</br>

<p>Start Mongo Service:</p>
<li>net start <strong>MongoDB</strong></li>
</br>

<p>Go to Mongo shell:</p>
<li>Type, <strong>mongo</strong></li>
</br>

<p>Show databases:</p>
<li>Type, <strong>show dbs</strong></li>
</br>

<p>Create New Database:</p>
<li>use <strong>myuserprofile</strong></li>
</br>

<p>Check Current Database:</p>
<li>Type <strong>db</strong></li>
</br>

<p>Create User:</p>
<pre>db.createUser({
	user: "root",
	pwd: "root",
	roles: ["readWrite", "dbAdmin"]
});</pre>
