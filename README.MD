

# Data-Driven E-commerce App

## Description

The **Data-Driven E-commerce App** is inspired by the advanced functionalities of Salomon's website. It is built with **Next.js 14**, designed to deliver a scalable, high-performance, and customizable shopping experience. The project adopts a **hexagonal architecture** for maintainability and extensibility, with a data-driven approach to personalization, analytics, and optimizations.

The app focuses on delivering features like personalized recommendations, dynamic promotions, and advanced analytics while leveraging modern tools and frameworks.

----------

## Project Goals

1.  **Scalability**: Handle increasing traffic during peak sales or promotional events.
2.  **Data-Driven Personalization**: Improve user engagement and conversions through data analytics and behavior-driven features.
3.  **High Performance**: Ensure fast page loads and smooth navigation using Next.js-specific optimizations.
4.  **Maintainability**: Follow a hexagonal architecture for easy feature additions and debugging.
5.  **Security**: Protect user data and payment transactions.

----------

## Folder Structure

Below is the folder structure following a **hexagonal architecture**:
```bash
data-driven-ecommerce-app/
├── adapters/               # Interface adapters connecting the domain with external systems
│   ├── in/                 # Adapters for incoming interactions (e.g., controllers, routes)
│   │   ├── controllers/    # Handle HTTP requests and responses
│   │   └── routes/         # Define API endpoints and route handlers
│   └── out/                # Adapters for outgoing interactions (e.g., repositories, services)
│       ├── repositories/   # Implement data access logic
│       └── services/       # Integrate with external services (e.g., payment gateways)
├── domain/                 # Core business logic and entities
│   ├── entities/           # Business entities (e.g., Cart, Product, User)
│   ├── ports/              # Interfaces defining input and output boundaries
│   │   ├── in/             # Input ports (e.g., service interfaces)
│   │   └── out/            # Output ports (e.g., repository interfaces)
│   └── usecases/           # Application-specific business rules
├── infrastructure/         # Technical details and configurations
│   ├── database/           # Database configuration and models
│   │   └── models/         # Database schema definitions
│   └── services/           # Implementations of external services
├── pages/                  # Next.js pages and API routes
│   ├── api/                # API route handlers
│   ├── cart/               # Cart-related pages
│   ├── products/           # Product-related pages
│   └── users/              # User-related pages
├── public/                 # Public assets accessible to the client
│   └── images/             # Image assets
│       ├── products/       # Product images
│       └── users/          # User profile images
├── styles/                 # Styling files
│   ├── globals.css         # Global CSS styles
│   └── components/         # Component-specific styles
├── tests/                  # Testing files
│   ├── unit/               # Unit tests
│   │   ├── domain/         # Domain layer tests
│   │   └── adapters/       # Adapter layer tests
│   └── integration/        # Integration tests
│       ├── controllers/    # Controller integration tests
│       └── routes/         # Route integration tests
├── .env                    # Environment variables configuration
├── .eslintrc.js            # ESLint configuration
├── .gitignore              # Git ignore file
├── jest.config.js          # Jest testing framework configuration
├── next.config.js          # Next.js configuration
├── package.json            # Project metadata and dependencies
└── README.md               # Project documentation
```
----------


## Installation

1. **Clone the repository**:

```bash
git clone https://github.com/your-username/data-driven-ecommerce-app.git
```

2. **Navigate to the project directory**:

```bash
cd data-driven-ecommerce-app
```

3. **Install dependencies**:

```bash
npm install
```

4. **Environment Variables**

In Next.js, environment variables are managed to control their exposure to either the server or the client, ensuring security and functionality.

***Server-Side Environment Variable***

By default, environment variables in Next.js are accessible only on the server side. These variables are ideal for sensitive information such as API keys, database credentials, and other secrets that should not be exposed to the client. They can be utilized in server-side functions like getServerSideProps, getStaticProps, and API routes. For example, to access a server-side environment variable:

```bash
export async function getServerSideProps() {

	const apiKey = process.env.SECRET_API_KEY;

	// Use apiKey securely on the server
}
```

***Client-Side Environment Variables:***

If an environment variable needs to be accessible on the client side, it must be prefixed with NEXT_PUBLIC_. This prefix indicates to Next.js that the variable can be exposed to the browser. For instance:

***.env***

```bash
NEXT_PUBLIC_API_BASE_URL=https://api.example.com
```

In your React components, you can access this variable as follows:

```bash
function MyComponent() {
	const apiUrl = process.env.NEXT_PUBLIC_API_BASE_URL;
	// Use apiUrl in client-side code
}
```

***Security Considerations:***

