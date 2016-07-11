# Email Specifications

## Note of intent
This document is intended as a starting point for reference on where specifications should be provided and eventually for the specifications themselves. This note itself should be updated as the scope and intent of the document changes.

## Areas of interest

### Security
* Document Encryption
* Header requirements
** SPF, DKIM required
* External references, filetype support
** cross-origin loads are not valid resources
* Code transformations
* Embedded data
* Plugins
* Character sets

## HTML
* How to embed an HTML email within a webmail or application. Some webmails
like Gmail, Yahoo or Outlook.com embed the HTML directly within the
webmail. Others like AOL use an iframe.
* Supported attributes. Given the immensity of JavaScript attributes that
can be written directly inline (like "onload", "onmouseover", etc.), I
believe the safest way to embed an HTML email within a webmail is to have a
white list of supported attributes. I believe attributes like "id" and
"class" should be supported. But for some reason, a webmail like Gmail
removes this (even though it keeps styles targeting classes or ids).
* Attributes prefixing. Supported attributes like class or ids should be
prefixed in order to prevent an email to reuse styles from a webmail. This
is done by webmails like Yahoo.
* Supported elements. Listing elements that should or shouldn't be
supported by webmails and email clients. For example, should a webmail
support video or audio tags ? What are the security implications ?
* Image blocking. Some webmails (like Outlook.com) block images by
replacing the image path in the src attribute with a dummy pixel image.
Others (like Gmail, Yahoo or AOL) remove the src attribute. Both solutions
have different results across browsers depending on other attributes
present on the images.
* DOCTYPE. Is this a requirement? Should there be a new doctype? no doctype?

## CSS
* Supported properties. Things like "position:fixed" should be removed for
security reasons (a malicious email could easily position an element above
the webmail's UI). What properties and values should be allow ?
* Filtering guidelines. If a style has to be filtered, how should this
happen ? Some webmails remove only the property concerned. Others the
complete CSS rule. And others the complete style tag.
* Styles prefixing. This follows the HTML guideline for attributes
prefixing. But there's allow cases were prefixing needs to happen in CSS.
For example, a webmail should prefix animations @keyframes declarations
names (in order to avoid a malicious email to use same names as in the
webmail's UI).

## MIME
