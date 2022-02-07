# Grafana pour YunoHost

[![Niveau d'intégration](https://dash.yunohost.org/integration/grafana.svg)](https://dash.yunohost.org/appci/app/grafana) ![](https://ci-apps.yunohost.org/ci/badges/grafana.status.svg) ![](https://ci-apps.yunohost.org/ci/badges/grafana.maintain.svg)  
[![Installer Grafana avec YunoHost](https://install-app.yunohost.org/install-with-yunohost.svg)](https://install-app.yunohost.org/?app=grafana)

*[Read this readme in english.](./README.md)*
*[Lire ce readme en français.](./README_fr.md)*

> *Ce package vous permet d'installer Grafana rapidement et simplement sur un serveur YunoHost.
Si vous n'avez pas YunoHost, regardez [ici](https://yunohost.org/#/install) pour savoir comment l'installer et en profiter.*

## Vue d'ensemble

Tableaux de bords de supervision

**Version incluse :** 8.3.3~ynh1

**Démo :** https://play.grafana.org

## Captures d'écran

![](./doc/screenshots/Grafana8_Kubernetes.jpg)

## Avertissements / informations importantes

## Configuration

**Important at first login:**

* you have to go the Grafana Menu (Grafana icon), select your account menu and select *Switch to Main Org.*
* you can now access the default NetData dashboard via the Home menu

**Don't hesitate to create new dashboards**: the default dashboard contains metrics from NetData, but only generic ones that are generated on every machine. NetData dynamically detects services and applications (e.g.redis, nginx, etc.) and enriches its dashboard and generated metrics. Many NetData metrics don't appear in the provided default Grafana dashboard!

## Documentation

 * Official Grafana documentation: https://grafana.com/docs/grafana/latest/
 * Official InfluxdB documentation: https://docs.influxdata.com/influxdb/
 * YunoHost documentation: If specific documentation is needed, feel free to contribute.

## YunoHost specific features

* installs InfluxDB as time series database
* if the NetData package is installed, configures NetData to feed InfluxDB every minute
* installs Grafana as dashboard server
* creates a Grafana Data Source to fetch data from InfluxDB (and hence NetData!)
* creates a default dashboard to plot some data from NetData (doesn't cover every metric, can be greatly enhanced!)

#### General architecture

![image](https://cloud.githubusercontent.com/assets/2662304/20649711/29f182ba-b4ce-11e6-97c8-ab2c0ab59833.png)

#### Multi-users support

LDAP and HTTP auth are supported.

## Limitations

* The default dashboard may be updated in a further release of this package, so please make sure you create your own dashboards!
* Organizations creation doesn't play well with LDAP integration; it is disabled for standard users, but can't be disabled for administrators: **please do not create organizations**!

## Documentations et ressources

* Site officiel de l'app : https://grafana.com/
* Dépôt de code officiel de l'app : https://github.com/grafana/
* Documentation YunoHost pour cette app : https://yunohost.org/app_grafana
* Signaler un bug : https://github.com/YunoHost-Apps/grafana_ynh/issues

## Informations pour les développeurs

Merci de faire vos pull request sur la [branche testing](https://github.com/YunoHost-Apps/grafana_ynh/tree/testing).

Pour essayer la branche testing, procédez comme suit.
```
sudo yunohost app install https://github.com/YunoHost-Apps/grafana_ynh/tree/testing --debug
ou
sudo yunohost app upgrade grafana -u https://github.com/YunoHost-Apps/grafana_ynh/tree/testing --debug
```

**Plus d'infos sur le packaging d'applications :** https://yunohost.org/packaging_apps