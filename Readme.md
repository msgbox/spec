MsgBox Spec Proposal
========================

MsgBox is a format meant to replace the important parts of email while
leaving behind the baggage.

Email has become overrun with newsletters, spam and conversations while items
that need to be taken care of are lost or hidden in the noise.

Email also has it's problems simply from it's age.

It is non-international with email address and headers being in US-ASCII format.

It is insecure and unencrypted by default.

MsgkBox aims to fix this. By using UTF-8 Unicode, internationalization is possible in
every field including the account address.

It should also encrypt the body and attachments of the message by default using a
common encryption standard.

To prevent spam, instead of the concept of a spam blacklist a whitelist is used
to limit which accounts are able to add items to an account's box.

The MsgBox format is made up of:

  - Header
    - Creator (individual account)
    - Receiver (individual or domain box)
    - Created_At (timestamp)
    - MessageID (UUID)

  - Payload
    - Title, optional
    - Body, optional

  - Attachments
    - TODO


# Account Address

Accounts should be unique per provider.

## Individual Address

`particlebanana:home::example.com`

Broken down this represents a user [particlebanana] followed by a colon followed by
the box name [home] followed by a double colon followed by the domain [example.com].

## Shared Address

`+organization:work::example.com`

This adds a plus symbol to the beginning of an addressee to explicitly state that the
task should be shared between multiple parties.

# Encryption

TODO

# Server Implementation

TODO

# Response Messages

TODO
