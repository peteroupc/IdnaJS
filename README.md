IdnaJS
=======

**Download source code: [ZIP file](https://github.com/peteroupc/IdnaJS/archive/master.zip)**

----

A JavaScript implementation of IDNA 2008 and Unicode normalization.

Installation
----------

Run the following code, assuming you have `npm` installed:

     npm install peteroupc/IdnaJS

Usage
----------

     var idna=require("idnajs"),
           Normalizer=idna.Normalizer,
           Idna=idna.Idna;

Normalizer.IsNormalized(string[, form])
--------------
Returns whether the specified string is in a Unicode normalization form.
The form can be `Normalization.NFC`, `Normalization.NFD`, `Normalization.NFKC`,
or `Normalization.NFKD`.  If not given, NFC is assumed.  Returns false if the string
is null or contains an unpaired surrogate code point.

Normalizer.Normalize(string[, form])
--------------
Converts the specified string is in a Unicode normalization form.
The form can be `Normalization.NFC`, `Normalization.NFD`, `Normalization.NFKC`,
or `Normalization.NFKD`.  If not given, NFC is assumed.  Throws an error if the
string is null.  Replaces unpaired surrogate code points in the string with
U+FFFD (the replacement character).

Idna.EncodeDomainName(string)
-------------
Tries to encode each label of the specified domain name into Punycode.  Labels
where this is not possible remain unchanged.  The labels are not checked for
validity beyond the Punycode checks.

Idna.IsValidDomainName(string[, lookupRules])
-------------
Checks whether a domain name is valid under IDNA 2008 (the second version
of Internationalized Domain Names in Applications).  If `lookupRules` is true,
uses somewhat more relaxed rules to be followed before looking up a domain
name in the DNS; if `lookupRules` is omitted, the value `false` is assumed.

Source Code
---------
Source code is available in the [project page](https://github.com/peteroupc/IdnaJS).

About
-----------

Written by Peter O.

See the [LICENSE](https://github.com/peteroupc/IdnaJS/blob/master/LICENSE.md) file for license information.
