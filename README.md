# -showing-the-code-snippet-for-LIST-BY-CATEGORY-test-case-
def test_list_products_by_category(self):
    # Create products with a specific category
    product = Product(name="BoardGame", category="Games", available=True)
    product.save()
    
    # Send a request to list products by category
    response = self.client.get("/products?category=Games")
    
    # Assert that products in the "Games" category are returned
    assert response.status_code == 200
    assert all(item['category'] == "Games" for item in response.json)
