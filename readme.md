Multiple Products DMN project
=============================

## Scenario

Each product has its own configuration parameters which are used to calculate a list of Price Point objects.
A customer can add multiple products to their basket.

If there are mulitple products in the basket, we want to return one set of Price Points for the entire basket.
There is a heirarchy within the products which we want to define in order to determine which product's configuration to use.

There are two categories of Products defined below:

CORE PRODUCTS hierarchy: 

1) Product A
2) Product B
3) Product C
4) Product D

ANCILLARY PRODUCTS hierarchy: 

Product E, Product F, Product G

The heirarchy for Ancillary Products is based on the product’s cost, from largest to smallest.


Core Products will always take priority over Ancillary Products, and are regardless of the price.

### Example scenarios

Basket: Product A, Product B

Result: Use configuration from Product A

----------------------------------------

Basket: Product B, Product D

Result: Use configuration from Product B

----------------------------------------

Basket: Product D, Product E (price: £20)

Result: Use configuration from Product D

----------------------------------------

Basket: Product E (price: £5), Product F (price: £10), Product G (price: £20)

Result: Use configuration from Product G

----------------------------------------

Basket: Product B, Product D

Result: Use configuration from Product B

------------------------------------

## Point calculation logic:

1) Identify the priority product in the basket
2) Take the configuration from that product and loop through logic to calculate the Price Points for each product in the basket
3) Sum all Price Points for each product and return one set of Price Points