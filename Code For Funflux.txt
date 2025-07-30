import React, { useState } from 'react';

// Main App Component
function App() {
  const [activeSection, setActiveSection] = useState('dashboard'); // State to manage active section

  // Function to render content based on active section
  const renderContent = () => {
    switch (activeSection) {
      case 'dashboard':
        return <Dashboard />;
      case 'loans':
        return <Loans />;
      case 'customers':
        return <Customers />;
      case 'reports':
        return <Reports />;
      case 'settings':
        return <Settings />;
      default:
        return <Dashboard />;
    }
  };

  return (
    <div className="flex h-screen bg-gray-100 font-sans">
      {/* Sidebar Navigation */}
      <Sidebar activeSection={activeSection} setActiveSection={setActiveSection} />

      {/* Main Content Area */}
      <div className="flex-1 flex flex-col overflow-hidden">
        {/* Top Bar / Header */}
        <header className="flex items-center justify-between p-4 bg-white border-b border-gray-200 shadow-sm">
          <h1 className="text-2xl font-semibold text-gray-800 capitalize">{activeSection} Overview</h1>
          <div className="flex items-center space-x-4">
            {/* User Profile Placeholder */}
            <div className="relative">
              <button className="flex items-center space-x-2 text-gray-700 hover:text-blue-600 focus:outline-none">
                <img
                  src="https://placehold.co/40x40/cbd5e1/4a5568?text=JD" // Placeholder image for user avatar
                  alt="User Avatar"
                  className="w-10 h-10 rounded-full border-2 border-blue-400"
                />
                <span className="font-medium hidden md:block">John Doe</span>
                <svg className="w-4 h-4 text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                  <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M19 9l-7 7-7-7"></path>
                </svg>
              </button>
              {/* Dropdown Menu (hidden for now) */}
              {/* <div className="absolute right-0 mt-2 w-48 bg-white rounded-md shadow-lg py-1 z-10">
                <a href="#" className="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Profile</a>
                <a href="#" className="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Settings</a>
                <a href="#" className="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Logout</a>
              </div> */}
            </div>
          </div>
        </header>

        {/* Main Content Area */}
        <main className="flex-1 overflow-x-hidden overflow-y-auto bg-gray-100 p-6">
          {renderContent()}
        </main>
      </div>
    </div>
  );
}

// Sidebar Component
const Sidebar = ({ activeSection, setActiveSection }) => {
  const navItems = [
    { name: 'Dashboard', icon: (
      <svg className="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001 1h3v-3m-3 3h3v-3m-3 0a1 1 0 001 1h3v-3m-3 3h3v-3m-3 0a1 1 0 001 1h3v-3m-3 3h3v-3m-3 0a1 1 0 001 1h3v-3"></path>
      </svg>
    )},
    { name: 'Loans', icon: (
      <svg className="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M17 9V7a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2m2 4h10a2 2 0 002-2v-6a2 2 0 00-2-2H9a2 2 0 00-2 2v6a2 2 0 002 2zm7-5a2 2 0 11-4 0 2 2 0 014 0z"></path>
      </svg>
    )},
    { name: 'Customers', icon: (
      <svg className="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M17 20h2a2 2 0 002-2V7a2 2 0 00-2-2h-2m-4 14v-2m6 2v-2M9 14V5l3-3m0 0l3 3m-3-3v8m0-13a2 2 0 012 2v6a2 2 0 01-2 2h-2a2 2 0 01-2-2V7a2 2 0 012-2h2z"></path>
      </svg>
    )},
    { name: 'Reports', icon: (
      <svg className="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"></path>
      </svg>
    )},
    { name: 'Settings', icon: (
      <svg className="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"></path>
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path>
      </svg>
    )},
  ];

  return (
    <div className="w-64 bg-gray-800 text-white flex flex-col rounded-r-lg shadow-lg">
      <div className="p-6 text-center border-b border-gray-700">
        <h2 className="text-3xl font-bold text-blue-400">Finflux</h2>
        <p className="text-sm text-gray-400">Lending Platform</p>
      </div>
      <nav className="flex-1 px-4 py-6 space-y-2">
        {navItems.map((item) => (
          <button
            key={item.name}
            onClick={() => setActiveSection(item.name.toLowerCase())}
            className={`flex items-center w-full px-4 py-3 rounded-lg transition-all duration-200 ease-in-out
              ${activeSection === item.name.toLowerCase()
                ? 'bg-blue-600 text-white shadow-md'
                : 'text-gray-300 hover:bg-gray-700 hover:text-white'
              }`}
          >
            {item.icon}
            <span className="ml-3 text-lg font-medium">{item.name}</span>
          </button>
        ))}
      </nav>
      <div className="p-4 text-center text-gray-400 text-sm border-t border-gray-700">
        &copy; 2024 Finflux Clone. All rights reserved.
      </div>
    </div>
  );
};

