<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>MyBusiness - Modern Business</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
<script src="https://www.paypal.com/sdk/js?client-id=YOUR_PAYPAL_CLIENT_ID&currency=USD"></script>
<script src="https://js.stripe.com/v3/"></script>
<style>
* { margin:0; padding:0; box-sizing:border-box; font-family:'Poppins',sans-serif; }
body { background:#0f172a; color:white; }
header { padding:20px 50px; display:flex; justify-content:space-between; align-items:center; background:#020617; }
header h1 { color:#38bdf8; }
nav a { margin-left:20px; text-decoration:none; color:white; cursor:pointer; }
section { padding:80px 20px; text-align:center; }
.hero { height:90vh; display:flex; flex-direction:column; justify-content:center; align-items:center; }
.hero h2 { font-size:42px; margin-bottom:20px; }
.hero p { max-width:600px; margin-bottom:30px; }
.btn { padding:12px 25px; background:#38bdf8; border:none; border-radius:6px; cursor:pointer; font-weight:bold; }
.cards, .pricing { display:flex; flex-wrap:wrap; justify-content:center; gap:30px; margin-top:40px; }
.card, .price-card { background:#020617; padding:30px; border-radius:10px; width:280px; }
.price-card h2 { margin:15px 0; }
footer { text-align:center; padding:20px; background:#020617; }
.dashboard { display:none; text-align:left; max-width:1000px; margin:auto; }
.dashboard h2 { margin-bottom:20px; }
.dashboard table { width:100%; border-collapse:collapse; }
.dashboard th, .dashboard td { border:1px solid #334155; padding:10px; }
.dashboard th { background:#1e293b; }
input { padding:10px; margin:10px 0; width:100%; border-radius:5px; border:none; }
@media(max-width:768px){
.hero h2 { font-size:30px; }
}
</style>
</head>
<body><header>
<h1>MyBusiness</h1>
<nav>
<a onclick="showSection('home')">Home</a>
<a onclick="showSection('services')">Services</a>
<a onclick="showSection('pricing')">Pricing</a>
<a onclick="showSection('dashboard')">Dashboard</a>
</nav>
</header><section id="home" class="hero">
<h2>Grow Your Business Online</h2>
<p>Modern solutions to help your business succeed in the digital world.</p>
<button class="btn" onclick="showSection('pricing')">Get Started</button>
</section><section id="services" style="display:none;">
<h2>Our Services</h2>
<div class="cards">
<div class="card"><h3>Web Design</h3><p>Modern responsive websites.</p></div>
<div class="card"><h3>Marketing</h3><p>Grow your audience and revenue.</p></div>
<div class="card"><h3>Consulting</h3><p>Professional strategy & scaling.</p></div>
</div>
</section><section id="pricing" style="display:none;">
<h2>Pricing</h2>
<div class="pricing"><div class="price-card">
<h3>Starter - $50</h3>
<div id="paypal-button-container"></div>
<br>
<button class="btn" onclick="stripeCheckout(50)">Pay with Card</button>
<br><br>
<button class="btn" onclick="mobileMoney()">Mobile Money</button>
</div></div>
</section><section id="dashboard" class="dashboard">
<h2>Admin Dashboard</h2>
<h3>Recent Orders</h3>
<table>
<tr><th>Order ID</th><th>Customer</th><th>Amount</th><th>Status</th></tr>
<tr><td>#001</td><td>John Doe</td><td>$50</td><td>Paid</td></tr>
<tr><td>#002</td><td>Jane Smith</td><td>$120</td><td>Pending</td></tr>
</table>
<br>
<h3>Add Product</h3>
<input type="text" placeholder="Product Name">
<input type="number" placeholder="Price">
<button class="btn">Save Product</button>
</section><footer>
<p>© 2026 MyBusiness. All rights reserved.</p>
</footer><script>
function showSection(id){
document.querySelectorAll('section').forEach(sec=>sec.style.display='none');
document.getElementById(id).style.display='block';
}

paypal.Buttons({
createOrder: function(data, actions) {
return actions.order.create({
purchase_units: [{ amount: { value: '50.00' } }]
});
},
onApprove: function(data, actions) {
return actions.order.capture().then(function(details) {
alert('Payment completed by ' + details.payer.name.given_name);
});
}
}).render('#paypal-button-container');

function stripeCheckout(amount){
var stripe = Stripe('YOUR_STRIPE_PUBLIC_KEY');
alert('Connect Stripe backend to complete payment for $'+amount);
}

function mobileMoney(){
alert('Integrate your local Mobile Money API (e.g., M-Pesa, MTN, etc.) here.');
}
</script></body>
</html>
