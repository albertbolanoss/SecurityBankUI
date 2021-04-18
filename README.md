# Bankui

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 10.0.3.

## Create self signed certiificate
1. Create a server.cnf file, remove "#" on ALTNAMES to write your DNS i.e:
ALTNAMES = DNS:$FQDN   , DNS:bar.example.org , DNS:www.foo.example.org
1. execute the following command on GitBath or Linux

```sh
openssl req -new -config myserver.cnf -keyout myserver.key -out myserver.csr
```

server.cnf
```cnf
# OpenSSL configuration file for creating a CSR for a server certificate
# Adapt at least the FQDN and ORGNAME lines, and then run 
# openssl req -new -config myserver.cnf -keyout myserver.key -out myserver.csr
# on the command line.

# the fully qualified server (or service) name
FQDN = foo.example.org

# the name of your organization
# (see also https://www.switch.ch/pki/participants/)
ORGNAME = Example University

# subjectAltName entries: to add DNS aliases to the CSR, delete
# the '#' character in the ALTNAMES line, and change the subsequent
# 'DNS:' entries accordingly. Please note: all DNS names must
# resolve to the same IP address as the FQDN.
ALTNAMES = DNS:$FQDN   # , DNS:bar.example.org , DNS:www.foo.example.org

# --- no modifications required below ---
[ req ]
default_bits = 2048
default_md = sha256
prompt = no
encrypt_key = no
distinguished_name = dn
req_extensions = req_ext

[ dn ]
C = CH
O = $ORGNAME
CN = $FQDN

[ req_ext ]
subjectAltName = $ALTNAMES
```

To more informarmation visit [this page](https://www.switch.ch/pki/manage/request/csr-openssl/)

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
