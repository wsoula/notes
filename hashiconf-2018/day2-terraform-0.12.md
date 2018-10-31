Terraform 0.12
---
* dont need double quotes and dollar sign curly brace to interpolate variables
* rich value types - maps and lists, maps of maps, maps of lists of maps of lists - can save entire object so you can access different attributes
* improved error messages
* for expressions
  * for: list and map transformations
  * for_each: for dynamic nested blocks
  * can use for creating all the tags on an ec2 instance
Takeaway
* configuration is easier to read and reason about
* consistent, predictable behavior in complex functions
*
is XYZ feature part of 0.12.0?  Below are not in 0.12.0 but now can be built
  * module counts
  * module/resource for_each
  * module depends_on
Will need an upgrade tool they will release