// Dashboard Component
const Dashboard = () => {
  const stats = [
    { title: 'Total Loans', value: '$12,500,000', change: '+15%', icon: (
      <svg className="w-8 h-8 text-blue-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8V9m0 3v2m0 3V15m0 0a3 3 0 110 6 3 3 0 010-6zm0 0V9m0 3v2m0 3V15m0 0a3 3 0 110 6 3 3 0 010-6z"></path>
      </svg>
    )},
    { title: 'Active Customers', value: '2,450', change: '+8%', icon: (
      <svg className="w-8 h-8 text-green-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M17 20h2a2 2 0 002-2V7a2 2 0 00-2-2h-2m-4 14v-2m6 2v-2M9 14V5l3-3m0 0l3 3m-3-3v8m0-13a2 2 0 012 2v6a2 2 0 01-2 2h-2a2 2 0 01-2-2V7a2 2 0 012-2h2z"></path>
      </svg>
    )},
    { title: 'Pending Applications', value: '187', change: '-2%', icon: (
      <svg className="w-8 h-8 text-yellow-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-3 7h3m-3 4h3m-6-4h.01M9 16h.01"></path>
      </svg>
    )},
    { title: 'Revenue (MTD)', value: '$500,000', change: '+10%', icon: (
      <svg className="w-8 h-8 text-purple-500" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M3 10h18M3 14h18m-9-4v8m-7 0h14a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2z"></path>
      </svg>
    )},
  ];

  const recentActivities = [
    { id: 1, type: 'Loan Approved', description: 'Loan application for John Doe approved.', time: '2 hours ago' },
    { id: 2, type: 'New Customer', description: 'Jane Smith onboarded as a new customer.', time: '5 hours ago' },
    { id: 3, type: 'Payment Received', description: 'Payment received for Loan ID #FLX00123.', time: '1 day ago' },
    { id: 4, type: 'Application Submitted', description: 'New loan application from Robert Brown.', time: '2 days ago' },
  ];

  return (
    <div className="space-y-6">
      {/* Stats Cards */}
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
        {stats.map((stat, index) => (
          <div key={index} className="bg-white rounded-xl shadow-md p-6 flex items-center space-x-4">
            <div className="p-3 rounded-full bg-gray-100">{stat.icon}</div>
            <div>
              <p className="text-gray-500 text-sm">{stat.title}</p>
              <h3 className="text-2xl font-bold text-gray-900">{stat.value}</h3>
              <p className={`text-sm ${stat.change.startsWith('+') ? 'text-green-500' : 'text-red-500'}`}>{stat.change} since last month</p>
            </div>
          </div>
        ))}
      </div>

      {/* Recent Activity Section */}
      <div className="bg-white rounded-xl shadow-md p-6">
        <h2 className="text-xl font-semibold text-gray-800 mb-4">Recent Activity</h2>
        <ul className="divide-y divide-gray-200">
          {recentActivities.map((activity) => (
            <li key={activity.id} className="py-3 flex items-center justify-between">
              <div>
                <p className="text-gray-900 font-medium">{activity.type}</p>
                <p className="text-gray-600 text-sm">{activity.description}</p>
              </div>
              <span className="text-gray-500 text-sm">{activity.time}</span>
            </li>
          ))}
        </ul>
        <button className="mt-4 w-full bg-blue-500 text-white py-2 px-4 rounded-lg hover:bg-blue-600 transition duration-200 ease-in-out">
          View All Activities
        </button>
      </div>

      {/* Placeholder for Charts/Graphs */}
      <div className="bg-white rounded-xl shadow-md p-6 h-64 flex items-center justify-center text-gray-400">
        <p>Placeholder for Loan Portfolio Growth Chart</p>
      </div>
    </div>
  );
};

