Detailed PHP requirements
=========================

You need PHP 5.4 compiled with (at least) the following modules (those
are actually very common and should be available in any reasonable Linux distro):

-   JSON
-   mbstring
-   CURL (not required, but highly recommended) OR support for remote
    fopen()
-   posix functions (for the multiprocess update daemon, otherwise not
    needed)
-   GD (for OTP QR code generation, otherwise not needed)
-   PostgreSQL or MySQL depending on the database server used

Plugins may have additional dependencies i.e. several bundled plugins depend on CURL.

Some safe\_mode-related restrictions may stop parts of tt-rss from
functioning. This is usually only a problem for (unsupported) shared
hosting configurations.

NB: I’m using whatever Debian stable is shipping. If you decide to use bleeding edge php, especially beta
versions, and run into issues, most likely I won’t be able to help you. -fox
