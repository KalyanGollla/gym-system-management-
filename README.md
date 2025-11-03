<!DOCTYPE html> 

<html lang="en"> 

<head> 

<meta charset="UTF-8"> 

<meta name="viewport" content="width=device-width, initial-scale=1.0"> 

<title>Gym Management System</title> 

<style> 

body { 

  font-family: Arial, sans-serif; 

  background: #f4f7fb; 

  margin: 0; 

  padding: 20px; 

} 

  

h1 { text-align: center; color: #2b6cb0; } 

  

.container { 

  max-width: 800px; 
																																													
  margin: auto; 

  background: #fff; 

  padding: 20px; 

  border-radius: 10px; 

} 

  

input, select, button { 

  padding: 8px; 

  margin: 5px 0; 

  width: 100%; 

  border-radius: 5px; 

  border: 1px solid #ccc; 

} 

  

table { 

  width: 100%; 

  border-collapse: collapse; 

  margin-top: 10px; 

} 

  

th, td { 

  border: 1px solid #ddd; 

  padding: 8px; 

  text-align: left; 

} 

  

th { 

  background: #2b6cb0; 

  color: white; 

} 

  

button { 

  background: #2b6cb0; 

  color: white; 

  border: none; 

  cursor: pointer; 

} 

  

button:hover { background: #1e4f8f; } 

</style> 

</head> 

<body> 

<h1>Gym Management System</h1> 

<div class="container"> 

  <h3>Add Member</h3> 

  <input type="text" id="name" placeholder="Enter name"> 

  <input type="text" id="phone" placeholder="Enter phone number"> 

  <select id="package"> 

    <option value="Monthly">Monthly - 1000</option> 

    <option value="Quarterly">Quarterly - 2700</option> 

    <option value="Yearly">Yearly - 10000</option> 

  </select> 

  <button onclick="addMember()">Add Member</button> 

  

  <h3>Members List</h3> 

  <table id="memberTable"> 

    <thead> 

      <tr><th>Name</th><th>Phone</th><th>Package</th></tr> 

    </thead> 

    <tbody></tbody> 

  </table> 

  

  <h3>Create Bill</h3> 

  <select id="billMember"></select> 

  <input type="number" id="amount" placeholder="Enter amount"> 

  <input type="date" id="date"> 

  <button onclick="createBill()">Add Bill</button> 

  

  <h3>Billing Records</h3> 

  <table id="billTable"> 

    <thead> 

      <tr><th>Member</th><th>Amount</th><th>Due Date</th></tr> 

    </thead> 

    <tbody></tbody> 

  </table> 

</div> 

  

<script> 

let members = []; 

let bills = []; 

  

// Add Member 

function addMember() { 

  const name = document.getElementById('name').value; 

  const phone = document.getElementById('phone').value; 

  const pack = document.getElementById('package').value; 

  if (!name || !phone) return alert('Please fill all fields'); 

  members.push({name, phone, pack}); 

  updateMembers(); 

  updateBillMembers(); 

  document.getElementById('name').value = ''; 

  document.getElementById('phone').value = ''; 

} 

  

// Update Members Table 

function updateMembers() { 

  const tbody = document.querySelector('#memberTable tbody'); 

  tbody.innerHTML = ''; 

  members.forEach(m => { 

    const row = `<tr><td>${m.name}</td><td>${m.phone}</td><td>${m.pack}</td></tr>`; 

    tbody.innerHTML += row; 

  }); 

} 

  

// Update Bill Dropdown 

function updateBillMembers() { 

  const select = document.getElementById('billMember'); 

  select.innerHTML = ''; 

  members.forEach(m => { 

    const opt = document.createElement('option'); 

    opt.value = m.name; 

    opt.textContent = m.name; 

    select.appendChild(opt); 

  }); 

} 

  

// Create Bill 

function createBill() { 

  const member = document.getElementById('billMember').value; 

  const amount = document.getElementById('amount').value; 

  const date = document.getElementById('date').value; 

  if (!member || !amount || !date) return alert('Please fill all fields'); 

  bills.push({member, amount, date}); 

  updateBills(); 

  document.getElementById('amount').value = ''; 

  document.getElementById('date').value = ''; 

} 

  

// Update Bills Table 

function updateBills() { 

  const tbody = document.querySelector('#billTable tbody'); 

  tbody.innerHTML = ''; 

  bills.forEach(b => { 

    const row = `<tr><td>${b.member}</td><td>${b.amount}</td><td>${b.date}</td></tr>`; 

    tbody.innerHTML += row; 

  }); 

} 

</script> 

</body> 

</html> 
