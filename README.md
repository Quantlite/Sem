# MWP Lab – 10 Runnable Experiments

Each experiment is a **single HTML file**. Save or download the file and open it in a browser. No separate frontend/backend files are included.

**Note:** Experiments 6–8 are browser-based demonstrations of REST operations, full-stack data flow, and JWT-style login. They are not real Express/MongoDB server deployments. Experiment 4 loads React from a CDN and needs an internet connection.

## Experiment 01
File: `Experiment_01_Portfolio.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Personal Portfolio</title>
<style>
*{box-sizing:border-box}body{margin:0;font:16px Arial;background:#f3f6fb;color:#182235}
header{background:#182b49;color:white;padding:55px 20px;text-align:center}
header h1{font-size:2.5rem;margin:0 0 10px}header p{color:#dce7f7}
nav{background:#10203a;padding:14px;text-align:center;position:sticky;top:0}
nav a{color:white;text-decoration:none;margin:0 14px}
main{max-width:900px;margin:25px auto;padding:0 18px}
section{background:white;padding:24px;margin:18px 0;border-radius:12px;box-shadow:0 3px 14px #15243a12}
h2{color:#2355a0}.tag{display:inline-block;background:#e6efff;padding:8px 12px;border-radius:20px;margin:5px}
footer{text-align:center;padding:25px;color:#64748b}
</style></head>
<body>
<header><h1>Alex Morgan</h1><p>Computer Science Student | Web Developer | Problem Solver</p></header>
<nav><a href="#about">About</a><a href="#skills">Skills</a><a href="#projects">Projects</a><a href="#contact">Contact</a></nav>
<main>
<section id="about"><h2>About Me</h2><p>Hello! I am a student interested in building useful and creative web applications. I enjoy learning new technologies and solving problems.</p></section>
<section id="skills"><h2>Skills</h2><span class="tag">HTML</span><span class="tag">CSS</span><span class="tag">JavaScript</span><span class="tag">Python</span><span class="tag">React</span></section>
<section id="projects"><h2>Projects</h2><h3>To-Do Application</h3><p>A simple application to manage daily tasks.</p><h3>Weather Dashboard</h3><p>A dashboard that displays weather information.</p></section>
<section id="contact"><h2>Contact</h2><p>Email: alex@example.com</p><p>LinkedIn: linkedin.com/in/alexmorgan</p></section>
</main><footer>© 2026 Alex Morgan · Personal Portfolio</footer>
</body></html>
```

## Experiment 02
File: `Experiment_02_To_Do_List.html`

```html
<!DOCTYPE html>
<html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>To-Do List</title><style>
body{font:16px Arial;background:#eef2f8;margin:0;padding:35px}.app{max-width:550px;margin:auto;background:white;padding:25px;border-radius:14px;box-shadow:0 5px 22px #0001}
h1{margin-top:0;color:#213b65}form{display:flex;gap:8px}input{flex:1;padding:12px;border:1px solid #bbc6d5;border-radius:7px}
button{padding:11px 15px;border:0;border-radius:7px;background:#245bb5;color:white;cursor:pointer}
ul{padding:0;list-style:none}li{display:flex;align-items:center;gap:10px;padding:12px 4px;border-bottom:1px solid #e6eaf0}
li span{flex:1}li.done span{text-decoration:line-through;color:#8993a3}.delete{background:#d94848}
</style></head><body><div class="app"><h1>My To-Do List</h1>
<form id="form"><input id="task" placeholder="Enter a task..." required><button>Add</button></form>
<ul id="list"></ul><p id="count">0 tasks</p></div>
<script>
const form=document.getElementById('form'),input=document.getElementById('task'),list=document.getElementById('list'),count=document.getElementById('count');
function update(){count.textContent=list.children.length+' tasks';}
form.addEventListener('submit',e=>{e.preventDefault();const li=document.createElement('li'),check=document.createElement('input'),span=document.createElement('span'),del=document.createElement('button');check.type='checkbox';span.textContent=input.value;del.textContent='Delete';del.className='delete';check.onchange=()=>li.classList.toggle('done',check.checked);del.onclick=()=>{li.remove();update();};li.append(check,span,del);list.append(li);input.value='';update();});
</script></body></html>
```

## Experiment 03
File: `Experiment_03_Form_Validation.html`

