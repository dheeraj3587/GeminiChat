# SOEN App

## Overview

This document provides an overview of the routes used in the SOEN app and the steps to run the app. The UI is designed to look modern and user-friendly.

## Routes

- `/` - Home page
- `/login` - User login page
- `/register` - User registration page
- `/dashboard` - User dashboard
- `/profile` - User profile page
- `/settings` - User settings page

- `/logout` - User logout

## Steps to Run the App

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/soen-main.git
   cd soen-main
   ```

2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Set Up Environment Variables**
   Create a `.env` file in the root directory and add the necessary environment variables.

   ```env
   PORT=3000
   DATABASE_URL=your_database_url
   JWT_SECRET=your_jwt_secret
   ```

4. **Run Database Migrations**

   ```bash
   npx sequelize-cli db:migrate
   ```

5. **Start the Application**

   ```bash
   npm start
   ```

6. **Access the App**
   Open your browser and navigate to `http://localhost:3000`.

## Modern UI Design

- **Responsive Layout**: The app is designed to be fully responsive, ensuring a seamless experience on both desktop and mobile devices.
- **Material Design**: Utilizes Material-UI components for a clean and modern look.
- **Dark Mode**: Supports dark mode for better accessibility and user preference.
- **Animations**: Smooth animations and transitions for a polished user experience.

## Conclusion

Follow the steps above to set up and run the SOEN app. The app's modern UI ensures a great user experience across all devices.
