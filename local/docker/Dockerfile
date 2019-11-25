FROM httpd:2.4

RUN mkdir -p /private/libexec/apache2/
# Copy dispatcher module to --> /private/libexec/apache2/
COPY ./apache2-modules/ /private/libexec/apache2/
# Create Symbolic Link For dispatcher module. Refer inside httpd-dispatcher.conf
RUN ln -s /private/libexec/apache2/dispatcher-apache2.4-4.2.3.so /private/libexec/apache2/mod_dispatcher.so

# Copy configurations to --> /private/etc/apache2/conf/
RUN mkdir -p /private/etc/apache2/conf
COPY ./publish/etc/httpd/conf.d/ /private/etc/apache2/conf/

# Create folder for caching files
RUN mkdir -p /Library/WebServer/docroot/publish
# Set the permissions for Users/Group as defined in dev-httpd.conf
RUN chown -R daemon:daemon /Library/WebServer/docroot

# Create folder for log files
RUN mkdir -p /private/var/log/apache2

# Replace httpd.conf with current apache configuration. i.e. dev-httpd.conf
COPY ./dev-httpd.conf /usr/local/apache2/conf/httpd.conf