```html
<!DOCTYPE html>
<html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Form Validation</title><style>
body{font:16px Arial;background:#eef3f8;padding:30px}.box{max-width:460px;margin:auto;background:white;padding:26px;border-radius:12px}
label{display:block;margin-top:14px}input{width:100%;padding:11px;margin-top:6px;border:1px solid #bac5d3;border-radius:6px;box-sizing:border-box}
button{margin-top:20px;padding:12px 18px;background:#235bb4;color:white;border:0;border-radius:6px}
#error{color:#c62828}#success{color:#187b42}
</style></head><body><div class="box"><h1>Registration Form</h1>
<form id="register" novalidate>
<label>Name<input id="name" required></label>
<label>Email<input id="email" type="text" required></label>
<label>Password<input id="password" type="password" required></label>
<label>Phone<input id="phone" type="text" required></label>
<button>Register</button></form><p id="error"></p><p id="success"></p></div>
<script>
document.getElementById('register').addEventListener('submit',e=>{
e.preventDefault();let name=document.getElementById('name').value.trim(),email=document.getElementById('email').value.trim(),pass=document.getElementById('password').value,phone=document.getElementById('phone').value.trim();
let errors=[];if(!/^[A-Za-z ]{2,}$/.test(name))errors.push('Enter a valid name.');if(!/^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$/.test(email))errors.push('Enter a valid email.');if(!/^(?=.*[A-Za-z])(?=.*\\d).{8,}$/.test(pass))errors.push('Password must be 8+ characters with a letter and number.');if(!/^[0-9]{10}$/.test(phone))errors.push('Phone number must contain 10 digits.');
document.getElementById('error').textContent=errors.join(' ');document.getElementById('success').textContent=errors.length?'':'Registration successful!';
});
</script></body></html>
```

## Experiment 04
File: `Experiment_04_React_SPA.html`

```html
<!DOCTYPE html>
<html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>React Single Page Application</title><style>
body{font:16px Arial;margin:0;background:#f2f5fa;color:#1c2b42}nav{background:#1e3a65;padding:18px;text-align:center}
nav button{background:transparent;border:1px solid white;color:white;padding:9px 16px;margin:4px;border-radius:6px;cursor:pointer}
#root{max-width:800px;margin:35px auto;padding:25px;background:white;border-radius:12px;min-height:240px}
</style>
<script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script></head>
<body><nav id="nav"></nav><div id="root"></div>
<script type="text/babel">
const pages={Home:<><h1>Home</h1><p>Welcome to the React Single Page Application.</p></>,About:<><h1>About</h1><p>This page is rendered by React without reloading the browser.</p></>,Services:<><h1>Services</h1><ul><li>Web Development</li><li>UI Design</li><li>Application Support</li></ul></>,Contact:<><h1>Contact</h1><p>Email: contact@example.com</p></>};
function App(){const [page,setPage]=React.useState('Home');return <><div>{Object.keys(pages).map(p=><button onClick={()=>setPage(p)}>{p}</button>)}</div><main>{pages[page]}</main></>}
ReactDOM.createRoot(document.getElementById('root')).render(<App/>);
const navRoot=ReactDOM.createRoot(document.getElementById('nav'));
navRoot.render(<App/>);
</script></body></html>
```

## Experiment 05
File: `Experiment_05_Weather_Dashboard.html`

```html
<!DOCTYPE html>
<html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Weather Dashboard</title><style>
body{font:16px Arial;background:linear-gradient(135deg,#c8e5ff,#f1f6ff);min-height:100vh;margin:0;padding:35px;box-sizing:border-box}
.card{max-width:520px;margin:auto;background:white;padding:26px;border-radius:18px;box-shadow:0 8px 30px #3456}
form{display:flex;gap:8px}input{flex:1;padding:12px;border:1px solid #bbc8d7;border-radius:8px}button{background:#2461ad;color:white;border:0;border-radius:8px;padding:12px}
.weather{text-align:center;padding:25px}.temp{font-size:58px;font-weight:bold;color:#21528a}.muted{color:#61748a}
</style></head><body><div class="card"><h1>Weather Dashboard</h1><form id="search"><input id="city" placeholder="Enter city name" value="Chennai"><button>Search</button></form><div class="weather"><h2 id="place">Chennai</h2><div class="temp" id="temp">32°C</div><h3 id="condition">Partly Cloudy</h3><p class="muted" id="details">Humidity: 68% · Wind: 14 km/h</p></div><p class="muted">Demo weather data is used so the page works immediately without an API key.</p></div>
<script>
const data={chennai:[32,'Partly Cloudy',68,14],coimbatore:[29,'Sunny',54,10],mumbai:[30,'Cloudy',72,18],delhi:[27,'Clear',42,8],london:[14,'Light Rain',81,12],newyork:[19,'Cloudy',61,15]};
document.getElementById('search').addEventListener('submit',e=>{e.preventDefault();let city=document.getElementById('city').value.trim(),d=data[city.toLowerCase()];document.getElementById('place').textContent=city||'Unknown';if(d){document.getElementById('temp').textContent=d[0]+'°C';document.getElementById('condition').textContent=d[1];document.getElementById('details').textContent='Humidity: '+d[2]+'% · Wind: '+d[3]+' km/h';}else{document.getElementById('temp').textContent='--';document.getElementById('condition').textContent='No demo data for this city';document.getElementById('details').textContent='Try Chennai, Coimbatore, Mumbai, Delhi, London or New York.';}});
</script></body></html>
```

