
# Apache Roller

[Apache Roller](http://roller.apache.org) is a Java-based, full-featured, multi-user and group-blog server suitable for blog sites large and small.
Roller is typically run with Apache Tomcat and MySQL.

## What is Roller?

Roller is an open source blogging platform that has been in active development since 2002. It supports:

- **Multi-user blogging** – host any number of independent weblogs on a single installation
- **Rich content editing** – create and manage blog entries with media, categories, and tags
- **Theme and template customisation** – Velocity-powered templates give full control over the look and feel of each blog
- **Comment management** – built-in spam filtering and moderation workflows
- **Full-text search** – powered by Apache Lucene
- **Web services** – XML-RPC, Atom Publishing Protocol (AtomPub), and OpenSearch support
- **Planet aggregation** – aggregate and display feeds from multiple external blogs in one place
- **Media management** – upload and organise images and other file attachments

## Technology Stack

| Layer | Technology |
|---|---|
| Language | Java 11+ |
| Build | Apache Maven |
| Web MVC | Apache Struts 2 |
| Dependency injection | Spring Framework, Google Guice |
| Security | Spring Security |
| Templating | Apache Velocity, JSP / Apache Tiles |
| Persistence | JPA (EclipseLink) |
| Full-text search | Apache Lucene |
| Feed parsing | ROME |
| Production server | Apache Tomcat + MySQL/PostgreSQL |
| Development server | Jetty + Apache Derby (embedded) |

## Maven Modules

Roller is made up of the following Maven projects:

* _roller-project_:         Top level project
* _app_:                    Roller Weblogger webapp, JSP pages, Velocity templates
* _db-utils_:               Database setup and migration utilities
* _assembly-release_:       Used to create official distributions of Roller
* _docs_:                   Roller documentation in ASCII Doc format
* _it-selenium_:            Integrated browser tests for Roller using Selenium

## Key Application Components

The `app` module contains the following major packages:

| Package | Description |
|---|---|
| `business` | Core service layer – `UserManager`, `WeblogManager`, `WeblogEntryManager`, etc. |
| `weblogger/pojos` | JPA entity model – `Weblog`, `WeblogEntry`, `WeblogCategory`, `MediaFile`, `User`, etc. |
| `ui/struts2` | Struts 2 action classes for the admin UI and blog editor |
| `ui/rendering` | Blog rendering engine – maps URLs, invokes Velocity templates, caches output |
| `webservices` | XML-RPC, AtomPub, OAuth and OpenSearch endpoint implementations |
| `business/search` | Lucene-based search index management |
| `planet` | Planet aggregation feature – feed fetching, subscription management |

## Documentation

The Roller Install, User and Template Guides are available in ODT format (for OpenOffice or LibreOffice):

* <https://github.com/apache/roller/tree/master/docs>

## For more information

Hit the Roller Confluence wiki:

* How to build and run Roller: <https://cwiki.apache.org/confluence/x/EM4>
* How to contribute to Roller: <https://cwiki.apache.org/confluence/x/2hsB>
* How to make a release of Roller: <https://cwiki.apache.org/confluence/x/gycB>
* Other developer resources: <https://cwiki.apache.org/confluence/x/D84>


## Installing Roller

If you want to run Roller in production, then you should download the latest official release and install it by following the Installation Guide, which you can find at the documentation link: <https://github.com/apache/roller/tree/master/docs>.


## Quick start: Running via Maven

You probably should not run Roller in production using this technique, but it's a relatively easy way to try Roller for yourself.
Assuming you've got a UNIX shell, Java, Maven and Git:

Get the code:

    $ git clone https://github.com/apache/roller.git

Compile and build Roller:

    $ cd roller
    $ mvn -DskipTests=true install

Run Roller in Jetty with an embedded Derby database (for testing only):

    $ mvn jetty:run

Once Jetty is up and running browse to <http://localhost:8080/roller> to try Roller.


## Quick start: running via Docker

Another way to try Roller is to use Docker.
This is actually easier than running via Maven because you do not need Maven or Java.
If you've got Docker, here's how you can run Roller for demo purposes.

Get the code:

    $ git clone https://github.com/apache/roller.git

Run Docker Compose to build and launch Roller along with a PostgreSQL database:

    $ cd roller
    $ docker-compose up

It will take a while to build and start the Docker image.
Once it's done browse to <http://localhost:8080/roller> to try Roller.
