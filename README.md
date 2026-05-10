<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bloomberg Terminal | Professional Financial Platform</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        html, body { height: 100%; }
        body { 
            background: #0a0e27; 
            color: #ffffff; 
            font-family: 'Segoe UI', Arial, sans-serif;
            display: flex;
            flex-direction: column;
        }
        
        /* HEADER */
        .header {
            background: linear-gradient(135deg, #1a1f3a 0%, #0f1428 100%);
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid #00d4ff;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0, 212, 255, 0.1);
        }
        
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: #00d4ff;
            letter-spacing: 2px;
        }
        
        .search-bar {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            background: #1a1f3a;
            padding: 0.75rem 1rem;
            border-radius: 8px;
            border: 1px solid #00d4ff;
            width: 300px;
        }
        
        .search-bar input {
            background: none;
            border: none;
            color: #00d4ff;
            outline: none;
            width: 100%;
            font-size: 0.9rem;
        }
        
        .search-bar input::placeholder { color: #666; }
        
        .header-right {
            display: flex;
            gap: 1rem;
        }
        
        .btn-small {
            background: none;
            border: 1px solid #00d4ff;
            color: #00d4ff;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            cursor: pointer;
            font-size: 0.85rem;
            transition: all 0.3s;
        }
        
        .btn-small:hover {
            background: #00d4ff;
            color: #0a0e27;
        }
        
        /* MAIN LAYOUT */
        .container {
            display: flex;
            flex: 1;
            overflow: hidden;
        }
        
        /* SIDEBAR */
        .sidebar {
            width: 220px;
            background: #0f1428;
            border-right: 1px solid #1a3a4a;
            padding: 1.5rem 0;
            overflow-y: auto;
            flex-shrink: 0;
        }
        
        .nav-section {
            margin-bottom: 2rem;
            padding: 0 1rem;
        }
        
        .nav-title {
            color: #00d4ff;
            font-size: 0.7rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 0.75rem;
            opacity: 0.7;
        }
        
        .nav-item {
            padding: 0.75rem 1rem;
            color: #888;
            background: none;
            border: none;
            cursor: pointer;
            width: 100%;
            text-align: left;
            border-left: 3px solid transparent;
            transition: all 0.3s;
            font-size: 0.9rem;
        }
        
        .nav-item:hover {
            color: #00d4ff;
            border-left-color: #00d4ff;
            background: rgba(0, 212, 255, 0.05);
        }
        
        .nav-item.active {
            color: #00d4ff;
            border-left-color: #00d4ff;
            background: rgba(0, 212, 255, 0.1);
        }
        
        /* CONTENT */
        .content {
            flex: 1;
            overflow-y: auto;
            padding: 2rem;
            background: #0a0e27;
        }
        
        .page { display: none; }
        .page.active { display: block; }
        
        .page-title {
            font-size: 2rem;
            color: #ffffff;
            margin-bottom: 0.5rem;
        }
        
        .page-subtitle {
            color: #888;
            font-size: 0.9rem;
            margin-bottom: 2rem;
        }
        
        /* GRID */
        .grid-4 {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        .grid-3 {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        .grid-2 {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        /* CARDS */
        .card {
            background: linear-gradient(135deg, #1a1f3a 0%, #0f1428 100%);
            border: 1px solid #1a3a4a;
            border-radius: 8px;
            padding: 1.5rem;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .card:hover {
            border-color: #00d4ff;
            box-shadow: 0 0 20px rgba(0, 212, 255, 0.1);
        }
        
        .card-title {
            color: #00d4ff;
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 1rem;
            opacity: 0.8;
        }
        
        /* STOCK CARDS */
        .stock-card {
            background: linear-gradient(135deg, #1a1f3a 0%, #0f1428 100%);
            border: 1px solid #1a3a4a;
            border-radius: 8px;
            padding: 1.5rem;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .stock-card:hover {
            border-color: #00d4ff;
            box-shadow: 0 0 20px rgba(0, 212, 255, 0.2);
            transform: translateY(-2px);
        }
        
        .stock-symbol {
            color: #00d4ff;
            font-size: 1.25rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }
        
        .stock-company {
            color: #888;
            font-size: 0.8rem;
            margin-bottom: 1rem;
        }
        
        .stock-price {
            color: #ffffff;
            font-size: 1.75rem;
            font-weight: bold;
            margin: 0.5rem 0;
        }
        
        .stock-change {
            font-size: 0.9rem;
            font-weight: bold;
        }
        
        .positive { color: #00ff00; }
        .negative { color: #ff0000; }
        
        /* STATS */
        .stat-value {
            color: #00d4ff;
            font-size: 2rem;
            font-weight: bold;
            margin: 0.5rem 0;
        }
        
        .stat-label {
            color: #888;
            font-size: 0.8rem;
        }
        
        /* TABLE */
        .table-container {
            background: linear-gradient(135deg, #1a1f3a 0%, #0f1428 100%);
            border: 1px solid #1a3a4a;
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 2rem;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        thead {
            background: rgba(0, 212, 255, 0.05);
            border-bottom: 1px solid #1a3a4a;
        }
        
        th {
            padding: 1rem;
            text-align: left;
            color: #00d4ff;
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 600;
        }
        
        td {
            padding: 1rem;
            border-bottom: 1px solid #1a3a4a;
            color: #ffffff;
        }
        
        tbody tr:hover {
            background: rgba(0, 212, 255, 0.05);
            cursor: pointer;
        }
        
        .section-title {
            color: #00d4ff;
            font-size: 1.1rem;
            margin: 2rem 0 1rem 0;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .back-btn {
            background: none;
            border: 1px solid #00d4ff;
            color: #00d4ff;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            cursor: pointer;
            margin-bottom: 1.5rem;
            transition: all 0.3s;
            font-size: 0.9rem;
        }
        
        .back-btn:hover {
            background: #00d4ff;
            color: #0a0e27;
        }
        
        ::-webkit-scrollbar {
            width: 10px;
        }
        
        ::-webkit-scrollbar-track {
            background: #0f1428;
        }
        
        ::-webkit-scrollbar-thumb {
            background: #1a3a4a;
            border-radius: 5px;
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: #00d4ff;
        }
    </style>
</head>
<body>
    <!-- HEADER -->
    <div class="header">
        <div class="logo">📊 BLOOMBERG</div>
        <div class="search-bar">
            <input type="text" id="searchInput" placeholder="Search stocks...">
        </div>
        <div class="header-right">
            <button class="btn-small" onclick="alert('Settings')">⚙️ Settings</button>
            <button class="btn-small" onclick="alert('Account')">👤 Account</button>
        </div>
    </div>

    <!-- MAIN LAYOUT -->
    <div class="container">
        <!-- SIDEBAR -->
        <div class="sidebar">
            <div class="nav-section">
                <div class="nav-title">Dashboard</div>
                <button class="nav-item active" onclick="showPage('dashboard')">📊 Overview</button>
                <button class="nav-item" onclick="showPage('watchlist')">⭐ Watchlist</button>
                <button class="nav-item" onclick="showPage('portfolio')">💼 Portfolio</button>
            </div>
            
            <div class="nav-section">
                <div class="nav-title">Analysis</div>
                <button class="nav-item" onclick="showPage('screener')">🔍 Screener</button>
                <button class="nav-item" onclick="showPage('technicals')">📈 Technicals</button>
                <button class="nav-item" onclick="showPage('fundamentals')">📋 Fundamentals</button>
            </div>
            
            <div class="nav-section">
                <div class="nav-title">News & Events</div>
                <button class="nav-item" onclick="showPage('news')">📰 News</button>
                <button class="nav-item" onclick="showPage('calendar')">📅 Calendar</button>
                <button class="nav-item" onclick="showPage('earnings')">🎯 Earnings</button>
            </div>
        </div>

        <!-- CONTENT -->
        <div class="content">
            <!-- DASHBOARD -->
            <div id="dashboard" class="page active">
                <div class="page-title">Market Overview</div>
                <div class="page-subtitle">Real-time financial data and analysis</div>

                <h3 class="section-title">Market Indices</h3>
                <div class="grid-4">
                    <div class="card">
                        <div class="card-title">S&P 500</div>
                        <div class="stat-value">4,783.45</div>
                        <div class="stock-change positive">↑ +2.50 (+0.05%)</div>
                    </div>
                    <div class="card">
                        <div class="card-title">DOW JONES</div>
                        <div class="stat-value">37,456.89</div>
                        <div class="stock-change positive">↑ +125.30 (+0.34%)</div>
                    </div>
                    <div class="card">
                        <div class="card-title">NASDAQ</div>
                        <div class="stat-value">14,892.34</div>
                        <div class="stock-change positive">↑ +185.60 (+1.27%)</div>
                    </div>
                    <div class="card">
                        <div class="card-title">VIX</div>
                        <div class="stat-value">16.45</div>
                        <div class="stock-change negative">↓ -0.85 (-4.91%)</div>
                    </div>
                </div>

                <h3 class="section-title">Top Gainers</h3>
                <div class="grid-4">
                    <div class="stock-card" onclick="showStockDetail('NVDA')">
                        <div class="stock-symbol">NVDA</div>
                        <div class="stock-company">NVIDIA Corporation</div>
                        <div class="stock-price">$875.29</div>
                        <div class="stock-change positive">↑ +12.15 (+1.41%)</div>
                    </div>
                    <div class="stock-card" onclick="showStockDetail('TSLA')">
                        <div class="stock-symbol">TSLA</div>
                        <div class="stock-company">Tesla Inc.</div>
                        <div class="stock-price">$242.84</div>
                        <div class="stock-change positive">↑ +5.50 (+2.32%)</div>
                    </div>
                    <div class="stock-card" onclick="showStockDetail('META')">
                        <div class="stock-symbol">META</div>
                        <div class="stock-company">Meta Platforms Inc.</div>
                        <div class="stock-price">$485.20</div>
                        <div class="stock-change positive">↑ +8.40 (+1.76%)</div>
                    </div>
                    <div class="stock-card" onclick="showStockDetail('GOOGL')">
                        <div class="stock-symbol">GOOGL</div>
                        <div class="stock-company">Alphabet Inc.</div>
                        <div class="stock-price">$139.87</div>
                        <div class="stock-change positive">↑ +3.15 (+2.30%)</div>
                    </div>
                </div>

                <h3 class="section-title">All Stocks</h3>
                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Symbol</th>
                                <th>Company</th>
                                <th>Price</th>
                                <th>Change</th>
                                <th>% Change</th>
                                <th>Volume</th>
                                <th>Market Cap</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr onclick="showStockDetail('AAPL')">
                                <td><strong>AAPL</strong></td>
                                <td>Apple Inc.</td>
                                <td>$189.45</td>
                                <td>+2.50</td>
                                <td class="positive">+1.33%</td>
                                <td>45.2M</td>
                                <td>$2.98T</td>
                            </tr>
                            <tr onclick="showStockDetail('MSFT')">
                                <td><strong>MSFT</strong></td>
                                <td>Microsoft Corporation</td>
                                <td>$378.92</td>
                                <td>-1.20</td>
                                <td class="negative">-0.32%</td>
                                <td>22.1M</td>
                                <td>$2.82T</td>
                            </tr>
                            <tr onclick="showStockDetail('GOOGL')">
                                <td><strong>GOOGL</strong></td>
                                <td>Alphabet Inc.</td>
                                <td>$139.87</td>
                                <td>+3.15</td>
                                <td class="positive">+2.30%</td>
                                <td>28.5M</td>
                                <td>$1.76T</td>
                            </tr>
                            <tr onclick="showStockDetail('AMZN')">
                                <td><strong>AMZN</strong></td>
                                <td>Amazon.com Inc.</td>
                                <td>$178.45</td>
                                <td>-2.30</td>
                                <td class="negative">-1.27%</td>
                                <td>35.6M</td>
                                <td>$1.85T</td>
                            </tr>
                            <tr onclick="showStockDetail('TSLA')">
                                <td><strong>TSLA</strong></td>
                                <td>Tesla Inc.</td>
                                <td>$242.84</td>
                                <td>+5.50</td>
                                <td class="positive">+2.32%</td>
                                <td>125M</td>
                                <td>$770B</td>
                            </tr>
                            <tr onclick="showStockDetail('META')">
                                <td><strong>META</strong></td>
                                <td>Meta Platforms Inc.</td>
                                <td>$485.20</td>
                                <td>+8.40</td>
                                <td class="positive">+1.76%</td>
                                <td>18.9M</td>
                                <td>$1.23T</td>
                            </tr>
                            <tr onclick="showStockDetail('NVDA')">
                                <td><strong>NVDA</strong></td>
                                <td>NVIDIA Corporation</td>
                                <td>$875.29</td>
                                <td>+12.15</td>
                                <td class="positive">+1.41%</td>
                                <td>35.2M</td>
                                <td>$2.15T</td>
                            </tr>
                            <tr onclick="showStockDetail('AMD')">
                                <td><strong>AMD</strong></td>
                                <td>Advanced Micro Devices</td>
                                <td>$164.50</td>
                                <td>-3.20</td>
                                <td class="negative">-1.91%</td>
                                <td>52.1M</td>
                                <td>$268B</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- STOCK DETAIL -->
            <div id="stock-detail" class="page">
                <button class="back-btn" onclick="showPage('dashboard')">← Back to Dashboard</button>
                
                <div style="margin-bottom: 2rem;">
                    <div style="font-size: 2.5rem; font-weight: bold; color: #00d4ff; margin-bottom: 0.5rem;" id="detail-symbol">AAPL</div>
                    <div style="color: #888; font-size: 1rem; margin-bottom: 1rem;" id="detail-company">Apple Inc.</div>
                    <div style="font-size: 2.5rem; font-weight: bold; color: #ffffff; margin: 1rem 0;" id="detail-price">$189.45</div>
                    <div style="font-size: 1.2rem; font-weight: bold;" id="detail-change" class="stock-change positive">↑ +2.50 (+1.33%)</div>
                </div>

                <div class="grid-4">
                    <div class="card">
                        <div class="card-title">Open</div>
                        <div class="stat-value" id="detail-open">$187.10</div>
                    </div>
                    <div class="card">
                        <div class="card-title">High</div>
                        <div class="stat-value" id="detail-high">$190.50</div>
                    </div>
                    <div class="card">
                        <div class="card-title">Low</div>
                        <div class="stat-value" id="detail-low">$186.80</div>
                    </div>
                    <div class="card">
                        <div class="card-title">Volume</div>
                        <div class="stat-value" id="detail-volume">45.2M</div>
                    </div>
                </div>

                <div class="grid-2">
                    <div class="card">
                        <div class="card-title">52-Week High</div>
                        <div class="stat-value">$199.62</div>
                    </div>
                    <div class="card">
                        <div class="card-title">52-Week Low</div>
                        <div class="stat-value">$164.08</div>
                    </div>
                </div>

                <h3 class="section-title">Technical Indicators</h3>
                <div class="grid-3">
                    <div class="card">
                        <div class="card-title">RSI (14)</div>
                        <div class="stat-value">62.45</div>
                        <div style="color: #888; font-size: 0.8rem; margin-top: 0.5rem;">Neutral (50-70)</div>
                    </div>
                    <div class="card">
                        <div class="card-title">MACD</div>
                        <div class="stat-value positive">BULLISH</div>
                        <div style="color: #888; font-size: 0.8rem; margin-top: 0.5rem;">Positive signal</div>
                    </div>
                    <div class="card">
                        <div class="card-title">Moving Average (50)</div>
                        <div class="stat-value">$183.25</div>
                        <div style="color: #00ff00; font-size: 0.8rem; margin-top: 0.5rem;">Price above MA</div>
                    </div>
                </div>
            </div>

            <!-- WATCHLIST -->
            <div id="watchlist" class="page">
                <div class="page-title">My Watchlist</div>
                <div class="page-subtitle">Tracked stocks and alerts</div>

                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Symbol</th>
                                <th>Price</th>
                                <th>Change</th>
                                <th>% Change</th>
                                <th>Alert Price</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr onclick="showStockDetail('AAPL')">
                                <td><strong>AAPL</strong></td>
                                <td>$189.45</td>
                                <td>+2.50</td>
                                <td class="positive">+1.33%</td>
                                <td>$200</td>
                            </tr>
                            <tr onclick="showStockDetail('TSLA')">
                                <td><strong>TSLA</strong></td>
                                <td>$242.84</td>
                                <td>+5.50</td>
                                <td class="positive">+2.32%</td>
                                <td>$250</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- PORTFOLIO -->
            <div id="portfolio" class="page">
                <div class="page-title">Portfolio</div>
                <div class="page-subtitle">Your holdings and performance</div>

                <div class="grid-4">
                    <div class="card">
                        <div class="card-title">Total Value</div>
                        <div class="stat-value">$125,450</div>
                    </div>
                    <div class="card">
                        <div class="card-title">Total Gain/Loss</div>
                        <div class="stat-value positive">+$5,234</div>
                    </div>
                    <div class="card">
                        <div class="card-title">Return %</div>
                        <div class="stat-value positive">+4.35%</div>
                    </div>
                    <div class="card">
                        <div class="card-title">Cash Balance</div>
                        <div class="stat-value">$25,000</div>
                    </div>
                </div>

                <h3 class="section-title">Holdings</h3>
                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Symbol</th>
                                <th>Shares</th>
                                <th>Avg Cost</th>
                                <th>Current</th>
                                <th>Value</th>
                                <th>Gain/Loss</th>
                                <th>Return %</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><strong>AAPL</strong></td>
                                <td>50</td>
                                <td>$150.00</td>
                                <td>$189.45</td>
                                <td>$9,472.50</td>
                                <td class="positive">+$1,972.50</td>
                                <td class="positive">+26.30%</td>
                            </tr>
                            <tr>
                                <td><strong>MSFT</strong></td>
                                <td>25</td>
                                <td>$300.00</td>
                                <td>$378.92</td>
                                <td>$9,473.00</td>
                                <td class="positive">+$1,973.00</td>
                                <td class="positive">+26.43%</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- SCREENER -->
            <div id="screener" class="page">
                <div class="page-title">Stock Screener</div>
                <div class="page-subtitle">Filter and find stocks by criteria</div>

                <div class="grid-2">
                    <div class="card">
                        <div class="card-title">Market Cap</div>
                        <div style="margin: 1rem 0;">
                            <input type="number" placeholder="Min" style="width: 100%; padding: 0.5rem; background: #0a0e27; color: #00d4ff; border: 1px solid #1a3a4a; border-radius: 4px; margin-bottom: 0.5rem;">
                            <input type="number" placeholder="Max" style="width: 100%; padding: 0.5rem; background: #0a0e27; color: #00d4ff; border: 1px solid #1a3a4a; border-radius: 4px;">
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-title">P/E Ratio</div>
                        <div style="margin: 1rem 0;">
                            <input type="number" placeholder="Min" style="width: 100%; padding: 0.5rem; background: #0a0e27; color: #00d4ff; border: 1px solid #1a3a4a; border-radius: 4px; margin-bottom: 0.5rem;">
                            <input type="number" placeholder="Max" style="width: 100%; padding: 0.5rem; background: #0a0e27; color: #00d4ff; border: 1px solid #1a3a4a; border-radius: 4px;">
                        </div>
                    </div>
                </div>

                <button class="btn-small" style="padding: 0.75rem 2rem; margin: 2rem 0;">🔍 Run Screener</button>

                <h3 class="section-title">Results</h3>
                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Symbol</th>
                                <th>Market Cap</th>
                                <th>P/E Ratio</th>
                                <th>Dividend Yield</th>
                                <th>52W Change</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><strong>AAPL</strong></td>
                                <td>$2.98T</td>
                                <td>28.5</td>
                                <td>0.42%</td>
                                <td class="positive">+15.8%</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- NEWS -->
            <div id="news" class="page">
                <div class="page-title">Financial News</div>
                <div class="page-subtitle">Latest market news and updates</div>

                <div style="display: grid; gap: 1.5rem;">
                    <div class="card">
                        <div class="card-title">MARKET NEWS</div>
                        <h3 style="color: #ffffff; margin: 0.5rem 0;">S&P 500 Reaches All-Time High</h3>
                        <p style="color: #888; font-size: 0.9rem; margin: 0.75rem 0;">The stock market surged today with strong earnings reports and favorable economic data.</p>
                        <div style="color: #666; font-size: 0.8rem;">Reuters • 2 hours ago</div>
                    </div>

                    <div class="card">
                        <div class="card-title">EARNINGS</div>
                        <h3 style="color: #ffffff; margin: 0.5rem 0;">Apple Reports Record Q4 Revenue</h3>
                        <p style="color: #888; font-size: 0.9rem; margin: 0.75rem 0;">Apple announced record revenue, beating analyst expectations with strong iPhone sales.</p>
                        <div style="color: #666; font-size: 0.8rem;">Bloomberg • 4 hours ago</div>
                    </div>

                    <div class="card">
                        <div class="card-title">ANALYSIS</div>
                        <h3 style="color: #ffffff; margin: 0.5rem 0;">Tech Sector Momentum Continues</h3>
                        <p style="color: #888; font-size: 0.9rem; margin: 0.75rem 0;">Analysts expect technology stocks to maintain their upward trend as AI investments increase.</p>
                        <div style="color: #666; font-size: 0.8rem;">MarketWatch • 6 hours ago</div>
                    </div>
                </div>
            </div>

            <!-- CALENDAR -->
            <div id="calendar" class="page">
                <div class="page-title">Economic Calendar</div>
                <div class="page-subtitle">Upcoming economic events and earnings</div>

                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Date</th>
                                <th>Time</th>
                                <th>Event</th>
                                <th>Importance</th>
                                <th>Forecast</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Dec 15, 2024</td>
                                <td>2:00 PM</td>
                                <td>Fed Interest Rate Decision</td>
                                <td><span style="color: #ff0000;">●</span> High</td>
                                <td>5.00%</td>
                            </tr>
                            <tr>
                                <td>Dec 16, 2024</td>
                                <td>8:30 AM</td>
                                <td>CPI (Consumer Price Index)</td>
                                <td><span style="color: #ff0000;">●</span> High</td>
                                <td>3.1%</td>
                            </tr>
                            <tr>
                                <td>Dec 20, 2024</td>
                                <td>4:00 PM</td>
                                <td>Apple Earnings</td>
                                <td><span style="color: #ffcc00;">●</span> Medium</td>
                                <td>$2.18</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- EARNINGS -->
            <div id="earnings" class="page">
                <div class="page-title">Earnings Calendar</div>
                <div class="page-subtitle">Upcoming company earnings reports</div>

                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Date</th>
                                <th>Company</th>
                                <th>Symbol</th>
                                <th>EPS Est.</th>
                                <th>Revenue Est.</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Dec 20, 2024</td>
                                <td>Apple Inc.</td>
                                <td><strong>AAPL</strong></td>
                                <td>$2.18</td>
                                <td>$120.5B</td>
                            </tr>
                            <tr>
                                <td>Dec 21, 2024</td>
                                <td>Microsoft Corporation</td>
                                <td><strong>MSFT</strong></td>
                                <td>$3.45</td>
                                <td>$65.2B</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- TECHNICALS -->
            <div id="technicals" class="page">
                <div class="page-title">Technical Analysis</div>
                <div class="page-subtitle">Technical indicators and chart patterns</div>

                <div class="grid-3">
                    <div class="card">
                        <div class="card-title">Moving Average Crossover</div>
                        <div class="stat-value positive">BULLISH</div>
                        <div style="color: #888; font-size: 0.8rem; margin-top: 0.5rem;">50-day above 200-day</div>
                    </div>
                    <div class="card">
                        <div class="card-title">Relative Strength Index</div>
                        <div class="stat-value">62.45</div>
                        <div style="color: #888; font-size: 0.8rem; margin-top: 0.5rem;">Neutral momentum</div>
                    </div>
                    <div class="card">
                        <div class="card-title">MACD Signal</div>
                        <div class="stat-value positive">BULLISH</div>
                        <div style="color: #888; font-size: 0.8rem; margin-top: 0.5rem;">Above signal line</div>
                    </div>
                </div>
            </div>

            <!-- FUNDAMENTALS -->
            <div id="fundamentals" class="page">
                <div class="page-title">Fundamental Analysis</div>
                <div class="page-subtitle">Financial metrics and ratios</div>

                <div class="grid-3">
                    <div class="card">
                        <div class="card-title">P/E Ratio</div>
                        <div class="stat-value">28.5</div>
                        <div style="color: #888; font-size: 0.8rem; margin-top: 0.5rem;">Industry avg: 22.1</div>
                    </div>
                    <div class="card">
                        <div class="card-title">Price to Book</div>
                        <div class="stat-value">45.2</div>
                        <div style="color: #888; font-size: 0.8rem; margin-top: 0.5rem;">High valuation</div>
                    </div>
                    <div class="card">
                        <div class="card-title">Debt to Equity</div>
                        <div class="stat-value">0.92</div>
                        <div style="color: #888; font-size: 0.8rem; margin-top: 0.5rem;">Moderate leverage</div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        const stocks = {
            'AAPL': { symbol: 'AAPL', company: 'Apple Inc.', price: 189.45, change: 2.50, percent: 1.33, open: 187.10, high: 190.50, low: 186.80, volume: '45.2M' },
            'MSFT': { symbol: 'MSFT', company: 'Microsoft Corporation', price: 378.92, change: -1.20, percent: -0.32, open: 380.15, high: 381.50, low: 377.80, volume: '22.1M' },
            'GOOGL': { symbol: 'GOOGL', company: 'Alphabet Inc.', price: 139.87, change: 3.15, percent: 2.30, open: 136.70, high: 140.50, low: 136.50, volume: '28.5M' },
            'AMZN': { symbol: 'AMZN', company: 'Amazon.com Inc.', price: 178.45, change: -2.30, percent: -1.27, open: 180.75, high: 181.20, low: 177.90, volume: '35.6M' },
            'TSLA': { symbol: 'TSLA', company: 'Tesla Inc.', price: 242.84, change: 5.50, percent: 2.32, open: 237.30, high: 244.50, low: 236.80, volume: '125M' },
            'META': { symbol: 'META', company: 'Meta Platforms Inc.', price: 485.20, change: 8.40, percent: 1.76, open: 476.75, high: 487.50, low: 475.60, volume: '18.9M' },
            'NVDA': { symbol: 'NVDA', company: 'NVIDIA Corporation', price: 875.29, change: 12.15, percent: 1.41, open: 863.10, high: 878.50, low: 862.80, volume: '35.2M' },
            'AMD': { symbol: 'AMD', company: 'Advanced Micro Devices', price: 164.50, change: -3.20, percent: -1.91, open: 167.70, high: 168.90, low: 163.45, volume: '52.1M' }
        };

        function showPage(pageName) {
            document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
            document.getElementById(pageName).classList.add('active');
            
            document.querySelectorAll('.nav-item').forEach(item => item.classList.remove('active'));
            event.target.classList.add('active');
        }

        function showStockDetail(symbol) {
            const stock = stocks[symbol];
            document.getElementById('detail-symbol').textContent = stock.symbol;
            document.getElementById('detail-company').textContent = stock.company;
            document.getElementById('detail-price').textContent = '$' + stock.price.toFixed(2);
            
            const changeClass = stock.change >= 0 ? 'positive' : 'negative';
            const changeSign = stock.change >= 0 ? '↑' : '↓';
            document.getElementById('detail-change').textContent = changeSign + ' ' + (stock.change >= 0 ? '+' : '') + stock.change.toFixed(2) + ' (' + (stock.percent >= 0 ? '+' : '') + stock.percent.toFixed(2) + '%)';
            document.getElementById('detail-change').className = 'stock-change ' + changeClass;
            
            document.getElementById('detail-open').textContent = '$' + stock.open.toFixed(2);
            document.getElementById('detail-high').textContent = '$' + stock.high.toFixed(2);
            document.getElementById('detail-low').textContent = '$' + stock.low.toFixed(2);
            document.getElementById('detail-volume').textContent = stock.volume;

            showPage('stock-detail');
        }

        document.getElementById('searchInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                const symbol = this.value.toUpperCase();
                if (stocks[symbol]) {
                    showStockDetail(symbol);
                    this.value = '';
                } else {
                    alert('Stock symbol not found');
                }
            }
        });
    </script>
</body>
</html>
