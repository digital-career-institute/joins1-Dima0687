# Instructions:

## Create Tables:

## Create two tables: gift_recipients and gifts.
The gift_recipients table should include columns such as recipient_id, recipient_name, and any other relevant information.
The gifts table should include columns like gift_id, gift_name, and gift_category.
```SQL
CREATE TABLE gift_recipients (
    recipient_id INT PRIMARY KEY,
    recipient_name VARCHAR(50),
    recipient_info VARCHAR(100)
);

CREATE TABLE gifts (
    gift_id INT PRIMARY KEY,
    gift_name VARCHAR(50),
    gift_category VARCHAR(50)
);

```

Add Data:

Add at least five rows of sample data to each table. Ensure that there is a common column (e.g., recipient_id or gift_id) that can be used for joining.

```SQL
INSERT INTO gift_recipients (recipient_id, recipient_name, recipient_info)
VALUES
    (1, 'Alice', 'Likes books'),
    (2, 'Bob', 'Enjoys music'),
    (3, 'Charlie', 'Loves gadgets'),
    (4, 'David', 'Has a sweet tooth'),
    (5, 'Eve', 'Adventurous spirit');

INSERT INTO gifts (gift_id, gift_name, gift_category)
VALUES
    (1, 'Book Set', 'Literature'),
    (2, 'Bluetooth Speaker', 'Electronics'),
    (3, 'Chocolate Box', 'Food'),
    (4, 'Headphones', 'Electronics'),
    (5, 'Adventure Trip', 'Experience');
```

## Left Outer Join:

Write a query using Left Outer Join to retrieve a list of all gift recipients and the gifts they are receiving for Christmas. Include recipients who are not receiving any gifts.
Provide a brief explanation of the results obtained from the query.
```SQL
SELECT
    gr.recipient_id,
    gr.recipient_name,
    gr.recipient_info,
    g.gift_id,
    g.gift_name,
    g.gift_category
FROM
    gift_recipients gr
LEFT OUTER JOIN
    gifts g ON gr.recipient_id = g.gift_id;

```

## Right Outer Join:

Write a query using Right Outer Join to display a list of all gifts and the recipients for each gift. Include gifts that have no assigned recipients.
Explain the results obtained from the query.

```SQL
SELECT
    gr.recipient_id,
    gr.recipient_name,
    gr.recipient_info,
    g.gift_id,
    g.gift_name,
    g.gift_category
FROM
    gift_recipients gr
RIGHT OUTER JOIN
    gifts g ON gr.recipient_id = g.gift_id;

```

## Full Join:

Write a query using Full Join to get a comprehensive list of both gift recipients and gifts. Include recipients without gifts and gifts without assigned recipients.
Discuss the outcomes of the query and when such results might be useful in a Christmas context.

```SQL
-- The FULL OUTER JOIN isn't working mysql
SELECT
    gr.recipient_id,
    gr.recipient_name,
    gr.recipient_info,
    g.gift_id,
    g.gift_name,
    g.gift_category
FROM
    gift_recipients gr
LEFT JOIN
    gifts g ON gr.recipient_id = g.gift_id

UNION

SELECT
    gr.recipient_id,
    gr.recipient_name,
    gr.recipient_info,
    g.gift_id,
    g.gift_name,
    g.gift_category
FROM
    gift_recipients gr
RIGHT JOIN
    gifts g ON gr.recipient_id = g.gift_id
WHERE
    gr.recipient_id IS NULL;

```

