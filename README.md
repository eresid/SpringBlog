SpringBlog
=====

SpringBlog is a very simple and clean-design blog system implemented with Spring Boot.
I had put it on production for my personal [bvn13's blog](https://bvn13.tk) since 2017-11-03. 


SpringBlog is powered by many powerful frameworks and third-party projects:

- Spring Boot and many of Spring familiy (e.g. Spring MVC, Spring JPA, Spring Secruity and etc)
- Hibernate + PostgreSQL
- [HikariCP](https://github.com/brettwooldridge/HikariCP) - A solid high-performance JDBC connection pool
- [Bootstrap](https://getbootstrap.com) - A very popular and responsive front-end framework
- [Pegdown](https://github.com/sirthias/pegdown) - ~~A pure-java markdown processor~~ **(depricated)**
- [ACE Editor](http://ace.c9.io/) - A high performance code editor which I use to write posts and code.
- [Pygments](http://pygments.org/) - ~~A python library for highlighting code syntax~~ **(depricated)**
- [Flexmark](https://github.com/vsch/flexmark-java) - Java implementation of CommonMark 0.28 spec parser using the blocks first, inlines after Markdown parsing architecture
- [Jade4j](https://github.com/neuland/jade4j) - [Jade](http://jade-lang.com/) is an elegant template language.
- [Webjars](http://www.webjars.org/) - A client-side web libraries packaged into JAR files. A easy way to manage JavaScript and CSS vendors in Gradle.
- [Redis](http://redis.io/) - A very powerful in-memory data cache server.
- [github-markdown-css](https://github.com/sindresorhus/github-markdown-css) - markdown syntax highlighter

## Changelog

#### 2017-11-09

* Implemented files uploads/downloads

#### 2017-11-08

* Added sharing buttons via [sharethis.com](https://platform.sharethis.com) - register and change verification code to use it
* Removed deprecated Jython, Pygments and Pegdown. Replaced with [Flexmark](https://github.com/vsch/flexmark-java) and [github-markdown-css](https://github.com/sindresorhus/github-markdown-css) 

#### 2017-11-07

* Added 'admin' button on  the home page if admin is logged in
* Added SEO meta-tags:
  1. list of keywords
  2. description
* Updated html > head > title for posts pages

#### 2017-11-03

* Was forked from [SpringBlog by Raysmon](https://github.com/Raysmond/SpringBlog)
* Was migrated onto __SpringBoot 1.5.8__, all libraries was updated



## Development

Before development, please install the following service software:

- [MySQL](https://www.mysql.com)
- [Redis](http://redis.io)
- [Pygments](http://pygments.org)

Edit the spring config profile `src/main/resources/application.yml` according to your settings.

And start MySQL and Redis first before running the application.

```
# If you're using Ubuntu server

# Install MySQL
apt-get install mysql-server
service mysql start
mysql -u root -p
>> create database spring_blog;


# Install Python pygments
apt-get install python-pip
pip install pygments
```

```
# If you want to enable redis cache
# Install redis server first, you can find instructions
# from https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis
service redis_6379 start
```

This is a Gradle project. Make sure Gradle is installed in your machine.
Try `gradle -v` command. Otherwise install in from [http://www.gradle.org/](http://www.gradle.org/).
I recommend you import the source code into Intellij IDE to edit the code.

```
# Start the web application
./gradlew bootRun
```

## Development

**How to import the project into Intellij IDEA and run from the IDE?**


1. Clone the project
`git clone https://github.com/Raysmond/SpringBlog.git `
2. Download all dependencies
`cd SpringBlog `
`./gradlew idea `
3. Open the project in Intellij IDEA.
4. Run `Application.java` as Java application.
5. Preview: http://localhost:8001
    Admin: http://localhost:8001/admin , the default admin account is: admin@admin.com, password: admin


> Lombok is required to run the project. You can install the plugin in Intellij IDEA.
> Reference: https://github.com/mplushnikov/lombok-intellij-plugin


## Deployment

- Build application jar `./gradlew build`, then upload the distribution jar (e.g. `build/libs/SpringBlog-0.1.jar`) to your remote server.
- Upload `application-production.yml` to your server and change it according to your server settings.
- Run it (Java8 is a must)

  ```
  # assuming you have the jar and yml files under current dir
  java -jar SpringBlog-0.1.jar --spring.config.location=application-production.yml
  ```

## License
Modified BSD license. Copyright (c) 2015, Jiankun LEI (Raysmond).
