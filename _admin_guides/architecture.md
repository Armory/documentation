---
layout: post
title: Architecture
order: 10
# This is not to be redirected to the Armory Spinnaker architecture page, as it has different content.
---
{% include components/legacy_documentation.html %}

* This is a placeholder for an unordered list that will be replaced with ToC. To exclude a header, add {:.no_toc} after it.
{:toc}


## Armory Spinnaker

<div class="mermaid">
 graph TB

 deck(Deck-Armory) --> gate;
 api(Custom Script/API Caller) --> gate(Gate);
 gate(Gate-Armory) --> kayenta(Kayenta);
 orca(Orca-Armory) --> kayenta(Kayenta);
 gate --> orca;
 gate --> clouddriver(Clouddriver);
 orca --> clouddriver;
 gate --> rosco(Rosco);
 orca --> front50;
 orca --> rosco
 gate --> front50(Front50);
 gate --> fiat(Fiat);
 gate --> kayenta(Kayenta);
 orca --> kayenta;
 clouddriver --> fiat;
 orca --> fiat;
 front50 --> fiat;
 echo(Echo-Armory) --> orca;
 echo --> front50;
 igor(Igor) --> echo;
 dinghy(Dinghy) --> front50;
 dinghy --> orca;
 configurator(Configurator) --> S3;
 front50 --> S3;
 platform(Platform) --> echo;
 platform --> orca;

 classDef default fill:#d8e8ec,stroke:#39546a;
 linkStyle default stroke:#39546a,stroke-width:1px,fill:none;

 classDef external fill:#c0d89d,stroke:#39546a;
 class deck,api external
 </div>

 {% include components/mermaid.html %}

We provide two methods of installing Spinnaker: Stand-Alone and High-Availability (HA).  The stand-alone version is there for development and evaluation purposes.  It's a simplified deployment and is the quickest way to evaluate Spinnaker.  The HA deployment provides redundancy and additional security such that there is no single point of failure.


## Stand-Alone

 * Local instance Redis
 * Local networking
 * Configuration persistance is done through s3


Below is a diagram of the architecture & components deployed in a stand-alone configuration.

![](/images/Image 2017-01-26 at 12.03.11 PM.png)


### Security Groups
In order to not expose any Spinnaker sub-services which may not contain authentication, we use internal and user-facing security groups.  The user-facing security group exposes ports for `gate` and `deck`, typically 8084 and 80 respectively.  A separate security group is used for internal communication between services.


### Autoscaling Groups & Launch Configurations
We'll create an ASG with the name `armoryspinnaker-preprod-v000`.  

By default, we create an instance with a private IP and keys which should only be accessible by your team.


## High Availability (HA)

* Redudancy and solid performance
    - Multiple Availability Zones (AZ) failovers
    - Scheduled jobs failovers into a new AZ
    - Polling jobs (jenkins, etc.) failovers into a new AZ
* HA is our intermediate step before breaking up each sub-service into multiple AZs

Below is a diagram of the architecture & components deployed in an HA configuration.

![](/images/Image 2017-01-26 at 11.18.35 AM.png)

## Polling and Non-Polling environments

For certain components you'll only want a single instance running on an ASG on "polling" mode.  Namely Igor and Echo which need to run on a
single instance so that multiple trigger events are not sent to Spinnaker and issuing multiple events for the same build.

## Systems Requirements

Armory Spinnaker runs only on Ubuntu & CentOS and RHEL based machines within AWS.  It uses AWS resources to run manage and run Armory Spinnaker.  

### Cloud & Operating Systems

We currently support running Armory Spinnaker in AWS.  By default it uses (3) m4.2xlarge machines for redudancy.  Once launched, this is completely configurable and based on your team's usage patterns can be scaled up and down with Spinnaker.

### Target Cloud Providers
We currently support AWS and Kubernetes. We plan to support GCP and Azure in the future.

## Docker

Armory Spinnaker uses Docker and Docker-Compose for every component possible.  

### Security Groups
In order to not expose any Spinnaker sub-services which may not contain authentication, we use internal and user-facing security groups to match the internal and external facing ELB.  The user-facing security group exposes ports for `gate` and `deck`, typically 8084 and 80 respectively.  If you choose to [configure SSL/HTTPS](http://docs.armory.io/admin-guides/auth/#enabling-httpsssl) at a later time, then 443 will need to be opened as well.  A separate security group is used for internal communication between services which exposes ports but only between members of the security group.
