---
layout: post
title: "Choosing the Right Data Type for Postal Codes and Other Keys"
date:   2024-01-27 05:58:54 +0000
categories: "News"
excerpt_image: https://www.fmsinc.com/MicrosoftAccess/zip-code/zip-code-city-state-list.jpg
image: https://www.fmsinc.com/MicrosoftAccess/zip-code/zip-code-city-state-list.jpg
---

Postal codes and other identifying codes like phone numbers play an important role in organizing customer and transactional data. However, choosing the right database structure to store these values requires some consideration. 
Codes like postal codes have specific formatting rules that need to be respected. **In the United States**, postal codes known as ZIP codes begin with numbers but can also include leading zeros and dashes with optional plus-four extensions. Storing them as text values in a database preserves these formatting rules and ensures any trailing characters are not truncated. 
In contrast, postal codes in other countries like the **United Kingdom** have completely alphanumeric codes without standard formats. Since UK postcodes like "ED1 3NT" cannot be represented as numbers, these must be stored as text as well to avoid data loss.
When including postal codes or other codes in **relational database tables**, it's common to use them as foreign keys that link to a reference table holding valid code values. However, relational databases typically require foreign key fields to be numeric data types. 
To solve this, the code values themselves can be stored as text in the reference table while being referenced via an auto-incrementing numeric ID field. Any table columns referencing codes as foreign keys would use this ID instead of the text value. This allows codes to be queried and validated while still preserving their original text formatting.
Proper data types are also important when performing operations on code values. Values like room numbers are rarely used in mathematical calculations, so storing them as text is preferable since it allows **case-insensitive string comparisons and extraction of substrings**. 
On the other hand, values representing counts, timestamps or other measurable units generally require numeric data types to support addition, subtraction and other operations. Taking the intended uses and operations into consideration helps determine the optimal way to structure code attributes in a database for both integrity and application requirements.
### Referencing Codes While Maintaining Integrity
To tie codes like postal or phone numbers to related database records while preserving their original structure and avoiding data loss, developers can implement an abstracted reference table architecture. 
This involves creating a separate code reference table to hold the full code values as text alongside an auto-incrementing numeric ID field. Any other tables would contain foreign key relationships to this ID field rather than storing the text codes directly. 
For example, a postal code reference table could have fields like:
- ID (primary key, integer)  
- Code (text - stores full postal code)
A customer table would reference this via: 
- PostalCodeID (foreign key to postal code table ID)
This allows codes stored as text in the reference table to still participate in relational integrity constraints via their unique numeric IDs. It's also optimal for performance since integers have faster indexing and comparison than longer text values.
Any interfaces presenting code attributes to users can look up and display the associated text value from the reference table as needed, while queries, reports and relationships internally utilize the cleaner integer IDs. This balanced approach maintains both data integrity and original code structures.

![](https://support.content.office.net/en-us/media/bf465e40-ab9d-4a1c-be7e-d122fd50bf9a.jpg)
### Comparing and Processing Code Attributes
Once a database has been setup to store codes and identifiers with consideration for preservation of formatting, the next step is enabling common operations on those attributes. 
Text-based codes require different processing than numeric types. For example, to find customer records by a partial postal code substring, a query against a text-based "Code" column could use a LIKE operator and wildcard match. 
Numeric foreign key values don't support substrings so that query wouldn't be possible. Text is also preferable for case-insensitive comparison, like finding customers regardless of uppercase or lowercase values. 
Meanwhile, certain code segments like internal numeric portions may need to be extracted, cast to integers and compared mathematically. For example, finding all customers on the third floor of a building from their room numbers. 
Luckily, most databases support functions to parse out substrings, convert between data types and perform mixed operations. By choosing data types that match intended uses, applications gain the maximum flexibility in working with codes and identifiers through queries, validation and processing logic.
### Data Quality and Integrity with Referential Constraints
One key benefit of the reference table approach for codes is the ability to enforce data integrity at the database level through constraints. Declarative constraints ensure that only valid code values can exist across related tables.
For example, a foreign key constraint between an order table and postal code reference table prevents orders from being placed with non-existent codes. If a postal code is later deleted from the reference table due to an error or update, orders containing it will be prevented from being placed. 
A check constraint could verify codes match expected patterns, like the format of a UK postcode. And a unique constraint on the reference table avoids duplicate or inconsistent definitions of the same code. 
These integrity rules help maintain clean, consistent data across multiple code attributes without extra application logic. And reference tables allow new codes to be easily added without changes to related schema structures. Overall referential constraints are a key technique for ensuring codes are represented authoritatively in relational data.
 ![Choosing the Right Data Type for Postal Codes and Other Keys](https://www.fmsinc.com/MicrosoftAccess/zip-code/zip-code-city-state-list.jpg)