# Hall Booking Application

## Overview
The Hall Booking Application is a Node.js and Express-based API for managing room bookings. The API allows for creating rooms, booking rooms, and retrieving booking details for rooms and customers.

## Features
1. **Create a Room**: Define a room with its number of seats, amenities, and price per hour.
2. **Book a Room**: Book a room by providing customer name, date, start time, end time, and room ID.
3. **List All Rooms with Booked Data**: Retrieve a list of all rooms along with their booking details.
4. **List All Customers with Booked Data**: Retrieve a list of all customers along with their booking details.
5. **Customer Booking History**: Retrieve detailed booking history of a specific customer, including booking status.

## Setup Instructions

### Prerequisites
- Node.js
- npm 

### Dependencies
- npm init -y
- npm install express body-parser

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/Bharath-Parthipan/Hall-Booking-API.git
   cd Hall-Booking-API

### Running the Server
  To start the Express server, run:
   ```sh
    npm start
   ```
The server will start on "http://localhost:3000."

## Render URL
   ```sh
   https://hall-booking-api-1-8tp3.onrender.com
   ```

## API Endpoints

1. Create a Room
   - URL: POST /api/rooms
   - Body: { "roomName": "Room A", "seats": 20, "amenities": ["Projector", "Whiteboard"], "pricePerHour": 100 }
   - Response:
   ```json
   {
     "message": "Room created successfully",
     "room": {
       "id": 1,
       "roomName": "Room A",
       "seats": 20,
       "amenities": ["Projector", "Whiteboard"],
       "pricePerHour": 500
     }
   }
   ```
2. Book a Room
   - URL: POST /api/bookings
   - Body: { "customerName": "John Doe", "date": "2024-07-25", "startTime": "10:00", "endTime": "12:00", "roomId": 1 }
   - Response:
   ```json
   {
       "message": "Room booked successfully",
       "booking": {
           "id": 1,
           "customerName": "Bharath",
           "date": "2024-07-24",
           "startTime": "10:00",
           "endTime": "12:00",
           "roomId": 2,
           "bookingDate": "2024-07-23T07:34:36.462Z",
           "status": "Booked"
       }
   }
   ```
3. List all Rooms with Booked Data
   - URL: GET /api/rooms
   - Response:
   ```json
   [
       {
           "id": 1,
           "roomName": "Room A",
           "seats": 20,
           "amenities": [
               "Projector",
               "Whiteboard"
           ],
           "pricePerHour": 500,
           "bookings": []
       },
       {
           "id": 2,
           "roomName": "Room B",
           "seats": 50,
           "amenities": [
               "Projector",
               "Whiteboard"
           ],
           "pricePerHour": 1000,
           "bookings": [
               {
                   "id": 1,
                   "customerName": "Bharath",
                   "date": "2024-07-24",
                   "startTime": "10:00",
                   "endTime": "12:00",
                   "roomId": 2,
                   "bookingDate": "2024-07-23T07:34:36.462Z",
                   "status": "Booked"
               }
           ]
       },
       {
           "id": 3,
           "roomName": "Room C",
           "seats": 100,
           "amenities": [
               "Projector",
               "Whiteboard"
           ],
           "pricePerHour": 1700,
           "bookings": []
       },
       {
           "id": 4,
           "roomName": "Room D",
           "seats": 700,
           "amenities": [
               "Projector",
               "Whiteboard"
           ],
           "pricePerHour": 5000,
           "bookings": []
       }
   ]
   ```
4. List all Customers with Booked Data
   - URL: GET /api/customers
   - Response:
   ```json
   [
       {
           "customerName": "Bharath",
           "roomName": "Room B",
           "date": "2024-07-24",
           "startTime": "10:00",
           "endTime": "12:00"
       }
   ]
   ```
5. List how many times a customer has booked the room
   - URL: GET /api/customers/:customerName
   - Response:
   ```json
   {
       "customerName": "Bharath",
       "bookings": [
           {
               "roomName": "Room B",
               "date": "2024-07-24",
               "startTime": "10:00",
               "endTime": "12:00",
               "bookingId": 1,
               "bookingDate": "2024-07-23T07:34:36.462Z",
               "status": "Booked"
           }
       ]
   }
   ```
