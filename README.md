<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Video Calling</title>
    <script>
const startButton = document.getElementById('startButton');
const stopButton = document.getElementById('stopButton');
const localVideo = document.getElementById('localVideo');
const remoteVideo = document.getElementById('remoteVideo');
let localStream;
let remoteStream;
let peerConnection;

startButton.addEventListener('click', startCall);
stopButton.addEventListener('click', stopCall);

async function startCall() {
    try {
        localStream = await navigator.mediaDevices.getUserMedia({ video: true, audio: true });
        localVideo.srcObject = localStream;

        // Implement signaling to set up the connection with the remote peer.
        // This typically involves a signaling server (e.g., WebSocket).

        // Set up peer connection, add tracks, and create an offer.

    } catch (error) {
        console.error('Error accessing media devices:', error);
    }
}

function stopCall() {
    // Close the peer connection and release the media streams.
}
//
</script>
</head>

<body>
    <h1>Allim Quran Academy </h1>
    <video id="localVideo" autoplay muted></video>
    <video id="remoteVideo" autoplay></video>
    <button id="startButton">Start Call</button>
    <button id="stopButton">Stop Call</button>

    
</body>

</html>

<!DOCTYPE html>
<html lang="en">
<head>
   
    <title>My Educational Website</title>
    <style>
head{
    margin: 0;
    padding: 0;}
    </style>
</head>
<body>
    <header>
        <style>
        header {
            background-color: #007BFF;
            color: #ffffff;
            text-align: center;
            padding: 20px 0;
        }
        </style>

        <h1>Welcome to Allim Quran Academy</h1>
        <style>
         header h1 {
          font-size: 36px;
                    }
        </style>
        <nav>
            <style>
 nav ul{ list-style-type: none;}
 nav li {
    display: inline;
    margin-right: 20px;
}
nav a {
    text-decoration: lightgoldenrodyellow;
    color: #fff;
    font-weight: bold;
    font-size: 18px;
}
/* Style the sections */
section {
    padding: 40px;
    text-align: center;
}

/* Style section h2 elements */
section h2 {
    font-size: 24px;
    margin-bottom: 20px;
}

/* Style section p elements */
section p {
    font-size: 18px;
}

/* Style the footer */
footer {
    background-color: #007BFF;
    color: #fff;
    text-align: center;
    padding: 10px 0;
    position: absolute;
    bottom: 0;
    width: 100%;
}

/* Style links on hover */
a:hover {
    color: #0056b3;
}
         </style>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#courses">Courses</a></li>
                <li><a href="#about">About Us</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>

    </header>

    <section id="home">
        <h2>Learn, Explore, Grow</h2>
        <p>Discover a world of knowledge with our courses.</p>
    </section>

    <section id="courses">
             <h2>Our Courses</h2>
        <ul>
            <li>Arabic for Beginners</li>
            <li>Arabic for Intermediate Users</li>
            <li>Arabic for Advanced Users</li>
            <li>Quran Recitation</li>
            <li>Quran Memorization</li>
            <li>English for Beginners</li>
            <li>English for Advanced users</li>
        </ul>
    </section>

    <section id="about">
        <h2>About Us</h2>
        <p>Allim Quran Academy  has been launched to offer quality classes for </p>
    </section>

    <section id="contact">
        <h2>Contact Us</h2>
        <p>+201019115088</p>
        <p>Allim Quran Academy@gmail.com</p>
    </section>

    <footer>
        <p>&copy; 2023 My Educational Website</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>

<html lang="en">
<head>
  
    <title>Calendar Booking</title>
    <style>
        /* Add your CSS styles here */
    </style>
</head>
<body>
    <h1>Book a free 20-minute Demo Lesson</h1>
    <form id="booking-form">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required><br><br>
        
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>
        
        <label for="date">Date:</label>
        <input type="date" id="date" name="date" required><br><br>
        
        <label for="time">Time:</label>
        <input type="time" id="time" name="time" required><br><br>
        
        <button type="submit">Book Appointment</button>
    </form>

    <div id="confirmation"></div>

    <script>
        const bookingForm = document.getElementById('booking-form');
        const confirmationDiv = document.getElementById('confirmation');

        bookingForm.addEventListener('submit', function (e) {
            e.preventDefault();
            const formData = new FormData(bookingForm);

            // You can handle the form data here (e.g., send it to a server, store it in a database, etc.).

            // For this simplified example, display a confirmation message.
            confirmationDiv.innerHTML = 'Appointment booked successfully!';
            bookingForm.reset();
        });
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    
    <title>Slide Gallery</title>
    <style>
        /* Add your CSS styles here */
        .slideshow-container {
            max-width: 400px;
            position: relative;
            margin: auto;
        }

        .mySlides {
            display: inside;
        }

        .slideshow-container img {
            width: 50%;
            height: auto;
        }

        /* Add CSS styles for navigation buttons if needed */
    </style>
</head>

<body>
    <div class="slideshow-container">
        <div class="mySlides">
            <img src="image1.jpg" alt="Image 1">
        </div>

        <div class="mySlides">
            <img src="image2.jpg" alt="Image 2">
        </div>

        <div class="mySlides">
            <img src="C:\Users\ammar\Desktop\calendar-booking-app\My Photo.jpg" alt="Image 3">
        </div>

        <!-- Add more slides as needed -->

        <button class="prev" onclick="plusSlides(-1)">Previous</button>
        <button class="next" onclick="plusSlides(1)">Next</button>
    </div>

    <script>
        let slideIndex = 0;
        showSlides(slideIndex);

        function plusSlides(n) {
            showSlides(slideIndex += n);
        }

        function showSlides(n) {
            let i;
            const slides = document.querySelectorAll(".mySlides");
            if (n >= slides.length) { slideIndex = 0; }
            if (n < 0) { slideIndex = slides.length - 1; }
            for (i = 0; i < slides.length; i++) {
                slides[i].style.display = "none";
            }
            slides[slideIndex].style.display = "block";
        }
    </script>
</body>

</html>



