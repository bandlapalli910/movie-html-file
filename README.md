<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tollywood Ticket Booking</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #e84118;
            --secondary: #192a56;
            --light: #f5f6fa;
            --dark: #2f3640;
            --success: #44bd32;
        }

        body {
            background-color: #f5f6fa;
            color: #2f3640;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header Styles */
        header {
            background: linear-gradient(to right, var(--secondary), var(--dark));
            color: white;
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo i {
            font-size: 28px;
            color: var(--primary);
        }

        .logo h1 {
            font-size: 24px;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 20px;
        }

        nav a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }

        nav a:hover {
            color: var(--primary);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url('https://images.unsplash.com/photo-1595769816263-9b910be24d5f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80');
            background-size: cover;
            background-position: center;
            color: white;
            text-align: center;
            padding: 80px 20px;
            margin-bottom: 40px;
        }

        .hero h2 {
            font-size: 42px;
            margin-bottom: 20px;
        }

        .hero p {
            font-size: 18px;
            max-width: 700px;
            margin: 0 auto 30px;
        }

        .btn {
            display: inline-block;
            padding: 12px 30px;
            background-color: var(--primary);
            color: white;
            text-decoration: none;
            border-radius: 5px;
            font-weight: 600;
            transition: background-color 0.3s;
        }

        .btn:hover {
            background-color: #c23616;
        }

        /* Movies Section */
        .section-title {
            text-align: center;
            margin-bottom: 40px;
            color: var(--secondary);
            font-size: 32px;
            position: relative;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background-color: var(--primary);
            margin: 10px auto;
        }

        .movies-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 30px;
            margin-bottom: 50px;
        }

        .movie-card {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
        }

        .movie-card:hover {
            transform: translateY(-10px);
        }

        .movie-poster {
            height: 380px;
            overflow: hidden;
        }

        .movie-poster img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }

        .movie-card:hover .movie-poster img {
            transform: scale(1.1);
        }

        .movie-info {
            padding: 20px;
        }

        .movie-title {
            font-size: 20px;
            margin-bottom: 10px;
            color: var(--secondary);
        }

        .movie-details {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
            color: #7f8fa6;
        }

        .movie-actions {
            display: flex;
            justify-content: space-between;
        }

        /* Booking Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background-color: white;
            border-radius: 10px;
            width: 90%;
            max-width: 600px;
            padding: 30px;
            position: relative;
            max-height: 90vh;
            overflow-y: auto;
        }

        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 24px;
            cursor: pointer;
            color: #7f8fa6;
        }

        .booking-form h3 {
            margin-bottom: 20px;
            color: var(--secondary);
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }

        .form-group select, .form-group input {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }

        .showtimes {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
        }

        .time-option {
            padding: 10px 15px;
            background-color: #f1f2f6;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .time-option:hover {
            background-color: #dfe4ea;
        }

        .time-option.selected {
            background-color: var(--secondary);
            color: white;
        }

        /* Footer */
        footer {
            background-color: var(--dark);
            color: white;
            padding: 40px 0;
            margin-top: 50px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
        }

        .footer-section h3 {
            font-size: 20px;
            margin-bottom: 20px;
            color: var(--primary);
        }

        .footer-section p {
            margin-bottom: 10px;
            color: #dcdde1;
        }

        .social-icons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-icons a {
            color: white;
            font-size: 20px;
            transition: color 0.3s;
        }

        .social-icons a:hover {
            color: var(--primary);
        }

        .footer-bottom {
            text-align: center;
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid #57606f;
            color: #dcdde1;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }
            
            nav ul {
                gap: 15px;
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .hero h2 {
                font-size: 32px;
            }
            
            .hero p {
                font-size: 16px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <i class="fas fa-film"></i>
                <h1>Tollywood Tickets</h1>
            </div>
            <nav>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Movies</a></li>
                    <li><a href="#">Theaters</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <h2>Book Your Tollywood Movie Tickets</h2>
            <p>Experience the magic of Telugu cinema with the latest blockbusters on the big screen. Book your tickets now for an unforgettable experience.</p>
            <a href="#movies" class="btn">Browse Movies</a>
        </div>
    </section>

    <!-- Movies Section -->
    <section class="container" id="movies">
        <h2 class="section-title">Now Showing</h2>
        <div class="movies-grid" id="movies-container">
            <!-- Movie cards will be generated by JavaScript -->
        </div>
    </section>

    <!-- Booking Modal -->
    <div class="modal" id="booking-modal">
        <div class="modal-content">
            <span class="close-modal" id="close-modal">&times;</span>
            <div class="booking-form">
                <h3>Book Your Tickets</h3>
                <div class="form-group">
                    <label for="movie-select">Movie</label>
                    <select id="movie-select" disabled>
                        <!-- Options will be filled by JavaScript -->
                    </select>
                </div>
                <div class="form-group">
                    <label for="theater-select">Theater</label>
                    <select id="theater-select">
                        <option value="">Select Theater</option>
                        <option value="PVR Cinemas">PVR Cinemas</option>
                        <option value="INOX">INOX</option>
                        <option value="Cinepolis">Cinepolis</option>
                        <option value="AMB Cinemas">AMB Cinemas</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Show Times</label>
                    <div class="showtimes">
                        <div class="time-option" data-time="09:00 AM">09:00 AM</div>
                        <div class="time-option" data-time="12:30 PM">12:30 PM</div>
                        <div class="time-option" data-time="04:00 PM">04:00 PM</div>
                        <div class="time-option" data-time="07:30 PM">07:30 PM</div>
                        <div class="time-option" data-time="10:45 PM">10:45 PM</div>
                    </div>
                </div>
                <div class="form-group">
                    <label for="seats">Number of Seats</label>
                    <input type="number" id="seats" min="1" max="10" value="1">
                </div>
                <button class="btn" id="confirm-booking">Confirm Booking</button>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>About Us</h3>
                    <p>Your one-stop destination for booking Tollywood movie tickets. We bring the best of Telugu cinema to your fingertips.</p>
                </div>
                <div class="footer-section">
                    <h3>Contact Us</h3>
                    <p><i class="fas fa-map-marker-alt"></i> Hyderabad, Telangana</p>
                    <p><i class="fas fa-phone"></i> +91 9876543210</p>
                    <p><i class="fas fa-envelope"></i> info@tollywoodtickets.com</p>
                </div>
                <div class="footer-section">
                    <h3>Follow Us</h3>
                    <div class="social-icons">
                        <a href="#"><i class="fab fa-facebook"></i></a>
                        <a href="#"><i class="fab fa-twitter"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-youtube"></i></a>
                    </div>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2023 Tollywood Tickets. All Rights Reserved.</p>
            </div>
        </div>
    </footer>

    <script>
        // Movie data
        const movies = [
            {
                id: 1,
                title: "Pushpa: The Rise",
                image: "https://images.unsplash.com/photo-1633177317976-3f9bc45e1d1d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=735&q=80",
                duration: "2h 59m",
                rating: "8.2/10",
                genre: "Action, Drama"
            },
            {
                id: 2,
                title: "RRR",
                image: "https://images.unsplash.com/photo-1596541223130-5ccd5deb6e99?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80",
                duration: "3h 7m",
                rating: "8.0/10",
                genre: "Action, Drama"
            },
            {
                id: 3,
                title: "Baahubali 2",
                image: "https://images.unsplash.com/photo-1585951237318-9ea5e175b891?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80",
                duration: "2h 47m",
                rating: "8.2/10",
                genre: "Action, Adventure"
            },
            {
                id: 4,
                title: "Ala Vaikunthapurramuloo",
                image: "https://images.unsplash.com/photo-1585646793892-e0c3ddd763b9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80",
                duration: "2h 42m",
                rating: "7.5/10",
                genre: "Action, Comedy"
            },
            {
                id: 5,
                title: "Sarkaru Vaari Paata",
                image: "https://images.unsplash.com/photo-1616530940355-351fabd9524b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=735&q=80",
                duration: "2h 38m",
                rating: "7.0/10",
                genre: "Action, Drama"
            },
            {
                id: 6,
                title: "Bheemla Nayak",
                image: "https://images.unsplash.com/photo-1598885153329-ef1c0bf013d9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=698&q=80",
                duration: "2h 45m",
                rating: "7.6/10",
                genre: "Action, Drama"
            }
        ];

        // DOM elements
        const moviesContainer = document.getElementById('movies-container');
        const bookingModal = document.getElementById('booking-modal');
        const closeModal = document.getElementById('close-modal');
        const movieSelect = document.getElementById('movie-select');
        const confirmBooking = document.getElementById('confirm-booking');
        const timeOptions = document.querySelectorAll('.time-option');

        // Generate movie cards
        function generateMovieCards() {
            moviesContainer.innerHTML = '';
            
            movies.forEach(movie => {
                const card = document.createElement('div');
                card.className = 'movie-card';
                card.innerHTML = `
                    <div class="movie-poster">
                        <img src="${movie.image}" alt="${movie.title}">
                    </div>
                    <div class="movie-info">
                        <h3 class="movie-title">${movie.title}</h3>
                        <div class="movie-details">
                            <span>${movie.duration}</span>
                            <span>${movie.rating}</span>
                        </div>
                        <p>${movie.genre}</p>
                        <div class="movie-actions">
                            <button class="btn book-btn" data-movie-id="${movie.id}">Book Tickets</button>
                        </div>
                    </div>
                `;
                
                moviesContainer.appendChild(card);
            });
            
            // Add event listeners to book buttons
            document.querySelectorAll('.book-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const movieId = this.getAttribute('data-movie-id');
                    openBookingModal(movieId);
                });
            });
        }

        // Open booking modal
        function openBookingModal(movieId) {
            const movie = movies.find(m => m.id == movieId);
            
            if (movie) {
                movieSelect.innerHTML = `<option value="${movie.id}">${movie.title}</option>`;
                bookingModal.style.display = 'flex';
            }
        }

        // Close modal
        closeModal.addEventListener('click', function() {
            bookingModal.style.display = 'none';
        });

        // Time selection
        timeOptions.forEach(option => {
            option.addEventListener('click', function() {
                timeOptions.forEach(opt => opt.classList.remove('selected'));
                this.classList.add('selected');
            });
        });

        // Confirm booking
        confirmBooking.addEventListener('click', function() {
            const theater = document.getElementById('theater-select').value;
            const seats = document.getElementById('seats').value;
            const selectedTime = document.querySelector('.time-option.selected');
            
            if (!theater) {
                alert('Please select a theater');
                return;
            }
            
            if (!selectedTime) {
                alert('Please select a show time');
                return;
            }
            
            const time = selectedTime.getAttribute('data-time');
            const movieId = movieSelect.value;
            const movie = movies.find(m => m.id == movieId);
            
            alert(`Booking confirmed!\n\nMovie: ${movie.title}\nTheater: ${theater}\nTime: ${time}\nSeats: ${seats}\n\nEnjoy your movie!`);
            
            bookingModal.style.display = 'none';
            
            // Reset form
            document.getElementById('theater-select').value = '';
            document.getElementById('seats').value = '1';
            timeOptions.forEach(opt => opt.classList.remove('selected'));
        });

        // Close modal if clicked outside
        window.addEventListener('click', function(event) {
            if (event.target === bookingModal) {
                bookingModal.style.display = 'none';
            }
        });

        // Initialize the page
        generateMovieCards();
    </script>
</body>
</html>
