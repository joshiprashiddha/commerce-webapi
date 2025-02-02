The `Wishlist` object contains all the items in the customer's wish list.

Attribute | Data type | Description
--- | --- | ---
`id` | ID | The unique ID of a `Wishlist` object
`items` | [[WishlistItem](#wishlistitem-attributes)] | Deprecated. Use `items_v2` instead
`items_v2` | [[WishlistItemInterface]](../../graphql/schema/wishlist/interfaces/wishlist.md) | An array of items in the customer's wish list
`items_count` | Int | The number of items in the wish list
`name` | String | The wish list name. Applicable to Adobe Commerce only
`sharing_code` | String | An encrypted code that the application uses to link to the wish list
`updated_at` | String | The time of the last modification to the wish list
`visibility` | WishlistVisibilityEnum! | An enum indicating whether the wish list is PUBLIC or PRIVATE. Applicable to Adobe Commerce only

#### WishlistItem attributes

The `WishlistItem` object can contain the following attributes.

Attribute | Data type | Description
--- | --- | ---
`added_at` | String | The time when the customer added the item to the wish list
`description` | String | The customer's comment about this item
`id` | Int | The wish list item ID
`product` | [ProductInterface](../../graphql/schema/products/interfaces/types/index.md) | The ProductInterface contains attributes that are common to all types of products. Note that descriptions may not be available for custom and EAV attributes
`qty` | Float | The quantity of this wish list item