## Experiment 06
File: `Experiment_06_REST_API_Demo.html`

```html
<!DOCTYPE html>
<html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>REST API CRUD Demo</title><style>
body{font:16px Arial;background:#f1f4f9;padding:30px}.box{max-width:700px;margin:auto;background:white;padding:24px;border-radius:12px}
form{display:flex;gap:8px}input{flex:1;padding:11px;border:1px solid #bcc6d3;border-radius:6px}button{padding:10px 14px;background:#245bb1;color:white;border:0;border-radius:6px;cursor:pointer}
.item{padding:12px;border-bottom:1px solid #ddd;display:flex;justify-content:space-between;align-items:center}.del{background:#c33}
#log{background:#172235;color:#b9f6ca;padding:12px;border-radius:7px;min-height:50px;white-space:pre-wrap}
</style></head><body><div class="box"><h1>REST API – CRUD Demo</h1><p>Try creating, reading, updating and deleting records.</p>
<form id="form"><input id="name" placeholder="Enter product name" required><button>Add (POST)</button></form><h3>Products (GET)</h3><div id="items"></div><h3>API Activity</h3><div id="log">Ready.</div></div>
<script>
let records=[{id:1,name:'Laptop'},{id:2,name:'Keyboard'}],next=3;
function log(method,msg){document.getElementById('log').textContent=method+' /api/products\\n'+msg;}
function render(){let root=document.getElementById('items');root.innerHTML='';records.forEach(r=>{let row=document.createElement('div');row.className='item';let label=document.createElement('span');label.textContent=r.id+' - '+r.name;let edit=document.createElement('button');edit.textContent='Update (PUT)';edit.onclick=()=>{let n=prompt('New name',r.name);if(n){r.name=n;render();log('PUT','Updated product '+r.id);}};let del=document.createElement('button');del.textContent='Delete';del.className='del';del.onclick=()=>{records=records.filter(x=>x.id!==r.id);render();log('DELETE','Deleted product '+r.id);};row.append(label,edit,del);root.append(row);});}
document.getElementById('form').onsubmit=e=>{e.preventDefault();let name=document.getElementById('name').value;records.push({id:next++,name});e.target.reset();render();log('POST','Created product. Status: 201 Created');};
render();
</script></body></html>
```

## Experiment 07
File: `Experiment_07_Full_Stack_App_Demo.html`

```html
<!DOCTYPE html>
<html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Full Stack App Demo</title><style>
body{font:16px Arial;background:#eef2f7;padding:30px}.app{max-width:650px;margin:auto;background:white;padding:25px;border-radius:12px}
form{display:flex;gap:8px}input{flex:1;padding:11px;border:1px solid #bbc6d3;border-radius:6px}button{padding:11px 15px;background:#2259ac;color:white;border:0;border-radius:6px}
li{padding:10px;border-bottom:1px solid #ddd}.note{color:#64748b;font-size:14px}
</style></head><body><div class="app"><h1>Full Stack Product Manager</h1><p>React-style interface + API-style operations + local database storage.</p>
<form id="form"><input id="product" placeholder="Product name" required><button>Add Product</button></form><h3>Saved Products</h3><ul id="list"></ul><button id="clear" type="button">Clear All</button><p class="note" id="status">Data is stored in this browser using localStorage.</p></div>
<script>
const key='fullStackProductsDemo';let products=JSON.parse(localStorage.getItem(key)||'["Laptop","Mouse"]');
function save(){localStorage.setItem(key,JSON.stringify(products));render();}
function render(){document.getElementById('list').innerHTML='';products.forEach((p,i)=>{let li=document.createElement('li');li.textContent=p+' ';let b=document.createElement('button');b.textContent='Delete';b.onclick=()=>{products.splice(i,1);save();};li.append(b);document.getElementById('list').append(li);});}
document.getElementById('form').onsubmit=e=>{e.preventDefault();products.push(document.getElementById('product').value.trim());e.target.reset();save();document.getElementById('status').textContent='API operation simulated: product saved to localStorage.';};
document.getElementById('clear').onclick=()=>{products=[];save();};render();
</script></body></html>
```

## Experiment 08
File: `Experiment_08_JWT_Authentication_Demo.html`

