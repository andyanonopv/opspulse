# OpsPulse

> A lightweight incident-management platform for engineering and operations teams.

<p align="center">
  <a href="https://laravel.com" target="_blank">
    <img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="300" alt="Powered by Laravel">
  </a>
</p>

## 📌 Table of Contents
- [About OpsPulse](#about-opspulse)
- [Core Features & Technical Scope](#core-features--technical-scope)
- [Tech Stack](#tech-stack)
- [Installation & Local Setup](#installation--local-setup)
- [Usage & API Ingestion](#usage--api-ingestion)
- [Running Tests](#running-tests)
- [Built With Laravel](#built-with-laravel)
- [License](#license)

---

## 🚀 About OpsPulse

**OpsPulse** is designed for companies operating multiple web services. When an outage or degradation occurs, engineers can rapidly create an incident, assign ownership to a responder, track its lifecycle status, and document the final root-cause resolution.

Beyond manual incident tracking, OpsPulse exposes a REST API to ingest simulated alerts directly from external monitoring systems.

## ✨ Core Features & Technical Scope

OpsPulse goes beyond simple CRUD operations by implementing production-grade engineering patterns:

**Planned Features ->**

* **Incident Lifecycle Management:** Create, triage, assign, update status (`Open`, `Investigating`, `Resolved`), and log resolution post-mortems across multiple services.
* **External Alert Ingestion (REST API):** Secure endpoints to accept and process simulated webhook alerts from external monitoring tools.
* **Authentication & Authorization:** Role-based access control and API token authentication (Laravel Sanctum) ensuring only authorized engineers can modify or resolve incidents.
* **Relational Database Design:** Normalized schemas linking services, incidents, status updates, and engineering responders.
* **Asynchronous Background Jobs:** Queue-driven processing for incoming alert payloads, notifications, and heavy background tasks.
* **Concurrency Handling:** Safe state transitions and database locking to prevent race conditions when multiple engineers or automated webhooks update an incident simultaneously.
* **Interactive UI:** Responsive, real-time-feeling frontend interactions built with JavaScript and Tailwind CSS v4.
* **Security & Automated Testing:** Input validation, rate limiting, CSRF/XSS protection, and comprehensive feature/unit test coverage.

## 🧰 Tech Stack

* **Backend:** PHP 8.3+, Laravel
* **Frontend & Styling:** Tailwind CSS v4 (`@tailwindcss/vite`), Vanilla JS / Alpine / Livewire
* **Build Tooling:** Vite 8 (`laravel-vite-plugin`), Concurrently
* **Database & Queues:** MySQL / PostgreSQL / SQLite, Laravel Queues

## ⚙️ Installation & Local Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/andyanonopv/opspulse
   cd opspulse
   ```

2. **Install PHP and Node dependencies:**
   ```bash
   composer install
   npm install
   ```

3. **Configure your environment:**
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```
   *(Update your database and queue connection settings inside `.env` as needed.)*

4. **Run database migrations (and seeders, if available):**
   ```bash
   php artisan migrate --seed
   ```

5. **Start the development servers:**
   Run the Laravel server, queue worker, and Vite asset bundler:
   ```bash
   # Terminal 1: Laravel server
   php artisan serve

   # Terminal 2: Vite frontend bundler
   npm run dev

   # Terminal 3: Background queue worker
   php artisan queue:work
   ```
   *(Or use `composer run dev` if configured with `concurrently`.)*

## 📡 Usage & API Ingestion

### Simulating an External Monitoring Alert
External monitoring systems can trigger or update incidents via the REST API:

<!-- ```bash
curl -X POST http://127.0.0 \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "service": "payment-gateway",
    "severity": "critical",
    "title": "High 5xx Error Rate Detected",
    "payload": {
      "error_rate": "14.2%",
      "region": "eu-central-1"
    }
  }'
``` -->

To be configured

## 🧪 Running Tests

Execute the automated test suite via Artisan:

```bash
php artisan test
```

## 🛠️ Built With Laravel

OpsPulse is built on the [Laravel](https://laravel.com) web application framework, taking advantage of its expressive syntax and built-in ecosystem:

- [Simple, fast routing engine](https://laravel.com/docs/routing) & [API Authentication](https://laravel.com).
- Expressive, intuitive [Eloquent ORM](https://laravel.com/docs/eloquent) & [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues) & [concurrency utilities](https://laravel.com).
- Comprehensive [HTTP & database testing tools](https://laravel.com).

For developers new to the framework, explore the [Laravel Documentation](https://laravel.com/docs), [Laracasts](https://laracasts.com), or [Laravel Learn](https://laravel.com/learn).

## 📄 License

OpsPulse is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
