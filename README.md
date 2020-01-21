# MongoDB
Hands on with MongoDB

<h1>Configuration</h1>

<p>Mongo Installation directory, like:</p>
<li>C:\Program Files\MongoDB\Server\4.2</li>
</br>

<p>Create two folders (if its not already there), named as:</p>
<li>data</li>
<li>log</li>
</br>

<p>Inside data folder, create another folder named as:</p>
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
<li>use <strong>myuserprofiles</strong></li>
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

<p>Create Collection:</p>
<pre>db.createCollection('userprofiles');</pre>

<p>Show all Collections:</p>
<li>Type, <strong>show collections</strong></li>

<p>Insert Document:</p>
<pre>db.userprofiles.insert({
	first_name: "Muhammad Ubaid",
	middle_name: "Ur",
	last_name: "Raheem",
	gender: "Male"
});</pre>

<p>Show Document:</p>
<pre>db.userprofiles.find();</pre>

<p>Add Multiple Documents:</p>
<pre>db.userprofile.insert({
	first_name: "John",
	last_name: "Smith"
},
{
	first_name: "David",
	last_name: "Jones"
}
);</pre>

<p>Add new field on the fly:</p>
<pre>db.userprofiles.insert({
	first_name: "Michael",
	last_name: "Lee"
},
{
	first_name: "Maria",
	last_name: "Lopez",
	gender: "Female"
}
);</pre>

<p>Format the display:</p>
<pre>db.userprofiles.find().pretty();</pre>

<p>Update DB and add field:</p>
<strong>//first_name:"Muhammad Ubaid" is a matching criteria</strong>
<pre>db.userprofiles.update({first_name:"Muhammad Ubaid"}, {first_name:"Muhammad Ubaid", last_name:"Raheem", age:35});</pre>

<p>SET Operator:</p>
<strong>Update DB and add field Using SET operator:</strong>
<pre>db.userprofiles.update({first_name:"Michael"}, {$set:{gender:"Male"}});</pre>

<p>INC Operator:</p>
<strong>First update the existing record:</strong>
<pre>db.userprofiles.update({first_name:"David"}, {$set:{age:35}});</pre>

<strong>Increment existing age with 5</strong>
<pre>db.userprofiles.update({first_name:"Ubaid"}, {$inc:{age:5}});</pre>

<p>Update DB and remove field Using UNSET Operator:</p>
<pre>db.userprofiles.update({first_name:"Muhammad Ubaid"}, {$unset:{age:1}});</pre>

<p>UPSERT Operator:</p>
<strong>Trying to Update the record which is not exist:</strong>
<pre>db.userprofiles.update({first_name:"Sarah"}, {first_name:"Sarah", last_name:"James"});</pre>

<p>No records updated since there is no record available with matching criteria:</p>
<pre>db.userprofiles.update({first_name:"Sarah"}, {first_name:"Sarah", last_name:"James"}, {upsert: true});</pre>
<p>Record Inserted/Upserted</p>

<p>Rename Operator:</p>
<pre>db.userprofiles.update({first_name:"Michael"}, {$rename:{"gender":"sex"}});</pre>
<p>GENDER field has been renamed to SEX for the record matched as Michael</p>

<p>Remove Docuements:</p>
<pre>db.userprofiles.remove({first_name:"John"});</pre>

<p>Find by First Name:</p>
<pre>db.userprofiles.find({first_name: "Maria"});</pre>

<p>OR Operator:</p>
<pre>db.userprofiles.find({$or:[{first_name: "Muhammad Ubaid"}, {first_name: "Michael"}]});</pre>

<p>Find by Other fields:</p>
<pre>db.userprofiles.find({gender: "Male"});</pre>

<p><strong><</strong> Operator (<strong>use lt</strong>):</p>
<pre>db.userprofiles.find({age:{$lt:40}}).pretty();</pre>

<p><strong>></strong> Operator (<strong>use gt</strong>):</p>
<pre>db.userprofiles.find({age:{$gt:40}}).pretty();</pre>

<p><strong><=</strong> Operator (<strong>use lte</strong>):</p>
<pre>db.userprofiles.find({age:{$lte:40}}).pretty();</pre>

<p><strong>>=</strong> Operator (<strong>use gte</strong>):</p>
<pre>db.userprofiles.find({age:{$gte:40}}).pretty();</pre>

<p>Query in Object:</p>
<pre>db.userprofiles.find({"address.city":"Karachi"}).pretty();</pre>

<p>Query in Array:</p>
<pre>db.userprofiles.find({memberships: "mem1"}).pretty();</pre>

<p>Soring:</p>
<p>Sort by Last Name</p>
<p><strong>1 is used for ASC</strong></p>
<p><strong>-1 is used for DESC</strong></p>
<pre>db.userprofiles.find().sort({last_name: 1}); // 1 is used for ASC</pre>

<p>Count All Documents:</p>
<pre>db.userprofiles.find().count();</pre>

<p>Count Documents by Query Parameter:</p>
<pre>db.userprofiles.find({gender: "Male"}).count();</pre>

<p>Limit:</p>
<pre>db.userprofiles.find().limit(4);</pre>

<p>Limit with Sort:</p>
<pre>db.userprofiles.find().limit(4).sort({last_name: 1});</pre>

<p>For Each Loop:</p>
<pre>db.customers.find().forEach(function(doc){print("Customer Name: " + doc.first_name)});</pre>

<p>Insert String, Object and Array Data:</p>
<pre>db.customers.insert([
			{
				<strong>// String</strong>
				first_name: "Mike",
				last_name: "Jones",
				gender: "",
				age: 35,
				<strong>// Object</strong>
				address: {
						street: "",
						city: "",
						state: ""
				},				
				<strong>Array</strong>
				memberships: ["mem1", "mem2"],
				balance: 125.32,
			}
]);</pre>
