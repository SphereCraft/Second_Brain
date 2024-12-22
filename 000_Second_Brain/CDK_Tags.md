
# Notes / Work - 22-12-2024

### 📅 Date: 22-12-2024
### 🕒 Time: 13:26:13

# CDK Tags
## Overview
CDK Tags are a way to see what the code was mean to do and to even use it in a way for costing. Imagine writing the code and then 6 months later
and try to understand what the code was to do and even how it was implemented. The example below show tags for an IAM creation file with 2 Tags
for ease of identification and to help understand how the file was implemented.

    cdk.Tags.of(this).add('Purpose', 'IAM Management');
    cdk.Tags.of(this).add('ManagedBy', 'CDK');

cdk.Tags is a utility class for managing resource tags
.of(this) tells CDK to apply these tags to the current stack and all its children resources
.add('key', 'value') creates a key-value pair tag





---

## References
- [Reference 1](#)
- [Reference 2](#)

