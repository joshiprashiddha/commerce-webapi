The `RequisitionList` object contains the following attributes.

Attribute |  Data Type | Description
--- | --- | ---
`description` | String | Optional text that describes the requisition list
`items` | [RequistionListItems](#requistionlistitems-attributes) | An array of products added to the requisition list
`items_count` | Int! | The number of items in the list
`name` | String! | The requisition list name
`uid` | ID! | The unique requisition list ID
`updated_at` | String | The time of the last modification of the requisition list

### RequistionListItems attributes

The `RequistionListItems` object contains the following attributes.

Attribute |  Data Type | Description
--- | --- | ---
`items` | [[RequisitionListItemInterface]!](../../graphql/schema/b2b/requisition-list/interfaces/item.md) | An array of items in the requisition list
`page_info` | SearchResultPageInfo  | Contains pagination metadata
`total_pages` | Int! | The number of pages returned
