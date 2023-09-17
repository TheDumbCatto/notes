
# Nits & bits of capabilities
- **Time-based policy**: Assign time of validity to **Domain** or **Category** exception rule.
  Requires support to enable **time_based_policy** on the tenant
# Demo & PoC 
**Workflow**: Web isolation -> Document isolation -> Email isolation

**Web isolation**
- Should use prepend mode
- 2 window side-by-side, one opening a website without isolation, one with isolation
- The website should be something popular in the region of the PoC
- Show the bottom banner & its' functionality
- Show the HTML comparison of 2 windows
- Show ACR rendering speed through Youtube videos

**Document isolation**
- Still in prepend mode
- Find dummy pdf, showcase the re-written links

**Email isolation**
- Attach a phishing link from Menlo's list and send to the PoC machine
- Show the input/keyboard blocking mechanism
- Show the re-written link