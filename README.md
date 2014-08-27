email-addresses.js
==================

An RFC 5322 email address parser.

v 1.1.1

What?
-----
Want to see if something could be an email address? Want to grab the display name or just the address out of a string? Put your regexes down and use this parser!

This library does not validate email addresses - we can't really do that without sending an email. However, it attempts to parse addresses using the (fairly liberal) grammar specified in RFC 5322. You can use this to check if user input looks like an email address.

Why use this?
-------------
Use this library because you can be sure it really respects the RFC:
 - The functions in the recursive decent parser match up with the productions in the RFC
 - The productions from the RFC are written above each function for easy verification
 - Tests include all of the test cases from the [is_email](https://github.com/dominicsayers/isemail) project, which are extensive

Installation
------------
Add as a library resource to Google Apps Script projects.
- Publicly available, library key M26NvEFUvGLQadhq7G3OQmgFzUAA6_aCl.
- Documentation [available here](https://script.google.com/macros/library/d/M26NvEFUvGLQadhq7G3OQmgFzUAA6_aCl/1).

The only file needed for Google Apps Script is lib/email-addresses.js.

Example
-------

```
 var result = emailAddresses.parseOneAddress('"Jack Bowman" <jack@fogcreek.com>');
 // { name: '"Jack Bowman"',
 //   address: 'jack@fogcreek.com',
 //   local: 'jack',
 //   domain: 'fogcreek.com' }
 result = emailAddresses.parseAddressList('jack@fogcreek.com, Bob <bob@example.com>');
 // [ { name: null,
 //     address: 'jack@fogcreek.com',
 //     local: 'jack',
 //     domain: 'fogcreek.com' },
 //   { name: 'Bob',
 //     address: 'bob@example.com',
 //     local: 'bob',
 //     domain: 'example.com' } ]
 result = emailAddresses.parseOneAddress("bogus");
 // null
```

References
----------
 - http://tools.ietf.org/html/rfc5322
 - http://code.google.com/p/isemail/

Props
-----
Many thanks to [Dominic Sayers](https://github.com/dominicsayers) and his documentation and tests
for the [is_email](https://github.com/dominicsayers/isemail) function which helped greatly in writing this parser.

License
-------
Licensed under the MIT License. See the LICENSE file.