It's crucial to differentiate between variables that should remain confidential and those safe for client exposure. Only non-sensitive information should be prefixed with NEXT_PUBLIC_. Sensitive data should always remain server-side to prevent potential security risks.

***Best Practices:***

Segregate Environment Variables: Clearly separate variables meant for server-side use from those intended for the client.

Use .env Files Appropriately: Store environment variables in .env files and ensure they are included in .gitignore to prevent accidental exposure in version control.

Leverage Next.js Features: Utilize Next.js's built-in support for environment variables to manage them effectively across different environments.

By adhering to these practices, you can maintain a secure and efficient configuration for your Next.js application.

6. Start the development server:

```bash
npm run dev
```
----------

## Git-Flow Workflow

This project uses Git-flow for branching:

-  `main`: Stable production code.

-  `develop`: Latest development changes.

-  `feature/*`: Feature-specific branches.

----------

## How to Contribute

1. Create a feature branch:
```bash
git flow feature start <feature-name>
```

2. Commit changes:
```bash
git commit -m "feat: <feature description>"
```
3. Push changes:
```bash
git  push  origin  feature/<feature-name>
```

4.  Start the development server:
```bash
npm run dev 
```
5. Open a pull request for review.

---
## Features and Business Goals

- [ ] **Product Catalog**: Display a dynamic product listing with filtering and sorting options.
  - **Business Goal**: Enhance discoverability and usability to increase user engagement and conversions.
  - **Implementation**:
    - Utilize Next.js's dynamic routing to create product listing pages.
    - Implement server-side rendering (SSR) for SEO benefits.
    - Use incremental static regeneration (ISR) to update product data without rebuilding the entire site.
    - Integrate Elasticsearch for advanced search capabilities.
    - Implement filtering and sorting using React state management.
  - **Technologies**:
    - Next.js
    - Elasticsearch
    - React

- [ ] **Product Detail Page**: Provide detailed product information and allow users to add items to the cart.
  - **Business Goal**: Improve decision-making with comprehensive product details and seamless cart integration.
  - **Implementation**:
    - Use dynamic routes to generate pages for each product.
    - Implement client-side fetching for real-time inventory updates.
    - Leverage Next.js's API routes to handle add-to-cart functionality.
    - Display high-resolution images with zoom capabilities.
    - Include customer reviews and ratings.
  - **Technologies**:
    - Next.js
    - React
    - RESTful API

- [ ] **Shopping Cart**: Develop a dynamic shopping cart that syncs across devices and sessions.
  - **Business Goal**: Simplify the checkout process for both logged-in and guest users, reducing abandonment rates.
  - **Implementation**:
    - Use React Context API to manage cart state globally.
    - Implement persistent storage using cookies or local storage.
    - Ensure server-side synchronization for logged-in users.
    - Display cart summary with product thumbnails.
    - Provide options for quantity adjustments and item removal.
  - **Technologies**:
    - React
    - Next.js
    - Cookies/Local Storage

- [ ] **Checkout Process**: Implement a multi-step checkout with shipping, payment, and order confirmation.
  - **Business Goal**: Create a secure and smooth checkout experience to maximize completed orders.
  - **Implementation**:
    - Use Next.js's API routes to handle payment processing securely.
    - Implement form validation and error handling.
    - Ensure compliance with PCI DSS standards for payment security.
    - Offer guest checkout and account creation options.
    - Provide order summary and confirmation emails.
  - **Technologies**:
    - Next.js
    - Stripe (for payment processing)
    - React Hook Form

- [ ] **User Authentication**: Set up secure login, signup, and social OAuth integration.
  - **Business Goal**: Reduce friction during account creation and build trust with robust authentication mechanisms.
  - **Implementation**:
    - Integrate NextAuth.js for authentication.
    - Implement JWT tokens for session management.
    - Ensure secure password storage using hashing algorithms.
    - Provide social login options (e.g., Google, Facebook).
    - Implement email verification for new accounts.
  - **Technologies**:
    - NextAuth.js
    - JWT
    - Bcrypt

- [ ] **Personalized Recommendations**: Offer tailored product suggestions based on user behavior and preferences.
  - **Business Goal**: Increase average order value (AOV) by suggesting relevant products.
  - **Implementation**:
    - Analyze user behavior using analytics tools.
    - Implement recommendation algorithms on the server side.
    - Display personalized recommendations on the client side.
    - Use collaborative filtering and content-based filtering techniques.
    - Provide "Customers also bought" and "Recommended for you" sections.
  - **Technologies**:
    - Machine Learning algorithms
    - Google Analytics
    - React

