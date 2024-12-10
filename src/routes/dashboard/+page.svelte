<script>
    // Any necessary imports or reactive data for the dashboard
  </script>
  
  <style>
    .dashboard {
      padding: 2rem;
      background-color: #f9fafb;
      min-height: 100vh;
    }
  
    .welcome {
      margin-bottom: 2rem;
    }
  
    .welcome h2 {
      margin: 0;
      font-size: 1.5rem;
      font-weight: bold;
      color: #333;
    }
  
    .welcome p {
      font-size: 1rem;
      color: #666;
    }
  
    .grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr); /* Four columns */
      grid-template-rows: auto;
      grid-template-areas:
        "metric1 metric2 metric3 metric4"
        "charts charts charts recent"
        "stock1 stock1 stock2 stock2";
      gap: 1.5rem;
    }
  
    .card {
      background-color: white;
      padding: 1.5rem;
      border-radius: 0.3rem;
      box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
  
    .metric1 { grid-area: metric1; }
    .metric2 { grid-area: metric2; }
    .metric3 { grid-area: metric3; }
    .metric4 { grid-area: metric4; }
    .charts { grid-area: charts; }
    .recent { grid-area: recent; }
    .stock1 { grid-area: stock1; }
    .stock2 { grid-area: stock2; }
  
    /* Card typography */
    .card h2 {
      font-size: 1.2rem;
      font-weight: bold;
      margin: 0;
      color: #333;
    }
  
    .card p {
      margin: 0.5rem 0 0;
      font-size: 0.8rem;
      color: #666;
    }
  </style>
  
  <div class="dashboard">
    <!-- Welcome section -->
    <div class="welcome">
      <h2>Welcome Back, Eliziah!</h2>
      <p>Here's your Analytic Details</p>
    </div>
  
    <!-- Grid section -->
    <div class="grid">
      <!-- Metric cards -->
      <div class="card metric1">
        <h2>$54,000</h2>
        <p>Total Sale</p>
      </div>
      <div class="card metric2">
        <h2>$54,000</h2>
        <p>Total Sale</p>
      </div>
      <div class="card metric3">
        <h2>$54,000</h2>
        <p>Total Sale</p>
      </div>
      <div class="card metric4">
        <h2>$54,000</h2>
        <p>Total Sale</p>
      </div>
  
      <!-- Charts and activity section -->
      <div class="card charts">
        <h2>Charts</h2>
        <!-- Placeholder for charts -->
      </div>
      <div class="card recent">
        <h2>Recent Activity</h2>
        <!-- Placeholder for activity -->
      </div>
  
      <!-- Stock Alerts -->
      <div class="card stock1">
        <h2>Stock Alert</h2>
        <!-- Placeholder for stock alert -->
      </div>
      <div class="card stock2">
        <h2>Stock Alert</h2>
        <!-- Placeholder for stock alert -->
      </div>
    </div>
  </div>
  