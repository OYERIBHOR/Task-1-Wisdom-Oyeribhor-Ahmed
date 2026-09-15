# Task-1-Wisdom-Oyeribhor-Ahmed

# SQL Data Analysis Project — Data Cleaning Notes

## Overview
This repository contains an Orders dataset (`dataset-clean.xlsx`) used for a SQL data analysis project. The dataset contains 1,200 order records with 14 fields, including order details, customer information, shipping data, and coupon usage.

## Dataset Structure

| Column | Description |
|---|---|
| OrderID | Unique identifier for each order |
| Date | Order date |
| CustomerID | Unique identifier for each customer |
| Product | Product purchased |
| Quantity | Number of units ordered |
| UnitPrice | Price per unit |
| ShippingAddress | Delivery address |
| PaymentMethod | Method used to pay (Credit Card, Debit Card, Online) |
| OrderStatus | Current status of the order (Shipped, Delivered, Cancelled, Returned) |
| TrackingNumber | Shipment tracking ID |
| ItemsInCart | Number of items in the cart at checkout |
| CouponCode | Coupon code applied to the order (if any) |
| ReferralSource | Channel that referred the customer (Instagram, Facebook, Email, Referral) |
| TotalPrice | Final order total |

## Data Cleaning: `CouponCode` Column

**Issues found:**
- Orders with no coupon applied were recorded inconsistently (as `N/A` / `Null`) instead of a single standard value.
- Coupon codes were inconsistently cased (e.g. `Freeship`, `Winter15`, `Save10`) instead of a uniform format.

**Fixes applied:**
- All "no coupon" entries were standardized to the single label `None`.
- All coupon codes were standardized to uppercase (`FREESHIP`, `WINTER15`, `SAVE10`), matching how they're used elsewhere in the workflow.

**Result after cleaning:**

| CouponCode | Count |
|---|---|
| FREESHIP | 313 |
| SAVE10 | 286 |
| WINTER15 | 292 |
| None (no coupon used) | 309 |

**Why this matters:** Standardizing the "no coupon" label avoids treating `N/A` as a missing/null value in downstream SQL queries and aggregations (e.g. `GROUP BY CouponCode`, `COUNT`, `JOIN` conditions), and ensures coupon-usage analysis reflects consistent categories rather than a mix of nulls and text.

## Files
- `dataset-clean.xlsx` — cleaned dataset, ready for SQL import/analysis

## Author
Wisdom Ahmed Oyeribhor
