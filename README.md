# react-spa

# NAME: Hariprasath R
# REG NO : 212223040059

# ProtectedRouter.jsx
```
import { Navigate } from "react-router-dom";

const ProtectedRoute = ({ children }) => {
  const isAuthenticated = localStorage.getItem("isAuthenticated") === "true";

  if (!isAuthenticated) {
    return <Navigate to="/login" replace />;
  }

  return children;
};

export default ProtectedRoute;
```

# App.jsx
```
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Home from "./pages/Home";
import Login from "./pages/Login";
import Dashboard from "./pages/Dashboard";
import Profile from "./pages/Profile";
import Settings from "./pages/Settings";
import Notifications from "./pages/Notifications";
import ProtectedRoute from "./components/ProtectedRouter";

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/login" element={<Login />} />

        {/* Protected Dashboard Routes */}
        <Route
          path="/dashboard"
          element={
            <ProtectedRoute>
              <Dashboard />
            </ProtectedRoute>
          }
        >
          <Route path="profile" element={<Profile />} />
          <Route path="settings" element={<Settings />} />
          <Route path="notifications" element={<Notifications />} />
        </Route>

        {/* Catch-all route */}
        <Route path="*" element={<h1>404 - Page Not Found</h1>} />
      </Routes>
    </Router>
  );
}

export default App;
```

# Dashboard.jsx
```
import { Outlet, Link } from "react-router-dom";

const Dashboard = () => {
  return (
    <div>
      <h1>Dashboard</h1>
      <nav>
        <Link to="profile">Profile</Link> |{" "}
        <Link to="settings">Settings</Link> |{" "}
        <Link to="notifications">Notifications</Link>
      </nav>
      <hr />
      <Outlet /> {/* Nested routes will render here */}
    </div>
  );
};

export default Dashboard;
```
# Home.jsx
```
const Home = () => {
  return <h1>Home Page</h1>;
};

export default Home;
```

# Login.jsx
```
import { useNavigate } from "react-router-dom";

const Login = () => {
  const navigate = useNavigate();

  const handleLogin = () => {
    localStorage.setItem("isAuthenticated", "true");
    navigate("/dashboard");
  };

  return (
    <div>
      <h1>Login Page</h1>
      <button onClick={handleLogin}>Login</button>
    </div>
  );
};

export default Login;
```
# Notifications.jsx
```
const Notifications = () => <h2>Notifications Page</h2>;
export default Notifications;
```

# Profile.jsx
```
const Profile = () => <h2>Profile Page</h2>;
export default Profile;
```

# Settings.jsx
```
const Settings = () => <h2>Settings Page</h2>;
export default Settings;
```

## OUTPUT:
<img width="1253" height="661" alt="image" src="https://github.com/user-attachments/assets/30cdcd77-2bec-4a65-9992-a6a8947a4959" />
<img width="1359" height="867" alt="image" src="https://github.com/user-attachments/assets/643bfda3-8e4e-436d-9256-794067966471" />
<img width="1350" height="775" alt="image" src="https://github.com/user-attachments/assets/4d0bdf09-d6ac-4b3e-9d4b-56452511d156" />
<img width="1151" height="765" alt="image" src="https://github.com/user-attachments/assets/6ccb18ec-4217-4789-b7a1-24acba3db948" />
<img width="1289" height="709" alt="image" src="https://github.com/user-attachments/assets/2bd8b9e2-3945-4964-97b3-1c247fb082ac" />





