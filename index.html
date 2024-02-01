// video_sharing_app.js

// Frontend HTML
const frontendHTML = `
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Video Sharing App</title>
</head>
<body>
    <div id="root"></div>
    <script src="/bundle.js"></script> <!-- React bundle -->
</body>
</html>
`;

// Backend (Node.js med Express.js)
const express = require('express');
const mongoose = require('mongoose');
const multer = require('multer');
const path = require('path');
const { createProxyMiddleware } = require('http-proxy-middleware');

// Opret Express-app
const app = express();

// Middleware
app.use(express.json());

// Databaseforbindelse
mongoose.connect('mongodb://localhost:27017/video-sharing', { useNewUrlParser: true, useUnifiedTopology: true });
const db = mongoose.connection;
db.on('error', console.error.bind(console, 'MongoDB connection error:'));

// Multer konfiguration til håndtering af filuploads
const storage = multer.diskStorage({
    destination: function (req, file, cb) {
        cb(null, 'uploads/');
    },
    filename: function (req, file, cb) {
        cb(null, Date.now() + '-' + file.originalname);
    }
});
const upload = multer({ storage: storage });

// Brugeroprettelse endpoint
app.post('/api/users', async (req, res) => {
    // Logik til brugeroprettelse
});

// Video-upload endpoint
app.post('/api/videos', upload.single('video'), async (req, res) => {
    // Logik til video-upload
});

// Proxy til API-anmodninger
app.use('/api', createProxyMiddleware({ target: 'http://localhost:5000', changeOrigin: true }));

// Server statiske filer (frontend build)
app.use(express.static(path.join(__dirname, 'client/build')));

// Returner frontend HTML
app.get('/', (req, res) => {
    res.send(frontendHTML);
});

// Start serveren
const PORT = process.env.PORT || 5000;
app.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`);
});
