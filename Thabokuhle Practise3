--Q1 Find records wher size is missing and the purchase_amout is greater than 50.
--Expected columns; Customerid, Size, Purchase_amount, Item_purchase.
---------------------------------------------
SELECT CUSTOMER_ID, SIZE, PURCHASE_AMOUNT, ITEM_PURCHASED
FROM practise3.dataset3.shoping
WHERE SIZE IS NULL
AND PURCHASE_AMOUNT > 50;
---------------------------------------------
--Q2 List total number of purchases grouped by season, treating Null value as Unknwn season.
--Expected columns: Season, Total_purchases.
--------------------------------------------
SELECT COALESCE(SEASON, 'UNKNOWN SEASON') AS SEASON,
COUNT(*) AS TOTAL_PURCHASES
FROM PRACTISE3.DATASET3.SHOPING
GROUP BY COALESCE(SEASON, 'UNKNOWN SEASON');
--------------------------------------------
--Q3 Count how many customers used each Payment method, treading NULLs as not provided.
--Expected columns; Payment_method, Customer_count
--------------------------------------------
SELECT PAYMENT_METHOD, COUNT(DISTINCT CUSTOMER_ID) AS CUSTOMER_COUNT
FROM (SELECT COALESCE(PAYMENT_METHOD, 'NOT PROVIDED') AS PAYMENT_METHOD, CUSTOMER_ID
FROM PRACTISE3.DATASET3.SHOPING) AS T GROUP BY PAYMENT_METHOD;
--------------------------------------------
--Q4 Show customer where promo code udes is NULL and reviewing rating is belown3.0.
--Expected columns; customer_Id, promo_code, rewing_rating, item_purchsed
--------------------------------------------
SELECT
CUSTOMER_ID, PROMO_CODE_USED, REVIEW_RATING, ITEM_PURCHASED
FROM PRACTISE3.DATASET3.SHOPING
WHERE PROMO_CODE_USED IS NULL AND REVIEW_RATING< 3.0;
--------------------------------------------
--Q5 Group customers by shipping type, and count how many customers chose each option.
--Expected output Shipping_type, Cestomer_count.
--------------------------------------------
SELECT SHIPPING_TYPE, COUNT (DISTINCT CUSTOMER_ID) AS CUSTOMER_COUNT FROM PRACTISE3.DATASET3.SHOPING
GROUP BY SHIPPING_TYPE;
--------------------------------------------
--Q6 Display the number of purchases per location,but only for those with more than 5 purchases and no NULL Payment_method.
--------------------------------------------
SELECT LOCATION, COUNT (*) AS TOTAL_PURCHASES
FROM PRACTISE3.DATASET3.SHOPING
WHERE PAYMENT_METHOD IS NOT NULL
GROUP BY LOCATION
HAVING COUNT (*) > 5;
--------------------------------------------
--Q7 Create a column spender_category, that classified customer using.
--'high' if purchased amount > 80
--'medium' if purchase amount BETWEEN 50 AND 80
--Low atherwise
--Also replace NULL value in purchase_amount with 0
--Expected output customer_id, purchased_Amount, Spender_category
--------------------------------------------
SELECT CUSTOMER_ID, COALESCE(PURCHASE_AMOUNT, 0) AS PURCHASE_AMOUNT, CASE WHEN COALESCE( PURCHASE_AMOUNT, 0) BETWEEN 50 AND 80 THEN 'MEDIUM' ELSE 'LOW'
END AS SPENDER_CATEGORY
FROM PRACTISE3.DATASET3.SHOPING;
--------------------------------------------
--Q8 Find customers who have no previouse purchase(ie previouse purchase is null but the color is no null)
--Expected output: customerId, color, previouse_parchases
--------------------------------------------
SELECT CUSTOMER_ID, COLOR, PREVIOUS_PURCHASES
FROM PRACTISE3.DATASET3.SHOPING
WHERE PREVIOUS_PURCHASES IS NULL AND COLOR IS NOT NULL;
--------------------------------------------
--Q9 Group records by Frequency_of_purhases and sho the total amount spent per group,treating Null frequenceies as unknown
--Expected columns: Frequency_of_purchases, Total_Purchase_Amount
--------------------------------------------
SELECT COALESCE(FREQUENCY_OF_PURCHASES, 'UNKNOWN') AS FREQUENCY_OF_PURCHASES, SUM(PURCHASE_AMOUNT) AS TOTAL_PARCHASE_AMOUNT
FROM PRACTISE3.DATASET3.SHOPING
GROUP BY COALESCE(FREQUENCY_OF_PURCHASES, 'UNKNOWN');
--------------------------------------------
--Q10 Disp;ay a list of all Category values with the number of times each purcha
--sed,exclunding rows where category is NULL.
--expected column: category and total purchase.
-------------------------------------------
SELECT CATEGORY, COUNT(*) AS TOTAL_PARCHASES
FROM PRACTISE3.DATASET3.SHOPING WHERE CATEGORY IS NULL
GROUP BY CATEGORY;
--------------------------------------------
--Q11 Locations with the highest total_purchase_amount, replacing NULL in amount
--with 0. Expected columns Location, total purchase_amount
--------------------------------------------
SELECT LOCATION, SUM(COALESCE(PURCHASE_AMOUNT, 0)) AS TOTAL_PURCHASE_AMOUNT
FROM PRACTISE3.DATASET3.SHOPING
GROUP BY LOCATION ORDER BY TOTAL_PURCHASE_AMOUNT DESC LIMIT 5;
--------------------------------------------
--Q12 Group customers by gender and size, and count how many entries have null.
--L color. Expected column: gender, size,NULL color count
--------------------------------------------
SELECT GENDER, SIZE, COUNT(*) AS NULL_COLOR_COUNT
FROM PRACTISE3.DATASET3.SHOPING
WHERE COLOR IS NULL GROUP BY GENDER, SIZE;
--------------------------------------------
--Q13 identify all item purchased wheren more than 3 purchases had anull shipping
---type--
--Expected column item purchased, NULL shipping, type count.
--------------------------------------------
SELECT ITEM_PURCHASED,
COUNT(*) AS NULL_SHIPPING_TYPE_COUNT
FROM PRACTISE3.DATASET3.SHOPING
WHERE SHIPPING_TYPE IS NULL
GROUP BY ITEM_PURCHASED 
HAVING COUNT(*) >3;
-------------------------------------------
--Q14 Show a count of many customers per Payment Methond have NULL review.
--Expected columns: Payment Method, Missing_Review_Count.
-------------------------------------------
SELECT PAYMENT_METHOD, COUNT(*) AS MISSING_REVEIW_RATING_COUNT
FROM PRACTISE3.DATASET3.SHOPING
WHERE REVIEW_RATING IS NULL 
GROUP BY PAYMENT_METHOD;
-------------------------------------------
--Q15 Group by category return the avarage review rating, replacing NULLs with 0, and filter only where avarage is greater than 3.5.
--expected columns: category, Average_review_rating.
-------------------------------------------
SELECT CATEGORY, AVG(COALESCE(REVIEW_RATING, 0)) AS AVERAGE_REVIEW_RATING
FROM PRACTISE3.DATASET3.SHOPING
GROUP BY CATEGORY
HAVING AVG(COALESCE(REVIEW_RATING, 0)) > 3.5;
-------------------------------------------
--Q16 list all colors that are missing(NULL) in at least two rows and the avarage age of customers for those raws.
--Expected columns: color, Avarage Age.
-------------------------------------------
SELECT COLOR, AVG(AGE) AS AVARAGE_AGE
FROM PRACTISE3.DATASET3.SHOPING
WHERE COLOR IS NULL GROUP BY COLOR
HAVING COUNT(*) >= 2;
-------------------------------------------
--Q17 Use CASE to create a column delivery speed: "Fast" if shipping type is "Express" or 'Next Day Air', 'Slow' if 'Standard',
--'Other' for all else including Null then count how many customers fall into each category.
--Expected column:Delivery speed, customer count.
-------------------------------------------
SELECT DELIVERY_SPEED, COUNT(DISTINCT CUSTOMER_ID) AS CUSTOMER_COUNT
FROM (SELECT CUSTOMER_ID, CASE WHEN SHIPPING_TYPE IN ('EXPRESS', 'NEXT DAY AIR') THEN 'FAST' WHEN SHIPPING_TYPE = 'STANDARD' THEN 'SLOW'
ELSE 'OTHER' END AS DELIVERY_SPEED FROM PRACTISE3.DATASET3.SHOPING) AS T GROUP BY DELIVERY_SPEED;
-------------------------------------------
--Q19 Group by Location and show the maximum previous purchase, replace NULLs with o, onlybb where the avarage rating is above 4.0
--Expected colunm location, Max_Previous_Purchase, Avarage, Reviewing rating.
-------------------------------------------
SELECT LOCATION, MAX(COALESCE(PREVIOUS_PURCHASES, 0)) AS MAX_PREVIOUS_PURCHASES, AVG(REVIEW_RATING) AS AVARAGE_REVIEW_RATING
FROM PRACTISE3.DATASET3.SHOPING
GROUP BY LOCATION
HAVING AVG(REVIEW_RATING) > 4.0;
-------------------------------------------
--Q20 Show customers who have NULL shipping type but made a purchase in the range of 30 to 70 USD.
--Expected column: CustomerId, shippingType, PurchaseAmount, itemPurchase.
-------------------------------------------
SELECTSHIPPING_TYPE,
PURCHASE_AMOUNT,
ITEM_PURCHASED
FROM PRACTISE3.DATASET3.SHOPING
WHERE SHIPPING_TYPE IS NULL 
AND PURCHASE_AMOUNT BETWEEN 30 AND 70; CUSTOMER_ID,
