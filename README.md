# Hackathon
# Day-2
# Technical Documentation: Furniture E-Commerce Website

Overview
This document outlines the technical foundation of the furniture e-commerce website, including system architecture, workflows, API endpoints, and Sanity CMS schema design. The goal is to create a scalable, responsive, and user-friendly platform for browsing and purchasing furniture.


1️⃣. System Architecture

High-Level Design
The system architecture consists of the following components:

1️⃣. Frontend (Next.js):
  ◼ Responsible for displaying the user interface and handling user interactions.
  ◼ Pages include Home, Product Listing, Product Details, Cart, Checkout, and Order Confirmation.

2️⃣. Backend (Sanity CMS):
   ◼ Manages dynamic content such as product details, orders, and customer data.
   ◼ Provides APIs for fetching and storing data.

3️⃣. Third-Party APIs:
   ◼ Used for payment processing and shipment tracking.

Architecture Diagram
[Frontend (Next.js)]
        |
[Sanity CMS] ---------> [Product Data API]
        |
[Third-Party API] -----> [Payment Gateway & Shipment Tracking]

Workflow Example
1️⃣. User visits the site and views products.
2️⃣. Frontend fetches product data from Sanity CMS via the Product Data API.
3️⃣. User places an order -> Order details are sent to Sanity CMS.
4️⃣. Shipment tracking and payment processing are managed via third-party APIs.

2️⃣. Workflows
Key User Flows
1️⃣. Browsing Products:
   ◼ User selects a category -> Sanity CMS sends product data -> Data displayed on frontend.

2️⃣. Placing Orders:
   ◼ User adds items to cart -> Proceeds to checkout -> Order details sent to Sanity CMS.

3️⃣. Tracking Shipment:
   ◼ User checks order status -> Shipment details fetched from a third-party API.

3️⃣. API Endpoints

General Endpoints
| Endpoint            | Method     |Purpose                       |Response Example                                   |
|---------------------|------------|------------------------------|---------------------------------------------------|
|`/products`          | GET        | Fetch all product details    | `{ "id": 1, "name": "Table", "price": 200 }`      |
| `/orders`           | POST       | Create a new order           | `{ "orderId": 123, "status": "Success" }`         |
|`/shipment`          | GET        |Fetch order shipment status   | `{ "shipmentId": 456, "status": "In Transit" }`   |

Example Endpoint Details
1️⃣. Endpoint: `/products`
   ◼ Method:GET
   ◼ Description:Fetches all available products from Sanity CMS.
   ◼ Response Example:
          {
       "id": 1,
       "name": "Sofa",
       "price": 500,
       "stock": 10,
       "image": "sofa.jpg"
     }


2️⃣. Endpoint:`/orders`
   ◼ Method: POST
   ◼ Description: Creates a new order.
   ◼ Payload Example:
     {
       "customer": {
         "name": "John Doe",
         "email": "john@example.com"
       },
       "items": [
         { "productId": 1, "quantity": 2 }
       ],
       "paymentStatus": "Paid"
     }

4️⃣. Sanity CMS Schema
Product Schema

export default {
  name: 'product',
  type: 'document',
  fields: [
    { name: 'name', type: 'string', title: 'Product Name' },
    { name: 'price', type: 'number', title: 'Price' },
    { name: 'stock', type: 'number', title: 'Stock Level' },
    { name: 'image', type: 'image', title: 'Product Image' }
  ]
};


Order Schema

export default {
  name: 'order',
  type: 'document',
  fields: [
    { name: 'customerName', type: 'string', title: 'Customer Name' },
    { name: 'email', type: 'string', title: 'Customer Email' },
    { name: 'items', type: 'array', of: [{ type: 'reference', to: [{ type: 'product' }] }], title: 'Order Items' },
    { name: 'total', type: 'number', title: 'Total Amount' },
    { name: 'paymentStatus', type: 'string', title: 'Payment Status' }
  ]
};

5️⃣. Tools and Best Practices

1️⃣. Version Control:
   - Use GitHub to track code changes.
   - Commit changes regularly with clear messages.

2️⃣. Collaboration:
   - Use Slack or Google Meet for discussions.
   - Share drafts with teammates for feedback.

3️⃣. Documentation Standards:
   - Keep documents structured and simple.
   - Use diagrams to visualize workflows.


6️⃣. Next Steps

1️⃣. Finalize the Sanity schemas and integrate them with the frontend.
2️⃣. Set up API endpoints and test their functionality.
3️⃣. Begin frontend development, starting with the homepage and product listing pages.

This technical documentation serves as a roadmap for building a robust and scalable e-commerce platform. By following this plan, the implementation phase will align seamlessly with your business goals. 

