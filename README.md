<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multi-Purpose Educational Website</title>

    <!-- Slick Carousel Styles -->
    <link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick.css"/>
    <link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick-theme.css"/>

    <style>
        /* Video Calling Styles */
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
            margin: 0; /* Reset default margin */
        }

        h1 {
            font-size: 48px; /* Set a larger font size */
            color: #333;
            animation: colorChange 5s infinite alternate; /* Add color-changing animation */
            cursor: pointer;
            margin-top: 50px; /* Add some top margin for spacing */
        }

        @keyframes colorChange {
            0% {
                color: #ff0000; /* Start with red */
            }
            25% {
                color: #00ff00; /* Change to green */
            }
            50% {
                color: #0000ff; /* Change to blue */
            }
            75% {
                color: #ff00ff; /* Change to magenta */
            }
            100% {
                color: #ff0000; /* Back to red */
            }
        }

        video {
            width: 100%;
            max-width: 400px;
            margin: 10px;
        }

        button {
            padding: 10px;
            margin: 5px;
            font-size: 16px;
            cursor: pointer;
        }

        /* Educational Website Styles */
        header {
            background-color: #007BFF;
            color: #ffffff;
            text-align: center;
            padding: 20px 0;
        }

        header h1 {
            font-size: 36px;
        }

        nav ul {
            list-style-type: none;
        }

        nav li {
            display: inline;
            margin-right: 20px;
        }

        nav a {
            text-decoration: none;
            color: #fff;
            font-weight: bold;
            font-size: 18px;
        }

        section {
            padding: 40px;
            text-align: center;
        }

        section h2 {
            font-size: 24px;
            margin-bottom: 20px;
        }

        section p {
            font-size: 18px;
        }

        footer {
            background-color: #007BFF;
            color: #fff;
            text-align: center;
            padding: 10px 0;
            position: absolute;
            bottom: 0;
            width: 100%;
        }

        a:hover {
            color: #0056b3;
        }

        /* Carousel Styles */
        #course-carousel {
            max-width: 600px;
            margin: auto;
        }

        .course-slide img {
            width: 100%;
            height: auto;
        }

        .slick-prev, .slick-next {
            font-size: 24px;
            color: #007BFF;
        }

        /* Book Now Button Styles */
        #book-now-button {
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <!-- Video Calling Section -->
    <section id="video-calling">
        <h1 onclick="toggleColor()">Allim Quran Academy</h1>
        <video id="localVideo" autoplay muted></video>
        <video id="remoteVideo" autoplay></video>
        <button id="startButton" onclick="startCall()">Start Call</button>
        <button id="stopButton" onclick="stopCall()">Stop Call</button>
        <style>
            /* Add any additional styles specific to the video calling section here */
        </style>
        <script>
            const localVideo = document.getElementById('localVideo');
            const remoteVideo = document.getElementById('remoteVideo');
            let localStream;
            let remoteStream;
            let peerConnection;

            async function startCall() {
                try {
                    localStream = await navigator.mediaDevices.getUserMedia({ video: true, audio: true });
                    localVideo.srcObject = localStream;

                    // Implement signaling to set up the connection with the remote peer.
                    // This typically involves a signaling server (e.g., WebSocket).

                    // WebSocket setup for signaling
                    const socket = new WebSocket('wss://your-signaling-server.com');

                    // Handle WebSocket events
                    socket.addEventListener('open', (event) => {
                        console.log('WebSocket connected:', event);
                    });

                    socket.addEventListener('message', (event) => {
                        console.log('WebSocket message received:', event.data);
                        // Handle incoming signaling messages (offer, answer, ice candidate, etc.)
                    });

                    socket.addEventListener('close', (event) => {
                        console.log('WebSocket closed:', event);
                    });

                    socket.addEventListener('error', (event) => {
                        console.error('WebSocket error:', event);
                    });

                    // Create a peer connection configuration
                    const configuration = { iceServers: [{ urls: 'stun:stun.l.google.com:19302' }] };

                    // Create a peer connection
                    peerConnection = new RTCPeerConnection(configuration);

                    // Add the local stream to the peer connection
                    localStream.getTracks().forEach(track => peerConnection.addTrack(track, localStream));

                    // Set up event handlers for the peer connection

                    // Create an offer to initiate the connection
                    const offer = await peerConnection.createOffer();
                    await peerConnection.setLocalDescription(offer);

                    // Send the offer to the remote peer (via signaling)

                } catch (error) {
                    console.error('Error accessing media devices:', error);
                }
            }

            function stopCall() {
                // Close the peer connection and release the media streams.
                if (peerConnection) {
                    peerConnection.close();
                }
                localStream.getTracks().forEach(track => track.stop());
                localVideo.srcObject = null;
                remoteVideo.srcObject = null;
            }

            function toggleColor() {
                const title = document.querySelector('h1');
                title.style.color = getRandomColor();
            }

            function getRandomColor() {
                const letters = '0123456789ABCDEF';
                let color = '#';
                for (let i = 0; i < 6; i++) {
                    color += letters[Math.floor(Math.random() * 16)];
                }
                return color;
            }
        </script>
    </section>

    <!-- Educational Website Section -->
    <section id="educational-website">
        <header>
            <h1>Welcome to Allim Quran Academy</h1>
            <nav>
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
            <p>Take knowledge to the next level with us</p>
        </section>

        <section id="courses">
            <h2>Our Courses</h2>
            <!-- Slick Carousel for Courses -->
            <div id="course-carousel">
                <div class="course-slide">
                    <img src="file://C:/Users/ammar/Desktop/Ammar Directory/Arabic for Arabs.PNG" alt="Course 1">
                </div>
                <div class="course-slide">
                    <img src="file://C:/Users/ammar/Desktop/Ammar Directory/Quran Memorization.JPG" alt="Course 2">
                </div>
                <div class="course-slide">
                    <img src="file://C:/Users/ammar/Desktop/Ammar Directory/Quran Recitation.JPG" alt="Course 2">
                </div>
                <div class="course-slide">
                    <img src="file://C:/Users/ammar/Desktop/Ammar Directory/English for Beginners.JPG" alt="Course 2">
                </div>
                <div class="course-slide">
                    <img src="file://C:/Users/ammar/Desktop/Ammar Directory/English for Advanced users.JPG" alt="Course 2">
                </div>
                <div class="course-slide">
                    <img src="file://C:/Users/ammar/Desktop/Ammar Directory/Arabic for Intermediate Users.JPG" alt="Course 2">
                </div>
                <!-- Add more courses as needed -->
            </div>
        </section>

        <section id="about">
            <h2>About Us</h2>
            <p>Allim Quran Academy has been launched to offer quality classes for...</p>
        </section>

        <section id="contact">
            <h2>Contact Us</h2>
            <p>+201019115088</p>
            <p>Allim Quran Academy@gmail.com</p>
        </section>

        <footer>
            <p>&copy; 2023 My Educational Website</p>
        </footer>
    </section>

    <!-- Calendar Booking Section -->
    <section id="calendar-booking">
        <h1>Click below to book a free 30-minute Demo Lesson</h1>
        <!-- Book Now Button -->
        <a href="https://calendly.com/allimquranacademy2024" target="_blank" id="book-now-button">
            <button>Book Now</button>
        </a>
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
    </section>

    <!-- Slide Gallery Section -->
    <section id="slide-gallery">
        <div class="slideshow-container">
            <div class="mySlides">
                <img src="C:\Users\ammar\Desktop\Ammar Directory" alt="Image 1">
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
    </section>

    <!-- Slick Carousel Scripts -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/slick-carousel@1.8.1/slick/slick.min.js"></script>

    <script>
        // Initialize Slick Carousel with Autoplay
        $(document).ready(function(){
            $('#course-carousel').slick({
                dots: true,
                infinite: true,
                speed: 300,
                slidesToShow: 1,
                adaptiveHeight: true,
                autoplay: true,  // Enable Autoplay
                autoplaySpeed: 2000,  // Set Autoplay Speed in milliseconds (adjust as needed)
                prevArrow: '<button class="slick-prev">Previous</button>',
                nextArrow: '<button class="slick-next">Next</button>'
            });
        });
    </script>
</body>

</html>
