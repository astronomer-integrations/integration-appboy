![alt text](img/logo.jpg "Analytics serverside Integration for AppBoy")

#Analytics server side Integration for [AppBoy](https://www.appboy.com), by [Astronomer.io](http://www.astronomer.io/).

##Configuration

- [appGroupId](https://www.appboy.com/documentation/REST_API/#app-group-identifier-explanation) :  indicates the app title with which the data in this request is associated. It can be found in the Developer Console section of the Appboy dashboard.
- datacenter: Choose your datacenter from either US (default) or EU.
- [updateExistingOnly](https://www.appboy.com/documentation/REST_API/#user-attributes-object-specification): A flag to determine whether to update existing users only, defaults to false

####example
    settings = {
      appGroupId: '87dc25f8-6c23-4e49-9a8d-fc4053fdec04',
      updateExistingOnly: false,
      datacenter: 'US'
    };

### Sample analytics.js Track Call
This will be mapped to a POST to the AppBoy RESTS api. (see below).
```javascript
analytics.track('Order Completed', {
  currency: 'USD',
  products: [
        {
          "product_id": "507f1f77bcf86cd799439011",
          "sku": "45790-32",
          "name": "Monopoly: 3rd Edition",
          "price": 19,
          "quantity": 1,
          "category": "Games"
        },
        {
          "id": "505bd76785ebb509fc183733",
          "sku": "46493-32",
          "name": "Uno Card Game",
          "price": 3,
          "quantity": 2,
          "category": "Games"
        }
  ]});
```

### Sample AppBoy Track Call
```javascript
POST https://api.appboy.com/users/track
Content-Type: application/json
{
    "app_group_id": "87dc25f8-6c23-4e49-9a8d-fc4053fdec04",
    "purchases": [
      {
        "external_id": "track-products-user-id",
        "product_id": "507f1f77bcf86cd799439011",
        "time": "2015-01-01T00:00:00.000Z",
        "price": 19,
        "quantity": 1,
        "currency": "USD",
        "_update_existing_only": false
      },
      {
        "external_id": "track-products-user-id",
        "product_id": "505bd76785ebb509fc183733",
        "time": "2015-01-01T00:00:00.000Z",
        "price": 3,
        "quantity": 2,
        "currency": "USD",
        "_update_existing_only": false
      }
    ]
}
```

##License
Released under the [MIT license](License.md).
