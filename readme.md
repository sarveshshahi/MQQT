<div align="center">
  <img src="https://frappe.io/files/frappe-framework.png" height="100" alt="Frappe Logo" />
  <h1>Expo Item API for Frappe</h1>
  <p><em>REST API for fetching Website Items with stock, price, discounts, and slideshow images</em></p>

  <p>
    <img alt="Last Commit" src="https://img.shields.io/github/last-commit/your-username/your-repo-name" />
    <img alt="Repo Size" src="https://img.shields.io/github/repo-size/your-username/your-repo-name" />
    <img alt="License" src="https://img.shields.io/github/license/your-username/your-repo-name" />
    <img alt="Frappe Version" src="https://img.shields.io/badge/Frappe-14%2B-blue?logo=frappe" />
  </p>
</div>

---

## 🧩 Features

- ✅ Fetch Website Items (published only)
- 💰 Integrates with Item Price to return price
- 📦 Shows current stock from Bin
- 🎯 Adds discounts using a custom method
- 🖼️ Retrieves slideshow images tied to each item

---

## 📸 Screenshot

<p align="center">
  <img src="https://yourdomain.com/path-to-screenshot.png" width="700" alt="API Screenshot">
</p>

---

## 🚀 API Endpoints

### 🔹 `GET /api/method/get_items_for_expo_idd?name=ITEM-0001`

Fetches one specific Website Item and returns:

```json
{
  "status": "success",
  "message": "Item(s) fetched successfully",
  "items": [
    {
      "item_code": "ITEM-0001",
      "item_name": "Product Name",
      "price": 100.0,
      "stock": 25,
      "discount": 10,
      "slideshow_images": [
        "https://yourdomain.com/files/image1.png",
        "https://yourdomain.com/files/image2.png"
      ]
    }
  ]
}
