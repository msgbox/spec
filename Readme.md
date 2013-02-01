MsgBox Spec Proposal
========================

MsgBox is an exercise in redefining what a modern day message/todo system would look like. If email was never built to do what it is tasked with doing today then what would that system look like?

As Paul Graham explained in his essay from March, 2012 [Frighteningly Ambitious Startup Ideas](http://www.paulgraham.com/ambitious.html), email has become a todo list with email as a way items get on that list.

There have been a few innovative concepts and implementations built on top email that allows it to be used in various ways and they have been relatively successful. Unfortunately the current trend of aqui-hires hasn't produced a long-lived solution.

## Design Requirements

What follows is what I see as necessities for a solution to have a chance at getting some sort of market penetration.

**1. Open Protocol.**

Whatever the solution is it needs to be an open protocol with a limited scope. It should be encompassing enough to allow items to be passed around and understood by any provider but still allow enough flexibility for people to build innovative things on top of it.

**2. Encryption**

Encryption should be built into the spec because it's 2013 and to not do so would be foolish.

**3. Give control to the Recipient instead of the Sender.**

Allow a person to actually be in control of who can send them items and what can be sent to them.


## Ideas

To prevent spam, instead of the concept of a spam blacklist a whitelist is used
to limit which accounts are able to add items to an account's "box".

## Item Format

The MsgBox format would look something like this:

* Header (non-encrypted)
    * Creator (individual account)
    * Receiver (individual or domain box)
    * Created_At (timestamp)
    * MessageID (UUID)
* Payload (encrypted)
    * Body
    * Metadata (key/value pairs)
* Attachments (binary data)


## Addresses

Addresses should be similar to an email address for familiarity.

### Individual Address

`particlebanana:home@example.com`

Broken down this represents a user [particlebanana] followed by a colon followed by a box name [home] followed by the domain [example.com]

### Shared Address

`+organization:work@example.com`

This adds a plus symbol to the beginning of an addressee to explicitly state that the item can be viewed by multiple parties. Similar in concept to a shared inbox or task list.

## Encryption

TO DO

## Server Implementation

TO DO

An Example architecture may look something like this:

**Outgoing Message**

* User interacts with implementor's API
* API sends an encrypted message to a Delivery Agent
* Delivery Agent pushes the message to an outgoing queue
* A Worker process grabs the message off the queue and sends it to a relay
* Relay finds the destination server by doing a DNS query on a SRV record and sends the message to the receivers Relay

**Incoming Message**

* Receiver Relay gets the message and writes it to an incoming queue
* A Worker process grabs the message off the queue and ensures the receiving account exists and is able to receive messages from the sender. If so write the message to a permanent data store and publish an event to a PubSub system.
* A User interacts with implementor's API to handle the message.

![example diagram](https://github.com/msgbox/spec/raw/master/img/Diagram.gif)

## Error / Status Messages

TO DO
