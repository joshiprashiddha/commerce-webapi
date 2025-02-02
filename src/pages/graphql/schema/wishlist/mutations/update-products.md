---
title: updateProductsInWishlist mutation | Commerce Web APIs
---

# updateProductsInWishlist mutation

The `updateProductsInWishlist` mutation changes the quantity, description and option information for the specified items in the customer's wish list.

<InlineAlert variant="info" slots="text" />

Use the `removeProductsFromWishlist` mutation to remove an item from the wish list. Do not set the quantity of an item to 0.

This mutation requires a valid [customer authentication token](../../customer/mutations/generate-token.md).

## Syntax

```graphql
mutation {
  updateProductsInWishlist(
    wishlistId: ID!
    wishlistItems: [WishlistItemUpdateInput!]!
  ){
      UpdateProductsInWishlistOutput
  }
}
```

## Example usage

The following example changes the quantity of the product represented by wish list item `16` to `2` and adds a description for item `17`.

**Request:**

``` graphql
mutation {
  updateProductsInWishlist(
  wishlistId: 2
  wishlistItems: [
    {
      wishlist_item_id: 10
      quantity: 2
    }
    {
      wishlist_item_id: 11
      description: "I love this!"
    }
  ]){
    wishlist {
      id
      items_count
      items_v2 {
        items {
          id
          quantity
          product {
            name
            sku
            uid
            price_range {
              minimum_price {
                regular_price {
                  currency
                  value
                }
              }
              maximum_price {
                regular_price {
                  currency
                  value
                }
              }
            }
          }
        }
      }
    }
    user_errors {
      code
      message
    }
  }
}
```

**Response:**

```json
{
  "data": {
    "updateProductsInWishlist": {
      "wishlist": {
        "id": "2",
        "items_count": 8,
        "items_v2": {
          "items": [
            {
              "id": "8",
              "quantity": 1,
              "product": {
                "name": "Advanced Pilates & Yoga (Strength)",
                "sku": "240-LV08",
                "uid": "NDk=",
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 18
                    }
                  },
                  "maximum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 18
                    }
                  }
                }
              }
            },
            {
              "id": "10",
              "quantity": 1,
              "product": {
                "name": "Layla Tee",
                "sku": "WS04",
                "uid": "MTQ1MA==",
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 29
                    }
                  },
                  "maximum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 29
                    }
                  }
                }
              }
            },
            {
              "id": "11",
              "quantity": 1,
              "product": {
                "name": "Radiant Tee",
                "sku": "WS12",
                "uid": "MTU2Mg==",
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 22
                    }
                  },
                  "maximum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 22
                    }
                  }
                }
              }
            },
            {
              "id": "12",
              "quantity": 1,
              "product": {
                "name": "Electra Bra Top",
                "sku": "WB01",
                "uid": "MTYxMA==",
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 39
                    }
                  },
                  "maximum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 39
                    }
                  }
                }
              }
            },
            {
              "id": "13",
              "quantity": 1,
              "product": {
                "name": "Celeste Sports Bra",
                "sku": "WB03",
                "uid": "MTY0Mg==",
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 39
                    }
                  },
                  "maximum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 39
                    }
                  }
                }
              }
            },
            {
              "id": "15",
              "quantity": 2,
              "product": {
                "name": "Nora Practice Tank",
                "sku": "WT03",
                "uid": "MTcyMg==",
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 39
                    }
                  },
                  "maximum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 39
                    }
                  }
                }
              }
            },
            {
              "id": "24",
              "quantity": 2,
              "product": {
                "name": "Layla Tee",
                "sku": "WS04",
                "uid": "MTQ1MA==",
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 29
                    }
                  },
                  "maximum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 29
                    }
                  }
                }
              }
            },
            {
              "id": "25",
              "quantity": 1,
              "product": {
                "name": "Radiant Tee",
                "sku": "WS12",
                "uid": "MTU2Mg==",
                "price_range": {
                  "minimum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 22
                    }
                  },
                  "maximum_price": {
                    "regular_price": {
                      "currency": "USD",
                      "value": 22
                    }
                  }
                }
              }
            }
          ]
        }
      },
      "user_errors": []
    }
  }
}
```

## Input attributes

The `updateProductsInWishlist` mutation requires the following input.

Attribute |  Data Type | Description
--- | --- | ---
`wishlistId` | ID! | The ID of the customer's wish list
`wishlistItems`| [[WishlistItemUpdateInput!](#wishlistitemupdateinput-attributes)]! | An array containing products to be updated

### WishlistItemUpdateInput attributes

The `WishlistItemUpdateInput` object defines each item to add to the wish list.

Attribute |  Data Type | Description
--- | --- | ---
`description` | String | Customer-entered comments about the item
`entered_options`| [EnteredOptionInput] | An array of options that the customer entered
`quantity` | Float | The amount or number of items to add
`selected_options` | [ID!] | An array of strings corresponding to options the customer selected
`wishlist_item_id` | ID! | The ID of the wishlist item to update

### EnteredOptionInput attributes

import EnteredOptionInput from '/src/pages/_includes/graphql/entered-option-input.md'

<EnteredOptionInput />

## Output attributes

The `UpdateProductsInWishlistOutput` object contains the customer's wish list and error message information.

Attribute |  Data Type | Description
--- | --- | ---
`user_errors` | [WishListUserInputError!]! | An array of errors encountered while adding products to a wish list
`wishlist` | Wishlist! | Contains the wish list with all items that were successfully added

### Wishlist attributes

import Wishlist from '/src/pages/_includes/graphql/wishlist.md'

<Wishlist />

### WishListUserInputError attributes

import WishlistUserInputErrors from '/src/pages/_includes/graphql/wishlist-user-input-errors.md'

<WishlistUserInputErrors />

## Errors

Error | Description
--- | ---
`The current user cannot perform operations on wishlist` | An unauthorized user (guest) tried to add an item to a wishlist, or an authorized user (customer) tried to add an item to a wishlist of another customer.
`The wishlist was not found.` | The value provifed in the `wishlistId` field is invalid or does not exist for the customer.
