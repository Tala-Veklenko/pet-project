# Test Scenario
## GET /items/ API
### ✅ Positive Test Scenarios
```TS_01: Verify that the API returns a list of items successfully```

#### Preconditions: API is available.
* Steps:
1. Send a GET request to /items/ without any parameters.
2. Verify the response status code.
3. Check that the response body contains count, next, previous, and results fields.
4. Ensure that the results array contains item objects with valid fields.
5. Expected Result: The API returns 200 OK with a paginated list of items.

```TS_02: Verify that pagination works correctly```
#### Preconditions: The database contains more than one page of items.
* Steps:
1. Send a GET request to /items/?page=2.
2. Verify that the previous field points to page 1.
3. Check that the next field is correctly set (if more pages exist).
4. Expected Result: The API correctly paginates results and provides valid next and previous links.

```TS_03: Verify that items contain valid data```
#### Preconditions: Items exist in the database.
* Steps:
1. Send a GET request to /items/.
2. Verify that each item in results contains valid id, title, description, price, image, created_at, and category_id fields.
3. Ensure price is non-negative, created_at is in proper date format, and image is a valid URL.
4. Expected Result: All fields are correctly formatted and contain valid data.

```TS_04: Verify response when requesting the last page```
#### Preconditions: The database contains multiple pages.
* Steps:
1. Find the total number of items from the count field.
2. Calculate the last page number.
3. Send a GET request to /items/?page=last_page_number.
4. Verify that the next field is null and previous points to the previous page.
5. Expected Result: The last page is correctly handled, showing no next page.

### ❌ Negative Test Scenarios
```TS_05: Verify response when requesting a non-existing page```
#### Preconditions: API must have limited pages.
* Steps:
1. Send a GET request to /items/?page=9999.
2. Verify the response status code.
3. Expected Result: API returns 404 Not Found or empty results.

```TS_06: Verify API behavior when no items exist```
#### Preconditions: The database is empty.
* Steps:
Send a GET request to /items/.
Verify that count is 0 and results is an empty array.
Expected Result: API returns 200 OK with count: 0 and an empty results array.

```TS_07: Verify API response without authentication (if required)```
#### Preconditions: API requires authentication.
* Steps:
Send a GET request to /items/ without an authentication token.
Verify the response.
Expected Result: API returns 401 Unauthorized with an appropriate error message.

```TS_08: Verify API behavior when an invalid page parameter is provided```
#### Preconditions: None.
* Steps:
Send a GET request to /items/?page=abc (invalid string input).
Verify the response.
Expected Result: API returns 400 Bad Request with an error message.

```TS_09: Verify API behavior with unexpected query parameters```
#### Preconditions: None.
* Steps:
Send a GET request to /items/?invalid_param=123.
Verify the response.
Expected Result: API ignores the invalid parameter and returns a valid response or returns a 400 Bad Request error.


## POST /items/ API
### ✅ Positive Test Scenarios
```Scenario: A user successfully creates an item with valid data.```
* Steps:
1. Send a POST request with valid title, description, price, image, and category_id.
2. API processes the request.
3. API returns a 201 Created response with the newly created item.
4. Expected Result: The item is created successfully.
### ❌ Negative Scenario Example
```Scenario: A user tries to create an item without providing a title.```
* Steps:
1.Send a POST request without a title field.
2. API detects the missing field.
3. API returns a 400 Bad Request error with "Title is required".
4. Expected Result: The request is rejected.

