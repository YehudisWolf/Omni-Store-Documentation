# Tax Overview 

If the customer is not tax exempt and the product and variant are taxable, then the tax check is begun.

There are 2 tax options, each are mutualy exclusive: taxByState where each state has a different tax rate, or generic taxRate for all states.

If taxByState is enabled and there is a record that matches this carts shipping address, then the taxrate set in that record will be calculated against each cartProduct.

If taxByState is not enabled AND the taxRate (siteSettings table) is set above 0, each cartProduct is checked to see that the products taxtype is set to ‘tt_1’. If it is set to ‘tt_1’, then if either the sites state and the carts shipping address state must match, or the taxOutState feature is enabled, tax is calculated against the cartProduct.