// Loans Component
const Loans = () => {
  const loans = [
    { id: 'FLX00123', customer: 'John Doe', amount: '$50,000', status: 'Approved', type: 'Personal Loan', dueDate: '2025-12-01' },
    { id: 'FLX00124', customer: 'Jane Smith', amount: '$120,000', status: 'Pending', type: 'Home Loan', dueDate: 'N/A' },
    { id: 'FLX00125', customer: 'Robert Brown', amount: '$15,000', status: 'Disbursed', type: 'Vehicle Loan', dueDate: '2026-06-15' },
    { id: 'FLX00126', customer: 'Emily White', amount: '$30,000', status: 'Rejected', type: 'Business Loan', dueDate: 'N/A' },
  ];

  const getStatusColor = (status) => {
    switch (status) {
      case 'Approved': return 'bg-green-100 text-green-800';
      case 'Pending': return 'bg-yellow-100 text-yellow-800';
      case 'Disbursed': return 'bg-blue-100 text-blue-800';
      case 'Rejected': return 'bg-red-100 text-red-800';
      default: return 'bg-gray-100 text-gray-800';
    }
  };

  return (
    <div className="space-y-6">
      <div className="flex justify-between items-center mb-4">
        <h2 className="text-xl font-semibold text-gray-800">Loan Applications</h2>
        <button className="bg-blue-500 text-white py-2 px-4 rounded-lg hover:bg-blue-600 transition duration-200 ease-in-out">
          + Add New Loan
        </button>
      </div>
      <div className="bg-white rounded-xl shadow-md overflow-hidden">
        <table className="min-w-full divide-y divide-gray-200">
          <thead className="bg-gray-50">
            <tr>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Loan ID</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Customer</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Amount</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Type</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Due Date</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Actions</th>
            </tr>
          </thead>
          <tbody className="bg-white divide-y divide-gray-200">
            {loans.map((loan) => (
              <tr key={loan.id}>
                <td className="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{loan.id}</td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-700">{loan.customer}</td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-700">{loan.amount}</td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-700">{loan.type}</td>
                <td className="px-6 py-4 whitespace-nowrap">
                  <span className={`px-2 inline-flex text-xs leading-5 font-semibold rounded-full ${getStatusColor(loan.status)}`}>
                    {loan.status}
                  </span>
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-700">{loan.dueDate}</td>
                <td className="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                  <button className="text-blue-600 hover:text-blue-900 mr-4">Edit</button>
                  <button className="text-red-600 hover:text-red-900">Delete</button>
                </td>
              </tr>
            ))}
          </tbody>
        </table>
      </div>
    </div>
  );
};

// Customers Component
const Customers = () => {
  const customers = [
    { id: 'CUST001', name: 'John Doe', email: 'john.doe@example.com', phone: '123-456-7890', status: 'Active' },
    { id: 'CUST002', name: 'Jane Smith', email: 'jane.smith@example.com', phone: '098-765-4321', status: 'Active' },
    { id: 'CUST003', name: 'Robert Brown', email: 'robert.b@example.com', phone: '555-123-4567', status: 'Inactive' },
    { id: 'CUST004', name: 'Emily White', email: 'emily.w@example.com', phone: '111-222-3333', status: 'Active' },
  ];

  const getStatusColor = (status) => {
    return status === 'Active' ? 'bg-green-100 text-green-800' : 'bg-red-100 text-red-800';
  };

  return (
    <div className="space-y-6">
      <div className="flex justify-between items-center mb-4">
        <h2 className="text-xl font-semibold text-gray-800">Customer Management</h2>
        <button className="bg-blue-500 text-white py-2 px-4 rounded-lg hover:bg-blue-600 transition duration-200 ease-in-out">
          + Add New Customer
        </button>
      </div>
      <div className="bg-white rounded-xl shadow-md overflow-hidden">
        <table className="min-w-full divide-y divide-gray-200">
          <thead className="bg-gray-50">
            <tr>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Customer ID</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Name</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Email</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Phone</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status</th>
              <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Actions</th>
            </tr>
          </thead>
          <tbody className="bg-white divide-y divide-gray-200">
            {customers.map((customer) => (
              <tr key={customer.id}>
                <td className="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{customer.id}</td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-700">{customer.name}</td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-700">{customer.email}</td>
                <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-700">{customer.phone}</td>
                <td className="px-6 py-4 whitespace-nowrap">
                  <span className={`px-2 inline-flex text-xs leading-5 font-semibold rounded-full ${getStatusColor(customer.status)}`}>
                    {customer.status}
                  </span>
                </td>
                <td className="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                  <button className="text-blue-600 hover:text-blue-900 mr-4">View</button>
                  <button className="text-red-600 hover:text-red-900">Delete</button>
                </td>
              </tr>
            ))}
          </tbody>
        </table>
      </div>
    </div>
  );
};

// Reports Component
const Reports = () => {
  return (
    <div className="bg-white rounded-xl shadow-md p-6 h-96 flex items-center justify-center text-gray-400">
      <p>Placeholder for various financial reports (e.g., Loan Performance, Delinquency, Revenue)</p>
    </div>
  );
};

// Settings Component
const Settings = () => {
  return (
    <div className="bg-white rounded-xl shadow-md p-6 h-96 flex items-center justify-center text-gray-400">
      <p>Placeholder for application settings (e.g., User Management, Integrations, Notifications)</p>
    </div>
  );
};

export default App;