```html
<!DOCTYPE html>
<html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Authentication Demo</title><style>
body{font:16px Arial;background:#eef2f8;padding:35px}.card{max-width:460px;margin:auto;background:white;padding:25px;border-radius:12px}
input{width:100%;box-sizing:border-box;padding:12px;margin:8px 0;border:1px solid #bdc7d4;border-radius:6px}
button{padding:11px 16px;background:#245bb1;color:white;border:0;border-radius:6px;cursor:pointer}
#dashboard{display:none;background:#e9f8ef;padding:15px;margin-top:15px;border-radius:8px}#message{color:#b22;white-space:pre-wrap}
</style></head><body><div class="card"><h1>JWT Login Demo</h1><p>Use username <b>student</b> and password <b>12345</b>.</p>
<form id="login"><input id="user" placeholder="Username" required><input id="pass" type="password" placeholder="Password" required><button>Login</button></form>
<p id="message"></p><div id="dashboard"><h2>Welcome!</h2><p>Login successful. Demo access token:</p><code id="token"></code><p><button id="logout">Logout</button></p></div></div>
<script>
const enc=s=>btoa(unescape(encodeURIComponent(s))).replace(/=/g,'').replace(/\\+/g,'-').replace(/\\//g,'_');
document.getElementById('login').onsubmit=e=>{e.preventDefault();let u=document.getElementById('user').value,p=document.getElementById('pass').value;if(u==='student'&&p==='12345'){let header=enc(JSON.stringify({alg:'none',typ:'JWT'})),payload=enc(JSON.stringify({sub:u,role:'student',demo:true})),token=header+'.'+payload+'.';document.getElementById('token').textContent=token;document.getElementById('dashboard').style.display='block';document.getElementById('message').textContent='';}else{document.getElementById('message').textContent='Invalid username or password.';document.getElementById('dashboard').style.display='none';}};
document.getElementById('logout').onclick=()=>{document.getElementById('dashboard').style.display='none';document.getElementById('login').reset();document.getElementById('message').textContent='Logged out successfully.';};
</script></body></html>
```

## Experiment 09
File: `Experiment_09_Deployment_Ready_Website.html`

```html
<!DOCTYPE html>
<html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Deployment Ready Website</title><style>
*{box-sizing:border-box}body{margin:0;font:16px Arial;color:#1c2c42;background:#f4f7fb}
header{background:#18345d;color:white;text-align:center;padding:55px 20px}header h1{font-size:2.4rem}
main{max-width:850px;margin:30px auto;padding:0 18px}.panel{background:white;padding:25px;margin:18px 0;border-radius:12px;box-shadow:0 3px 14px #0001}
button{background:#2460ad;color:white;padding:11px 16px;border:0;border-radius:7px;cursor:pointer}
footer{text-align:center;padding:25px;color:#667}
</style></head><body><header><h1>My Deployed Website</h1><p>A responsive website ready for static hosting</p></header>
<main><section class="panel"><h2>Welcome</h2><p>This is a simple responsive website that can be deployed using a static website hosting service.</p><button onclick="document.getElementById('msg').textContent='Your website is working successfully!'">Test Website</button><p id="msg"></p></section>
<section class="panel"><h2>Features</h2><ul><li>Responsive layout</li><li>Simple navigation and interaction</li><li>HTML, CSS and JavaScript in one file</li></ul></section></main>
<footer>Deployment demonstration · 2026</footer></body></html>
```

## Experiment 10
File: `Experiment_10_Lighthouse_Audit_Page.html`

```html
<!DOCTYPE html>
<html lang="en"><head><meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Lighthouse Audit Test Page</title><meta name="description" content="A simple accessible page for testing website performance with Lighthouse.">
<style>
*{box-sizing:border-box}body{margin:0;font:16px/1.6 Arial,sans-serif;color:#203047;background:#f4f7fb}
header{background:#18345d;color:white;padding:45px 20px;text-align:center}
main{max-width:850px;margin:30px auto;padding:0 18px}.card{background:white;padding:24px;border-radius:12px;margin:16px 0}
a{color:#1859a5}button{padding:12px 18px;border:0;border-radius:7px;background:#235bb0;color:white}
</style></head><body><header><h1>Website Audit Test Page</h1><p>Simple page for performance, accessibility and SEO testing</p></header>
<main><section class="card"><h2>About this page</h2><p>This page uses semantic HTML, a viewport meta tag, readable text and a responsive layout.</p><button onclick="document.getElementById('result').textContent='JavaScript interaction is working.'">Test Interaction</button><p id="result" aria-live="polite"></p></section>
<section class="card"><h2>Navigation</h2><p><a href="#content">Go to content</a></p></section><section class="card" id="content"><h2>Main Content</h2><p>Use Chrome DevTools → Lighthouse → Analyze page load to generate an audit report.</p></section></main></body></html>
```
