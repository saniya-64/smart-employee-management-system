# smart-employee-management-system
A responsive employee management system built using HTML, CSS and JavaScript.
<!-- HEADER -->

<header class="header">

    <div class="logo">
        Employee<span>Hub</span>
    </div>

    <nav>
        <a href="#dashboard">Dashboard</a>
        <a href="#employees">Employees</a>
        <a href="#addEmployee">Add Employee</a>
    </nav>

    <button class="theme-btn" onclick="toggleDarkMode()">
        🌙
    </button>

</header>


<main class="container">

    <!-- DASHBOARD -->

    <section id="dashboard">

        <div class="welcome">

            <div>
                <h1>Smart Employee Dashboard</h1>

                <p>
                    Manage employees, performance and company records.
                </p>
            </div>

            <button class="add-btn" onclick="openForm()">
                + Add Employee
            </button>

        </div>


        <!-- STATISTICS -->

        <div class="dashboard-cards">

            <div class="card">
                <div class="card-icon">👥</div>

                <div>
                    <p>Total Employees</p>
                    <h2 id="totalEmployees">0</h2>
                </div>
            </div>


            <div class="card">
                <div class="card-icon">🟢</div>

                <div>
                    <p>Active Employees</p>
                    <h2 id="activeEmployees">0</h2>
                </div>
            </div>


            <div class="card">
                <div class="card-icon">🟡</div>

                <div>
                    <p>On Leave</p>
                    <h2 id="leaveEmployees">0</h2>
                </div>
            </div>


            <div class="card">
                <div class="card-icon">💰</div>

                <div>
                    <p>Average Salary</p>
                    <h2 id="averageSalary">₹0</h2>
                </div>
            </div>


            <div class="card">
                <div class="card-icon">⭐</div>

                <div>
                    <p>Average Rating</p>
                    <h2 id="averageRating">0</h2>
                </div>
            </div>


            <div class="card">
                <div class="card-icon">🏢</div>

                <div>
                    <p>Departments</p>
                    <h2 id="totalDepartments">0</h2>
                </div>
            </div>

        </div>


        <!-- ANALYTICS -->

        <div class="analytics">

            <div class="analytics-card">

                <h3>Department Overview</h3>

                <div id="departmentAnalytics"></div>

            </div>


            <div class="analytics-card">

                <h3>Top Performer</h3>

                <div id="topPerformer">
                    No employee available.
                </div>

            </div>

        </div>

    </section>


    <!-- EMPLOYEES -->

    <section id="employees" class="employee-section">

        <div class="section-heading">

            <div>
                <h2>Employee Records</h2>

                <p>
                    Search, filter and manage employees.
                </p>
            </div>

        </div>


        <!-- SEARCH AND FILTER -->

        <div class="filters">

            <div class="search-box">

                🔍

                <input
                    type="text"
                    id="searchInput"
                    placeholder="Search employee..."
                    onkeyup="filterEmployees()"
                >

            </div>


            <select id="departmentFilter"
                    onchange="filterEmployees()">

                <option value="all">
                    All Departments
                </option>

                <option value="IT">IT</option>

                <option value="HR">HR</option>

                <option value="Finance">
                    Finance
                </option>

                <option value="Marketing">
                    Marketing
                </option>

                <option value="Sales">
                    Sales
                </option>

            </select>


            <select id="statusFilter"
                    onchange="filterEmployees()">

                <option value="all">
                    All Status
                </option>

                <option value="Active">
                    Active
                </option>

                <option value="On Leave">
                    On Leave
                </option>

                <option value="Inactive">
                    Inactive
                </option>

            </select>


            <button class="export-btn"
                    onclick="exportCSV()">

                📥 Export CSV

            </button>

        </div>


        <!-- TABLE -->

        <div class="table-container">

            <table>

                <thead>

                    <tr>

                        <th>ID</th>

                        <th>Employee</th>

                        <th>Email</th>

                        <th>Department</th>

                        <th>Salary</th>

                        <th>Performance</th>

                        <th>Status</th>

                        <th>Actions</th>

                    </tr>

                </thead>


                <tbody id="employeeTableBody"></tbody>

            </table>


            <div id="noEmployee"
                 class="no-employee">

                <div>📋</div>

                <h3>No Employees Found</h3>

                <p>
                    Try changing your search or filters.
                </p>

            </div>

        </div>

    </section>


    <!-- ADD / EDIT FORM -->

    <section id="addEmployee"
             class="form-section">

        <div class="form-container">

            <div class="form-heading">

                <h2 id="formTitle">
                    Add New Employee
                </h2>

                <p>
                    Enter employee details below.
                </p>

            </div>


            <form id="employeeForm">

                <input type="hidden"
                       id="employeeId">


                <div class="form-grid">


                    <div class="form-group">

                        <label>
                            Full Name
                        </label>

                        <input
                            type="text"
                            id="name"
                            placeholder="Enter full name"
                            required
                        >

                    </div>


                    <div class="form-group">

                        <label>
                            Email
                        </label>

                        <input
                            type="email"
                            id="email"
                            placeholder="Enter email"
                            required
                        >

                    </div>


                    <div class="form-group">

                        <label>
                            Phone
                        </label>

                        <input
                            type="tel"
                            id="phone"
                            placeholder="10 digit phone number"
                            pattern="[0-9]{10}"
                            required
                        >

                    </div>


                    <div class="form-group">

                        <label>
                            Department
                        </label>

                        <select id="department"
                                required>

                            <option value="">
                                Select Department
                            </option>

                            <option value="IT">
                                IT
                            </option>

                            <option value="HR">
                                HR
                            </option>

                            <option value="Finance">
                                Finance
                            </option>

                            <option value="Marketing">
                                Marketing
                            </option>

                            <option value="Sales">
                                Sales
                            </option>

                        </select>

                    </div>


                    <div class="form-group">

                        <label>
                            Salary
                        </label>

                        <input
                            type="number"
                            id="salary"
                            min="0"
                            placeholder="Enter salary"
                            required
                        >

                    </div>


                    <div class="form-group">

                        <label>
                            Joining Date
                        </label>

                        <input
                            type="date"
                            id="joinDate"
                            required
                        >

                    </div>


                    <div class="form-group">

                        <label>
                            Employee Status
                        </label>

                        <select id="status"
                                required>

                            <option value="Active">
                                🟢 Active
                            </option>

                            <option value="On Leave">
                                🟡 On Leave
                            </option>

                            <option value="Inactive">
                                🔴 Inactive
                            </option>

                        </select>

                    </div>


                    <div class="form-group">

                        <label>
                            Performance Rating
                        </label>

                        <select id="rating"
                                required>

                            <option value="5">
                                ⭐⭐⭐⭐⭐ Excellent
                            </option>

                            <option value="4">
                                ⭐⭐⭐⭐ Very Good
                            </option>

                            <option value="3">
                                ⭐⭐⭐ Good
                            </option>

                            <option value="2">
                                ⭐⭐ Needs Improvement
                            </option>

                            <option value="1">
                                ⭐ Poor
                            </option>

                        </select>

                    </div>

                </div>


                <div class="form-buttons">

                    <button
                        type="submit"
                        class="save-btn">

                        Save Employee

                    </button>


                    <button
                        type="button"
                        class="cancel-btn"
                        onclick="resetForm()">

                        Cancel

                    </button>

                </div>

            </form>

        </div>

    </section>

</main>


<!-- PROFILE MODAL -->

<div id="profileModal"
     class="modal">

    <div class="modal-content">

        <button class="close-btn"
                onclick="closeProfile()">
            ×
        </button>

        <div id="profileContent"></div>

    </div>

</div>


<footer>

    <p>
        © 2026 Smart Employment Management System
    </p>

</footer>


<script src="script.js"></script>
