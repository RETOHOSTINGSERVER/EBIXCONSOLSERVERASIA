<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EBIXCONSOLPORTAL - Admin Portal</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        
        body {
            background-color: #f0f0f0;
            color: #333;
        }
        
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        
        .login-box {
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
            width: 350px;
            text-align: center;
        }
        
        .login-box h2 {
            margin-bottom: 20px;
            color: #444;
        }
        
        .login-box input {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        
        .login-box button {
            width: 100%;
            padding: 12px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
        }
        
        .login-box button:hover {
            background-color: #45a049;
        }
        
        .footer {
            margin-top: 20px;
            font-size: 12px;
            color: #777;
        }
        
        /* Admin Dashboard Styles */
        .admin-dashboard {
            display: none;
            background-color: #333;
            color: white;
            min-height: 100vh;
        }
        
        .header {
            background-color: #222;
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .clock {
            font-size: 18px;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .user-info button {
            padding: 5px 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }
        
        .main-content {
            padding: 20px;
            background-color: #444;
        }
        
        .form-section {
            background-color: #555;
            padding: 20px;
            border-radius: 5px;
            margin-bottom: 20px;
        }
        
        .form-section h3 {
            margin-bottom: 15px;
            color: #4CAF50;
        }
        
        .form-row {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .form-group {
            flex: 1;
            min-width: 200px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 5px;
            color: #ddd;
        }
        
        .form-group input, .form-group select {
            width: 100%;
            padding: 8px;
            border: 1px solid #777;
            border-radius: 4px;
            background-color: #666;
            color: white;
        }
        
        .status-options {
            display: flex;
            gap: 15px;
            margin-top: 10px;
        }
        
        .status-option {
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .action-buttons {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }
        
        .action-buttons button {
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        
        .save-btn {
            background-color: #4CAF50;
            color: white;
        }
        
        .print-btn {
            background-color: #2196F3;
            color: white;
        }
        
        .delete-btn {
            background-color: #f44336;
            color: white;
        }
        
        .file-upload {
            margin-top: 20px;
        }
        
        .file-upload label {
            display: block;
            margin-bottom: 5px;
            color: #ddd;
        }
        
        .records-summary {
            background-color: #555;
            padding: 15px;
            border-radius: 5px;
            margin-top: 20px;
        }
        
        .summary-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }
        
        .summary-item {
            text-align: center;
            flex: 1;
        }
        
        .summary-count {
            font-size: 24px;
            font-weight: bold;
            color: #4CAF50;
        }
        
        .records-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            background-color: #666;
        }
        
        .records-table th, .records-table td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #777;
        }
        
        .records-table th {
            background-color: #444;
            color: #4CAF50;
        }
        
        .records-table tr:hover {
            background-color: #555;
        }
        
        .filter-section {
            margin-bottom: 20px;
            display: flex;
            gap: 10px;
            align-items: center;
        }
        
        .filter-section select, .filter-section button {
            padding: 8px 12px;
            border-radius: 4px;
            border: none;
        }
        
        .filter-section button {
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }
        
        .view-records-btn {
            background-color: #2196F3;
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-top: 20px;
        }
        
        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            overflow: auto;
        }
        
        .modal-content {
            background-color: #555;
            margin: 5% auto;
            padding: 20px;
            width: 80%;
            max-width: 900px;
            border-radius: 5px;
        }
        
        .close-btn {
            float: right;
            font-size: 24px;
            cursor: pointer;
        }
        
        /* Change Password Modal */
        .change-password-modal {
            display: none;
        }
        
        .change-password-form {
            margin-top: 20px;
        }
        
        .change-password-form input {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border-radius: 4px;
            border: 1px solid #777;
            background-color: #666;
            color: white;
        }
        
        .change-password-form button {
            padding: 10px 15px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <!-- Login Section -->
    <div class="login-container" id="login-section">
        <div class="login-box">
            <h2>Admin Login</h2>
            <input type="text" id="username" placeholder="Username" required>
            <input type="password" id="password" placeholder="Password" required>
            <button onclick="login()">Login</button>
            <div class="footer">
                All Rights Reserved By Dev Makwana EBIXCONSOLPORTAL
            </div>
        </div>
    </div>
    
    <!-- Admin Dashboard -->
    <div class="admin-dashboard" id="admin-dashboard">
        <div class="header">
            <div class="logo">EBIXCONSOLPORTAL</div>
            <div class="clock" id="live-clock"></div>
            <div class="user-info">
                <span>Welcome, Admin</span>
                <button onclick="openChangePasswordModal()">Change Password</button>
                <button onclick="logout()">Logout</button>
            </div>
        </div>
        
        <div class="main-content">
            <div class="filter-section">
                <select id="status-filter">
                    <option value="">All Records</option>
                    <option value="accept">Accept</option>
                    <option value="hold">Hold</option>
                    <option value="running">Running</option>
                    <option value="public-holiday">Public Holiday</option>
                </select>
                <button onclick="filterRecords()">Filter</button>
            </div>
            
            <div class="form-section">
                <h3>Customer Information</h3>
                <div class="form-row">
                    <div class="form-group">
                        <label for="customer-number">Customer Number</label>
                        <input type="text" id="customer-number" placeholder="Enter customer number">
                    </div>
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input type="text" id="name" placeholder="Enter name">
                    </div>
                    <div class="form-group">
                        <label for="surname">Surname</label>
                        <input type="text" id="surname" placeholder="Enter surname">
                    </div>
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="email">Email ID</label>
                        <input type="email" id="email" placeholder="Enter email">
                    </div>
                    <div class="form-group">
                        <label for="contact">Contact Number</label>
                        <input type="tel" id="contact" placeholder="Enter contact number">
                    </div>
                    <div class="form-group">
                        <label for="pincode">Pin Code</label>
                        <input type="text" id="pincode" placeholder="Enter pin code">
                    </div>
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="address">Address</label>
                        <input type="text" id="address" placeholder="Enter address">
                    </div>
                    <div class="form-group">
                        <label for="city">City/Village</label>
                        <input type="text" id="city" placeholder="Enter city/village">
                    </div>
                    <div class="form-group">
                        <label for="state">State</label>
                        <input type="text" id="state" placeholder="Enter state">
                    </div>
                </div>
                
                <div class="form-group">
                    <label>Country</label>
                    <input type="text" id="country" value="India" readonly>
                </div>
                
                <div class="action-buttons">
                    <button class="save-btn" onclick="saveCustomerInfo()">Save Customer Info</button>
                </div>
            </div>
            
            <div class="form-section">
                <h3>Machine Information</h3>
                <div class="form-row">
                    <div class="form-group">
                        <label for="machine-name">Machine Name</label>
                        <input type="text" id="machine-name" placeholder="Enter machine name">
                    </div>
                    <div class="form-group">
                        <label for="serial-number">Serial Number</label>
                        <input type="text" id="serial-number" placeholder="Enter serial number">
                    </div>
                </div>
                
                <div class="form-group">
                    <label>Machine Status</label>
                    <div class="status-options">
                        <div class="status-option">
                            <input type="radio" id="warranty" name="machine-status" value="warranty" checked>
                            <label for="warranty">Under Warranty</label>
                        </div>
                        <div class="status-option">
                            <input type="radio" id="out-of-warranty" name="machine-status" value="out-of-warranty">
                            <label for="out-of-warranty">Out of Warranty</label>
                        </div>
                        <div class="status-option">
                            <input type="radio" id="amc" name="machine-status" value="amc">
                            <label for="amc">AMC</label>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label>Record Status</label>
                    <div class="status-options">
                        <div class="status-option">
                            <input type="radio" id="accept" name="record-status" value="accept" checked>
                            <label for="accept">Accept</label>
                        </div>
                        <div class="status-option">
                            <input type="radio" id="hold" name="record-status" value="hold">
                            <label for="hold">Hold</label>
                        </div>
                        <div class="status-option">
                            <input type="radio" id="running" name="record-status" value="running">
                            <label for="running">Running</label>
                        </div>
                        <div class="status-option">
                            <input type="radio" id="public-holiday" name="record-status" value="public-holiday">
                            <label for="public-holiday">Public Holiday</label>
                        </div>
                    </div>
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="customer-remark">Customer Remark</label>
                        <input type="text" id="customer-remark" placeholder="Enter customer remark">
                    </div>
                    <div class="form-group">
                        <label for="parts-change-remark">Parts Change Remark</label>
                        <input type="text" id="parts-change-remark" placeholder="Enter parts change remark">
                    </div>
                </div>
                
                <div class="file-upload">
                    <label for="invoice-upload">Upload Invoice</label>
                    <input type="file" id="invoice-upload">
                    
                    <label for="zip-upload" style="margin-top: 10px;">Upload ZIP File</label>
                    <input type="file" id="zip-upload">
                </div>
                
                <div class="action-buttons">
                    <button class="save-btn" onclick="saveMachineInfo()">Save Machine Info</button>
                    <button class="print-btn" onclick="printRecord()">Print Record</button>
                    <button class="delete-btn" onclick="deleteRecord()">Delete Record</button>
                </div>
            </div>
            
            <div class="records-summary">
                <h3>Records Summary</h3>
                <div class="summary-row">
                    <div class="summary-item">
                        <div class="summary-count" id="total-count">0</div>
                        <div>Total Records</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-count" id="accept-count">0</div>
                        <div>Accept</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-count" id="hold-count">0</div>
                        <div>Hold</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-count" id="running-count">0</div>
                        <div>Running</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-count" id="holiday-count">0</div>
                        <div>Public Holiday</div>
                    </div>
                </div>
            </div>
            
            <button class="view-records-btn" onclick="openRecordsModal()">View All Records</button>
        </div>
    </div>
    
    <!-- Records Modal -->
    <div id="records-modal" class="modal">
        <div class="modal-content">
            <span class="close-btn" onclick="closeModal('records-modal')">&times;</span>
            <h2>All Records</h2>
            <table class="records-table">
                <thead>
                    <tr>
                        <th>Customer No</th>
                        <th>Name</th>
                        <th>Contact</th>
                        <th>Machine</th>
                        <th>Serial No</th>
                        <th>Status</th>
                        <th>Date</th>
                    </tr>
                </thead>
                <tbody id="records-table-body">
                    <!-- Records will be populated here -->
                </tbody>
            </table>
        </div>
    </div>
    
    <!-- Change Password Modal -->
    <div id="change-password-modal" class="modal change-password-modal">
        <div class="modal-content">
            <span class="close-btn" onclick="closeModal('change-password-modal')">&times;</span>
            <h2>Change Password</h2>
            <div class="change-password-form">
                <input type="password" id="current-password" placeholder="Current Password">
                <input type="password" id="new-password" placeholder="New Password">
                <input type="password" id="confirm-password" placeholder="Confirm New Password">
                <button onclick="changePassword()">Change Password</button>
            </div>
        </div>
    </div>
    
    <script>
        // Sample records data
        let records = [];
        
        // Update clock every second
        function updateClock() {
            const now = new Date();
            const options = { 
                timeZone: 'Asia/Kolkata',
                hour12: true,
                hour: '2-digit',
                minute: '2-digit',
                second: '2-digit',
                day: '2-digit',
                month: '2-digit',
                year: 'numeric'
            };
            const formatter = new Intl.DateTimeFormat('en-IN', options);
            const parts = formatter.formatToParts(now);
            
            let dateTime = {};
            parts.forEach(part => {
                dateTime[part.type] = part.value;
            });
            
            const clockStr = `${dateTime.day}/${dateTime.month}/${dateTime.year} ${dateTime.hour}:${dateTime.minute}:${dateTime.second} ${dateTime.dayPeriod}`;
            document.getElementById('live-clock').textContent = clockStr;
        }
        
        setInterval(updateClock, 1000);
        updateClock();
        
        // Login function
        function login() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (username === 'devmakwana12' && password === '12345') {
                document.getElementById('login-section').style.display = 'none';
                document.getElementById('admin-dashboard').style.display = 'block';
                updateSummary();
            } else {
                alert('Invalid username or password');
            }
        }
        
        // Logout function
        function logout() {
            document.getElementById('login-section').style.display = 'flex';
            document.getElementById('admin-dashboard').style.display = 'none';
            document.getElementById('username').value = '';
            document.getElementById('password').value = '';
        }
        
        // Save customer information
        function saveCustomerInfo() {
            const customerNumber = document.getElementById('customer-number').value;
            const name = document.getElementById('name').value;
            const surname = document.getElementById('surname').value;
            const email = document.getElementById('email').value;
            const contact = document.getElementById('contact').value;
            const address = document.getElementById('address').value;
            const city = document.getElementById('city').value;
            const state = document.getElementById('state').value;
            const pincode = document.getElementById('pincode').value;
            
            if (!customerNumber || !name || !contact) {
                alert('Please fill in required fields: Customer Number, Name, and Contact');
                return;
            }
            
            // Check if this is an existing record
            const existingIndex = records.findIndex(r => r.customerNumber === customerNumber);
            
            if (existingIndex >= 0) {
                // Update existing record
                records[existingIndex] = {
                    ...records[existingIndex],
                    name,
                    surname,
                    email,
                    contact,
                    address,
                    city,
                    state,
                    pincode,
                    updatedAt: new Date().toISOString()
                };
            } else {
                // Create new record with just customer info (machine info will be added later)
                records.push({
                    customerNumber,
                    name,
                    surname,
                    email,
                    contact,
                    address,
                    city,
                    state,
                    pincode,
                    country: 'India',
                    createdAt: new Date().toISOString(),
                    updatedAt: new Date().toISOString(),
                    status: 'accept' // default status
                });
            }
            
            alert('Customer information saved successfully');
            updateSummary();
        }
        
        // Save machine information
        function saveMachineInfo() {
            const customerNumber = document.getElementById('customer-number').value;
            const machineName = document.getElementById('machine-name').value;
            const serialNumber = document.getElementById('serial-number').value;
            const machineStatus = document.querySelector('input[name="machine-status"]:checked').value;
            const recordStatus = document.querySelector('input[name="record-status"]:checked').value;
            const customerRemark = document.getElementById('customer-remark').value;
            const partsChangeRemark = document.getElementById('parts-change-remark').value;
            
            if (!customerNumber) {
                alert('Please save customer information first');
                return;
            }
            
            if (!machineName || !serialNumber) {
                alert('Please fill in machine name and serial number');
                return;
            }
            
            const recordIndex = records.findIndex(r => r.customerNumber === customerNumber);
            
            if (recordIndex >= 0) {
                records[recordIndex] = {
                    ...records[recordIndex],
                    machineName,
                    serialNumber,
                    machineStatus,
                    status: recordStatus,
                    customerRemark,
                    partsChangeRemark,
                    updatedAt: new Date().toISOString()
                };
                
                alert('Machine information saved successfully');
                updateSummary();
            } else {
                alert('Please save customer information first');
            }
        }
        
        // Update summary counts
        function updateSummary() {
            document.getElementById('total-count').textContent = records.length;
            document.getElementById('accept-count').textContent = records.filter(r => r.status === 'accept').length;
            document.getElementById('hold-count').textContent = records.filter(r => r.status === 'hold').length;
            document.getElementById('running-count').textContent = records.filter(r => r.status === 'running').length;
            document.getElementById('holiday-count').textContent = records.filter(r => r.status === 'public-holiday').length;
        }
        
        // Filter records
        function filterRecords() {
            const status = document.getElementById('status-filter').value;
            let filteredRecords = records;
            
            if (status) {
                filteredRecords = records.filter(r => r.status === status);
            }
            
            // For now, just update the counts to reflect filtered records
            document.getElementById('accept-count').textContent = filteredRecords.filter(r => r.status === 'accept').length;
            document.getElementById('hold-count').textContent = filteredRecords.filter(r => r.status === 'hold').length;
            document.getElementById('running-count').textContent = filteredRecords.filter(r => r.status === 'running').length;
            document.getElementById('holiday-count').textContent = filteredRecords.filter(r => r.status === 'public-holiday').length;
        }
        
        // Open records modal
        function openRecordsModal() {
            const modal = document.getElementById('records-modal');
            const tbody = document.getElementById('records-table-body');
            
            // Clear existing rows
            tbody.innerHTML = '';
            
            // Add records to table
            records.forEach(record => {
                const row = document.createElement('tr');
                
                const date = new Date(record.updatedAt);
                const dateStr = `${date.getDate()}/${date.getMonth()+1}/${date.getFullYear()}`;
                
                row.innerHTML = `
                    <td>${record.customerNumber}</td>
                    <td>${record.name} ${record.surname || ''}</td>
                    <td>${record.contact}</td>
                    <td>${record.machineName || '-'}</td>
                    <td>${record.serialNumber || '-'}</td>
                    <td>${record.status.charAt(0).toUpperCase() + record.status.slice(1)}</td>
                    <td>${dateStr}</td>
                `;
                
                tbody.appendChild(row);
            });
            
            modal.style.display = 'block';
        }
        
        // Close modal
        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }
        
        // Open change password modal
        function openChangePasswordModal() {
            document.getElementById('change-password-modal').style.display = 'block';
        }
        
        // Change password
        function changePassword() {
            const current = document.getElementById('current-password').value;
            const newPass = document.getElementById('new-password').value;
            const confirm = document.getElementById('confirm-password').value;
            
            if (current !== '12345') {
                alert('Current password is incorrect');
                return;
            }
            
            if (newPass !== confirm) {
                alert('New passwords do not match');
                return;
            }
            
            if (newPass.length < 5) {
                alert('Password must be at least 5 characters');
                return;
            }
            
            alert('Password changed successfully');
            closeModal('change-password-modal');
            
            // In a real app, you would send this to the server to update
        }
        
        // Print record
        function printRecord() {
            const customerNumber = document.getElementById('customer-number').value;
            const record = records.find(r => r.customerNumber === customerNumber);
            
            if (!record) {
                alert('No record found for this customer number');
                return;
            }
            
            // In a real app, you would open a print-friendly page with the record details
            alert('Printing functionality would open a print dialog with the record details');
        }
        
        // Delete record
        function deleteRecord() {
            const customerNumber = document.getElementById('customer-number').value;
            
            if (!customerNumber) {
                alert('Please enter a customer number');
                return;
            }
            
            if (confirm('Are you sure you want to delete this record?')) {
                records = records.filter(r => r.customerNumber !== customerNumber);
                alert('Record deleted successfully');
                clearForm();
                updateSummary();
            }
        }
        
        // Clear form
        function clearForm() {
            document.getElementById('customer-number').value = '';
            document.getElementById('name').value = '';
            document.getElementById('surname').value = '';
            document.getElementById('email').value = '';
            document.getElementById('contact').value = '';
            document.getElementById('address').value = '';
            document.getElementById('city').value = '';
            document.getElementById('state').value = '';
            document.getElementById('pincode').value = '';
            document.getElementById('machine-name').value = '';
            document.getElementById('serial-number').value = '';
            document.getElementById('customer-remark').value = '';
            document.getElementById('parts-change-remark').value = '';
            document.getElementById('invoice-upload').value = '';
            document.getElementById('zip-upload').value = '';
        }
    </script>
</body>
</html>