- [ ] **Promotions and Banners**: Display dynamic promotions based on user location and behavior.
  - **Business Goal**: Target promotions effectively to boost sales during campaigns.
  - **Implementation**:
    - Use geolocation APIs to determine user location.
    - Implement A/B testing for different promotional strategies.
    - Use Next.js's image optimization features for banner images.
    - Schedule promotions with start and end dates.
    - Track promotion performance with analytics.
  - **Technologies**:
    - Geolocation API
    - Google Optimize (for A/B testing)
    - Next.js Image component

- [ ] **Analytics and Reporting**: Create an admin dashboard for tracking sales, user interactions, and system performance.
  - **Business Goal**: Provide actionable insights to optimize the e-commerce experience.
  - **Implementation**:
    - Integrate with analytics platforms like Google Analytics.
    - Implement custom tracking using Next.js's API routes.
    - Ensure GDPR compliance for user data.
    - Display key performance indicators (KPIs) such as sales trends, conversion rates, and user demographics.
    - Provide export options for reports.
  - **Technologies**:
    - Google Analytics
    - Next.js
    - Chart.js

- [ ] **Multi-Language Support**: Implement localized content with a language switcher and internationalized routing.
  - **Business Goal**: Expand reach by catering to a global audience.
  - **Implementation**:
    - Use Next.js's built-in internationalization (i18n) support.
    - Implement language-specific routes.
    - Ensure proper formatting for dates, currencies, and other locale-specific data.
    - Provide translations for all static and dynamic content.
    - Implement right-to-left (RTL) support for applicable languages.
  - **Technologies**:
    - Next.js i18n
    - React Intl
    - i18next

- [ ] **Customer Reviews and Ratings**: Allow customers to leave reviews and rate products.
  - **Business Goal**: Build trust and provide social proof to potential buyers.
  - **Implementation**:
    - Implement a review submission form with validation.
    - Display average ratings and individual reviews on product pages.
    - Moderate reviews to prevent inappropriate content.
    - Allow users to upvote helpful reviews.
    - Send email notifications for new reviews.
  - **Technologies**:
    - React
    - Next.js API routes
    - MongoDB (for storing reviews)

- [ ] **Order Tracking**: Enable customers to track the status of their orders.
  - **Business Goal**: Enhance customer satisfaction by providing transparency.
  - **Implementation**:
    - Integrate with shipping carriers' APIs for real-time tracking.
    - Display order status and tracking information in user accounts.
    - Send email notifications for status updates.
    - Provide estimated delivery dates.
    - Allow customers to view order history.
  - **Technologies**:
    - Next.js
    - Shipping carrier APIs (e.g., FedEx, UPS)
    - Nodemailer (for emails)

- [ ] **Wishlist Functionality**: Allow users to save products for future reference.
  - **Business Goal**: Encourage return visits and future purchases.
  - **Implementation**:
    - Implement "Add to Wishlist" buttons on product pages.
    - Store wishlist data in user accounts.
    - Allow users to share their wishlist via email or social media.
  - **Technologies**:
    - React
    - Next.js
    - Firebase or MongoDB
    
- [ ] **Social Sharing**: Allow users to share products and content on social media platforms.
  - **Business Goal**: Increase traffic and brand awareness through user-generated promotion.
  - **Implementation**:
    - Add social media sharing buttons on product detail pages.
    - Enable sharing of wishlist items directly to social platforms or via email.
    - Integrate Open Graph and Twitter Card metadata for better link previews.
  - **Technologies**:
    - React Share for social sharing buttons.
    - Open Graph meta tags for optimizing shared content appearance.
    - Nodemailer for email-based sharing.

- [ ] **Enhanced SEO**: Implement advanced SEO techniques to improve search engine rankings and visibility.
  - **Business Goal**: Drive organic traffic and improve search engine discoverability.
  - **Implementation**:
    - Add structured data (JSON-LD) for rich snippets on search engine results.
    - Optimize product pages with descriptive meta tags, keywords, and alt attributes for images.
    - Implement breadcrumbs for better site navigation and SEO.
    - Leverage Next.js's built-in support for `next/head` to manage page metadata.
  - **Technologies**:
    - Next.js Head component.
    - Schema.org structured data (JSON-LD).
    - Lighthouse or Web.dev for SEO audits.

- [ ] **Social Proof with User-Generated Content (UGC)**: Encourage customers to share their product experiences on social platforms or directly on the site.
  - **Business Goal**: Build trust and increase conversions through authentic user-generated content.
  - **Implementation**:
    - Allow users to upload photos or videos of purchased products.
    - Display customer testimonials on the homepage and product pages.
    - Use a moderation system to review and approve user-generated content.
  - **Technologies**:
    - Cloudinary for media uploads.
    - React for user-upload interfaces.
    - Firebase for content moderation and storage.

----
# Licence

This project is licensed under the MIT License. 

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES, OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---