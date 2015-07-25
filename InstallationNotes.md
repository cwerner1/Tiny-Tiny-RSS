Installation Guide
==================

Installing Tiny Tiny RSS for the first time
-------------------------------------------

Before you begin, you’ll need to verify the following:

1. You need access to a hosting/VDS running a http server and a database
(mysql or postgresql). Your database should properly support unicode.
2. You will need to acquire database credentials, i.e. login, password,
and a database name. If you don’t have a database already created, you
need to do so before installing. Tiny Tiny RSS can coexist with other
applications in a shared database, creating a dedicated one is not
necessary.
3. Your http server should be running PHP version 5.3 or later. Having
an accelerator like php-apc is highly recommended.
4. The manual assumes you have basic knowledge of Git SCM.

After you have gone through the above list, you can proceed to the
installation.

1. Clone tt-rss repository using Git

<code>git clone https://github.com/gothfox/Tiny-Tiny-RSS.git tt-rss</code>

Alternatively, you can clone the repository on your local machine and
upload files to the server using FTP or any other means available to
you.

If you don’t want to deal with repositories, Github has a “Download ZIP”
button (not recommended).

2. Verify that you can open http://your.site.com/tt-rss/install/

3. Proceed with the installation using the easy installer. It will ask
your database credentials and a full URL on which tt-rss will be
accessed, for example <code>http://your.site.com/tt-rss/install/</code>.
It is required that the URL is an externally accessible one (if any),
don’t use <code>localhost</code> there, it will break PUSH support. If
you are deploying tt-rss on LAN, you can disregard this requirement.

4. The easy installer will generate <code>config.php</code> for you,
after you have entered your database credentials and initialized tt-rss
database. You will need to either copy text from the installer and paste
it into <code>config.php</code> on the server, or, if possible, the
installer will be able to do it for you automatically.

5. It is suggested that you read through <code>config.php</code> to see
if you need to enable additional functionality or change default
configuration values.

5. After finishing with the installer, open your Tiny Tiny RSS
installation at <code>http://your.site.com/tt-rss/</code> and login with
default credentials (username: <code>admin</code>, password:
<code>password</code>).

6. Go to preferences and change your password!

7. You will also need to decide on the method tt-rss uses to update
feeds. This is a separate topic, outlined in [UpdatingFeeds](UpdatingFeeds).

7. If all went well, you may proceed to use tt-rss normally. Create a
separate non-admin user, login under it, and start importing your feeds,
subscribing, and configure it to your taste.

8. That’s all!

Don’t forget to read [UpdatingFeeds](UpdatingFeeds) otherwise your feeds won’t update
automatically.

### Take a look at available plugins

There are many plugins written for tt-rss. You can see the list here: [Plugins](Plugins).

Upgrading Tiny Tiny RSS
-----------------------

It is highly recommended to temporarily disable any third party themes
and user CSS customizations before upgrading. Don’t forget to empty your
browser cache if you experience weird bugs right after upgrading.

Note that you should upgrade to the latest version available, installing
intermediate releases sequentially is not needed.

1. Using Git
------------

Change to tt-rss directory on your server and run:

<code>git pull origin master</code>

That’s it. Proceed to section 2.

2. Merging new config.php directives and updating the database
--------------------------------------------------------------

After the files have been upgraded by newer versions, open tt-rss. It
may complain about missing directives in <code>config.php</code>. If
that happens, you will need to either merge new stuff from
<code>config.php-dist</code> to your <code>config.php</code> or remove
<code>config.php</code> and rerun the installer (take note to copy
previous value of <code>FEED\_CRYPT\_KEY</code> if you have feeds with
authentication enabled).

DO NOT INITIALIZE DATABASE when upgrading. This will remove all your
tt-rss data.

Afterwards, you may be redirected to the database updater. Log in with
admin credentials and follow instructions.

Finishing that, you should be able to use tt-rss normally by logging in
with your normal account.

3. Post-upgrade tasks
---------------------

1. You might need to clear your browser cache if you experience CSS or
script-related issues, older scripts might have stuck in it.
2. Do not copy cache directories from your old tt-rss version, it is
unnecessary and potentially creates problems if you don’t preserve file
modification times.
3. If you are using an accelerator like php-apc you might need to
restart apache if older cached versions of PHP files got stuck in cache
(this happens rarely, but is a possibility).
