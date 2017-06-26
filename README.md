# emailer_app
send email via a web interface

My app sends emails from a predetermined (hard coded) email-address. It provides a web interface to enter the message,
the intended receiver etc..

Design choices:

1) I used rather simple code to send the email. One of my email addresses (gmail) won't work as sender, because apparently
my app is not secure enough. I found ample documentation from gmail, how to interface with their server securely, but it didn't
implement it for time reasons. Any serious application would require more attention to security.
2) Looking at https://tools.ietf.org/html/rfc3696#section-3 it appears that email-addresses can be a lot of crazy things. When
validating email-addresses I try to adhere to the recommendations in this document. I do this with a horrible looking regex
which, unfortunately is very hard to read.
3) I decided to use sinatra because the interface is very simple.
4) The workhorse of my implementation is the Email class. It is always initiated empty, and can be filled with everything that
is supposed to go into an email, e.g. sender and message text. It provides a method finalize which checks if everything that is
required has been supplied and it also validates the supplied email addresses. An email that has been finalized knows how to
send itself.

If you want to try out the code for your self:
I have marked the sections in app.rb (there are two place where changes are necessary) where you need to substitute the
account information for the email which you want to use as sender.
