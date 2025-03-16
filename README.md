<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kripto Para Takip</title>
    <meta name="description" content="Kripto para fiyatları, grafikleri ve piyasa değerleri">
    
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <style>
        body { background-color: #1a1f2e; color: #ffffff; }
        .navbar { background-color: #232842 !important; padding: 1rem 0; }
        .nav-links { display: flex; align-items: center; }
        .nav-links a { text-decoration: none; font-size: 14px; opacity: 0.8; transition: opacity 0.2s; color: #ffffff; }
        .nav-links a:hover { opacity: 1; }
        .dropdown-menu { background-color: #232842; border: 1px solid #2d334d; min-width: 250px; padding: 0; margin-top: 0.5rem; }
        .dropdown-menu .submenu { display: grid; grid-template-columns: repeat(2, 1fr); padding: 15px; }
        .dropdown-menu h6 { color: #8f9bb3; padding: 10px 15px; margin: 0; border-bottom: 1px solid #2d334d; }
        .nav-item.dropdown:hover .dropdown-menu { display: block; }
        @media (max-width: 1200px) { .nav-links { display: none; } }
        .search-input { background-color: #1a1f2e; border: 1px solid #2d334d; color: #ffffff; }
        .search-input:focus { background-color: #1a1f2e; color: #ffffff; }
        .crypto-table { background-color: #232842; border-radius: 10px; padding: 20px; margin-top: 20px; overflow-x: auto; }
        .crypto-row { display: grid; grid-template-columns: repeat(9, minmax(100px, 1fr)); padding: 15px; border-bottom: 1px solid #2d334d; align-items: center; transition: background-color 0.2s; }
        .crypto-row:hover { background-color: #2a3052; }
        .chart-container { height: 60px; width: 100%; max-width: 280px; }
        .crypto-row > div { padding: 0 10px; }
        .crypto-name { display: flex; align-items: center; gap: 10px; }
        .crypto-name img { width: 32px; height: 32px; border-radius: 50%; }
        .percentage { font-weight: 500; padding: 4px 8px; border-radius: 6px; background-color: rgba(0, 255, 136, 0.1); }
        .percentage.down { background-color: rgba(255, 77, 77, 0.1); }
        .header-row { font-weight: bold; color: #8f9bb3; }
        .price-up { color: #00ff88; }
        .price-down { color: #ff4d4d; }
        .market-overview { display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px; margin-bottom: 20px; }
        .overview-card { background-color: #232842; border-radius: 10px; padding: 15px; }
        .trending-section { display: grid; grid-template-columns: repeat(2, 1fr); gap: 20px; margin: 20px 0; }
        .news-feed { background-color: #232842; border-radius: 10px; padding: 20px; margin: 20px 0; }
        .news-item { padding: 15px; border-bottom: 1px solid #2d334d; }
        .news-meta { color: #8f9bb3; font-size: 0.9em; }
    </style>
</head>
<body>
    <nav class="navbar navbar-dark">
        <div class="container">
            <div class="d-flex align-items-center">
                <a class="navbar-brand" href="#">Crypto Tracker</a>
                <div class="nav-links ms-4">
                    <a href="#" class="text-light me-3">Markets</a>
                    <a href="#" class="text-light me-3">DexScan</a>
                    <a href="#" class="text-light me-3">Portfolio</a>
                    <a href="#" class="text-light me-3">News</a>
                </div>
            </div>
            <form class="d-flex">
                <input class="form-control search-input me-2" type="search" placeholder="Search Crypto...">
                <button class="btn btn-outline-light" type="submit">Search</button>
            </form>
        </div>
    </nav>

    <div class="container mt-4">
        <div class="market-header">
            <h1 class="h3">Today's Cryptocurrency Prices by Market Cap</h1>
            <p class="text-muted">The global crypto market cap is $2.75T, a 1.67% increase over the last day. <a href="#" class="text-info">Read More</a></p>
        </div>

        <div class="row mt-4">
            <div class="col-md-8">
                <div class="trending-coins mb-4">
                    <h5>Trending Coins</h5>
                    <div class="row">
                        <div class="col-md-4 mb-3">
                            <div class="coin-item">
                                <img src="placeholder.png" alt="ZRO" width="24">
                                <span>ZRO</span>
                                <span class="price-up">$2.25</span>
                                <span class="price-up">28.76%</span>
                            </div>
                        </div>
                        <!-- Add more trending coins -->
                    </div>
                </div>

                <div class="dexscan-trending mb-4">
                    <h5>Trending on DexScan</h5>
                    <div class="row">
                        <div class="col-md-4 mb-3">
                            <div class="pair-item">
                                <div class="pair-icons">
                                    <img src="placeholder.png" alt="Broccoli" width="20">
                                    <img src="placeholder.png" alt="WBNB" width="20">
                                </div>
                                <span>Broccoli/WBNB</span>
                                <span class="price-up">15.26%</span>
                            </div>
                        </div>
                        <!-- Add more trending pairs -->
                    </div>
                </div>
            </div>

            <div class="col-md-4">
                <div class="market-stats">
                    <div class="stat-item mb-3">
                        <h6>Market Cap</h6>
                        <div class="h4">$2.75T</div>
                        <span class="price-up">↑1.67%</span>
                    </div>
                    <div class="stat-item mb-3">
                        <h6>Fear & Greed</h6>
                        <div class="h4">22</div>
                        <span>Fear</span>
                    </div>
                    <!-- Add more market stats -->
                </div>
            </div>
        </div>
    </div>

    <div class="container crypto-table">
        <div class="crypto-row header-row">
            <div>Name</div>
            <div>Price</div>
            <div>1h %</div>
            <div>24h %</div>
            <div>7d %</div>
            <div>Market Cap</div>
            <div>Volume(24h)</div>
            <div>Circulating Supply</div>
            <div>Last 7 Days</div>
        </div>
        <div id="cryptoList">
            <!-- Crypto rows will be added here -->
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        async function getCryptoData() {
            try {
                const response = await fetch('https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=10&sparkline=true');
                const data = await response.json();
                displayCryptos(data);
            } catch (error) {
                console.error('Error:', error);
            }
        }

        function displayCryptos(cryptos) {
            const cryptoList = document.getElementById('cryptoList');
            cryptoList.innerHTML = cryptos.map((crypto, index) => `
                <div class="crypto-row">
                    <div class="crypto-name">
                        <img src="${crypto.image}" alt="${crypto.name}" width="32">
                        <div>${crypto.name} <small class="text-muted">${crypto.symbol.toUpperCase()}</small></div>
                    </div>
                    <div>$${crypto.current_price.toLocaleString(undefined, { maximumFractionDigits: 2 })}</div>
                    <div class="${crypto.price_change_percentage_24h > 0 ? 'price-up' : 'price-down'}">${crypto.price_change_percentage_24h?.toFixed(2)}%</div>
                    <div>$${crypto.market_cap.toLocaleString(undefined, { maximumFractionDigits: 0 })}</div>
                    <div>$${crypto.total_volume.toLocaleString(undefined, { maximumFractionDigits: 0 })}</div>
                    <div>${Math.round(crypto.circulating_supply).toLocaleString()} ${crypto.symbol.toUpperCase()}</div>
                    <div class="chart-container">
                        <canvas id="chart-${index}"></canvas>
                    </div>
                </div>
            `).join('');
            
            cryptos.forEach((crypto, index) => createChart(crypto, index));
        }

        function createChart(crypto, index) {
            const ctx = document.getElementById(`chart-${index}`).getContext('2d');
            new Chart(ctx, {
                type: 'line',
                data: {
                    labels: [...Array(crypto.sparkline_in_7d.price.length).keys()],
                    datasets: [{
                        data: crypto.sparkline_in_7d.price,
                        borderColor: crypto.price_change_percentage_24h > 0 ? '#00ff88' : '#ff4d4d',
                        backgroundColor: crypto.price_change_percentage_24h > 0 ? 'rgba(0,255,136,0.1)' : 'rgba(255,77,77,0.1)',
                        borderWidth: 2,
                        tension: 0.4,
                        pointRadius: 0
                    }]
                },
                options: {
                    plugins: { legend: { display: false } },
                    scales: { x: { display: false }, y: { display: false } },
                    responsive: true,
                    maintainAspectRatio: false
                }
            });
        }

        getCryptoData();
        setInterval(getCryptoData, 60000);
    </script>
</body>
</html>
