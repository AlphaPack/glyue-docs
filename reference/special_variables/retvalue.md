# retvalue

Variables that indicates the return value from a formula block. Used when the contents of a formula block / lifecycle hook spans multiple lines, or if the single line does not resolve into a singular value.

Examples:

```python
apply_exchange_rate_adjustments(sf_collateral.response.payload.collateral)
apply_inflation_adjustments(sf_collateral.response.payload.collateral)
retvalue = sum(c.amount for c in sf_collateral.response.payload.collateral)
```

```python
if input.payload == "test value":
    retvalue = input.payload
else:
    retvalue = "value not provided"
```
