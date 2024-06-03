# React Back-end Integration

## Coding Task Name
React and Back-end Integration

## Description
This project demonstrates how to integrate a React front-end with an Express back-end. It covers the essential aspects of connecting a front-end application to a back-end server, fetching data, and displaying it. Learning this integration is crucial for building full-stack applications where the front-end needs to communicate with the back-end for data retrieval and other operations.

## Table of Contents
1. [Installation](#installation)
2. [Usage](#usage)
3. [Credits](#credits)

## Installation
To run this project locally, follow these steps:

1. **Clone the repository:**
    ```bash
    git clone [https://github.com/puja-rathi/codingTasks.git]
    cd codingTasks
    ```

2. **Set up the backend:**
    ```bash
    cd backend
    npm install
    ```

3. **Set up the front-end:**
    ```bash
    cd ../frontend
    npm install
    ```

## Usage
After installing the dependencies, you can run the project with the following steps:

1. **Start the back-end server:**
    ```bash
    cd backend
    npm start
    ```

    The back-end server will start on `http://localhost:5000`.

2. **Start the front-end application:**
    ```bash
    cd ../frontend
    npm start
    ```

    The front-end application will start on `http://localhost:3000`.

3. **Access the Application:**
    Open your web browser and navigate to `http://localhost:3000`. You should see the custom message fetched from the back-end displayed on the front-end.

![Application Screenshot]<img width="1010" alt="react_backend_integration" src="https://github.com/puja-rathi/codingTasks/assets/37535019/c1247b47-3b20-44e2-a952-a73c3214293a">


### Code Explanation:
- **Backend (`backend/server.js`):**
    ```javascript
    const express = require('express');
    const cors = require('cors');
    const app = express();
    const port = 5000;

    app.use(cors());

    app.get('/api/message', (req, res) => {
        res.json({ message: 'Hello from the back-end!' });
    });

    app.listen(port, () => {
        console.log(`Server running on http://localhost:${port}`);
    });
    ```

- **Front-end (`frontend/src/App.js`):**
    ```javascript
    import React, { useState, useEffect } from 'react';
    import axios from 'axios';

    function App() {
        const [customMessage, setCustomMessage] = useState('');

        useEffect(() => {
            axios.get('http://localhost:5000/api/message')
                .then(response => {
                    setCustomMessage(response.data.message);
                })
                .catch(error => {
                    console.error('There was an error fetching the message!', error);
                });
        }, []);

        return (
            <div className="App">
                <h1>{customMessage}</h1>
            </div>
        );
    }

    export default App;
    ```

## Credits
This project was developed by Puja Rathi(https://github.com/puja-rathi). The code is open-source and available on GitHub.
