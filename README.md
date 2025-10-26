# 🚗 HelpOnRoute - Driver Support Platform

<div align="center">

**Helping each other on the road to ensure on-time deliveries.**

Connect with nearby Walmart delivery partners for instant roadside assistance.

[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Socket.io](https://img.shields.io/badge/Socket.io-black?style=for-the-badge&logo=socket.io&badgeColor=010101)](https://socket.io/)

</div>

---

## 📖 Overview

**HelpOnRoute** is a real-time roadside assistance platform designed for Walmart delivery drivers. The platform enables drivers to request help when they encounter issues on the road and allows other nearby drivers to offer assistance. Built with modern web technologies, it features real-time location tracking, instant notifications, and a reward system.

### Key Features

- 🔐 **User Authentication** - Secure signup and login for drivers
- 🗺️ **Real-time Mapping** - Interactive map with Leaflet showing driver locations
- 📍 **Location Tracking** - Live location updates for active drivers
- 🆘 **Help Request System** - Create, accept, and resolve help requests
- 💬 **Real-time Communication** - Instant notifications via Socket.io
- 🏆 **Reward System** - Earn coins for helping fellow drivers
- 📸 **Image Upload** - Upload vehicle issue photos (via Cloudinary)
- 🚗 **Driver Profiles** - View profile, vehicle details, and help history
- 🔔 **Status Management** - Track driver availability (Available/Busy/Helping)

---

## 🛠️ Tech Stack

### Frontend
- **React 19** - Modern UI framework
- **TypeScript** - Type-safe development
- **Vite** - Fast build tool
- **React Router** - Client-side routing
- **Leaflet** - Interactive maps
- **Tailwind CSS** - Utility-first styling
- **Framer Motion** - Smooth animations
- **Axios** - HTTP client
- **Socket.io-client** - Real-time communication

### Backend
- **Node.js** - Runtime environment
- **Express 5** - Web framework
- **TypeScript** - Type-safe development
- **Prisma** - ORM for PostgreSQL
- **PostgreSQL** - Relational database
- **Socket.io** - Real-time bidirectional communication
- **Cloudinary** - Image storage
- **Multer** - File upload handling
- **JWT** - Authentication

### Additional Tools
- **OpenRouteService** - Route calculation API
- **@turf/turf** - Geospatial calculations

---

## 📁 Project Structure

```
HelpOnRoute-main/
├── client/                 # React frontend application
│   ├── src/
│   │   ├── Components/     # Reusable components
│   │   ├── pages/          # Page components
│   │   ├── socket/         # Socket.io client setup
│   │   ├── model/          # Modal components
│   │   └── App.tsx         # Main app component
│   └── package.json
│
└── server/                 # Node.js backend application
    ├── src/
    │   ├── controllers/     # Request handlers
    │   ├── routes/         # API routes
    │   ├── socketHandler/ # Socket.io handlers
    │   ├── config/         # Configuration files
    │   └── index.ts        # Server entry point
    ├── prisma/
    │   └── schema.prisma   # Database schema
    └── package.json
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js (v18 or higher)
- PostgreSQL database
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/JK-77/HelpOnRoute.git
   cd HelpOnRoute
   ```

2. **Install server dependencies**
   ```bash
   cd server
   npm install
   ```

3. **Install client dependencies**
   ```bash
   cd ../client
   npm install
   ```

4. **Set up environment variables**

   Create a `.env` file in the `server` directory:
   ```env
   DATABASE_URL="postgresql://user:password@localhost:5432/helponroute"
   JWT_SECRET="your-secret-key"
   CLOUDINARY_CLOUD_NAME="your-cloud-name"
   CLOUDINARY_API_KEY="your-api-key"
   CLOUDINARY_API_SECRET="your-api-secret"
   ```

5. **Set up the database**
   ```bash
   cd server
   npx prisma migrate dev
   npx prisma generate
   ```

6. **Run the development servers**

   Terminal 1 (Server):
   ```bash
   cd server
   npm run dev
   ```
   Server runs on `http://localhost:3000`

   Terminal 2 (Client):
   ```bash
   cd client
   npm run dev
   ```
   Client runs on `http://localhost:5173`

---

## 📱 Usage

### For Drivers Requesting Help
1. Sign up or log in to your account
2. Navigate to Dashboard
3. Fill in your issue details and upload a photo (optional)
4. Your location is automatically tracked
5. Wait for a nearby driver to accept your request
6. Accept offers from other drivers
7. Mark request as resolved when help is complete

### For Drivers Offering Help
1. Log in to your account
2. Navigate to Help Dashboard
3. View all pending help requests on the map
4. Click on any request to see details
5. Accept a request to start helping
6. Navigate to the requester's location
7. Help is marked as resolved when complete
8. Earn coins for successful help!

---

## 🗄️ Database Schema

### Driver Model
- Personal information (name, email, phone)
- Location (latitude, longitude)
- Status (AVAILABLE, BUSY, HELPING)
- Profile data (image, vehicle number)
- Reward system (coins, help count)

### HelpRequest Model
- Requester and helper information
- Issue description and image
- Location coordinates
- Status (PENDING, ACCEPTED, RESOLVED)
- Timestamps

---

## 🔌 API Endpoints

### Authentication
- `POST /api/auth/signup` - Register new driver
- `POST /api/auth/signin` - Login driver

### Drivers
- `GET /api/drivers` - Get all drivers
- `PUT /api/driver/:id` - Update driver location/status
- `GET /api/driver/:id` - Get driver details

### Help Requests
- `POST /api/request/create` - Create help request
- `GET /api/request/pending` - Get all pending requests
- `PUT /api/request/:id/accept` - Accept help request
- `PUT /api/request/:id/resolve` - Resolve help request

### Socket Events
- `send-help-request` - Broadcast new help request
- `receive-help-request` - Receive help requests
- `accept-help` - Accept help request
- `help-accepted` - Notification when help is accepted
- `help-resolved` - Mark help as resolved

---

## 🎨 Features in Detail

### Real-time Location Tracking
- Drivers' locations are continuously updated and broadcasted
- Visual representation on interactive map
- Route calculation between requester and helper

### Reward System
- Drivers earn coins for successful help
- Track help count in profile
- Gamification encourages community support

### Image Upload
- Upload vehicle issue photos
- Cloudinary integration for reliable storage
- Visual aid for helpers to understand the issue

---

## 🔐 Security Features

- JWT-based authentication
- Password hashing
- CORS configuration
- Input validation
- Secure file uploads

---

## 🚧 Future Enhancements

- [ ] In-app messaging between drivers
- [ ] Push notifications
- [ ] Rating and review system
- [ ] Emergency contact integration
- [ ] Vehicle diagnostics integration
- [ ] Payment gateway for rewards
- [ ] Advanced analytics dashboard
- [ ] Mobile app (React Native)

---

## 📝 License

This project is licensed under the MIT License.

---

## 👥 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

## 📧 Contact

For questions or support, please open an issue on GitHub.

---

<div align="center">

**Made with ❤️ for Walmart delivery drivers**

Happy Driving! 🚗💨

</div>

