
Google Cloud Platform for Puppet
--------------------------------

[![Puppet Forge](http://img.shields.io/puppetforge/v/google/cloud.svg)](https://forge.puppetlabs.com/google/cloud)

This module installs all Google modules for Puppet to allow managing
[Google Cloud Platform][gcp] resources from your Puppet environment

#### Table of Contents

1. [Module Description](#module-description)
2. Setup
    * [Installing](#setup)
    * [Upgrading pre-release versions](#upgrading-pre_release-versions)
3. [Supported Google Cloud Platform Products][supported-products]
4. [Summary of Supported Products Types / Providers][supported-types]
5. [Supported Operating Systems](#supported-operating-systems)


## Module Description

This module is a convenience to install all Google Cloud Platform modules for
Puppet with a single command. You can install them individually if you wish as
well.


## Setup

To install this module on your Puppet Master (or Puppet Client/Agent), use the
Puppet module installer:

    puppet module install google/cloud

### Upgrading pre-release versions

If you already have pre-release modules installed (pre-release = modules with
version < 1.0.0) you need to force update of the modules, as they are
specifically strict about pre-release versions. You can do that by using the
`--force` argument on upgrade:

    puppet module upgrade --force google/cloud --version=<version>

You can find the latest version on [google/cloud][google-cloud-forge] Forge
page. If you omit the version you may get an intermedia upgrade, so please
re-run until you get the latest version.

Watch out for missing dependencies when you do that. If there are any missing
dependencies they will have a red `invalid` after the name of the module that
requires upgrade as well. The safest way is to upgrade all Google modules at
once (or remove them and do `puppet module install` again). Optionally you can
run a script to upgrade all Google modules, like this:

    puppet module list | awk '{print $2}' | grep '^google-' \
      | xargs -I{} puppet module upgrade --force {}

## Supported Google Cloud Platform Products

The `google/cloud` module installs the following modules automatically:

  - [Google Cloud BigQuery](#google-cloud-bigquery)
  - [Google Compute Engine](#google-compute-engine)
  - [Google Container Engine](#google-container-engine)
  - [Google Cloud DNS](#google-cloud-dns)
  - [Google Cloud IAM](#google-cloud-iam)
  - [Google Cloud Pub/Sub](#google-cloud-pub/sub)
  - [Google Cloud Resource Manager](#google-cloud-resource-manager)
  - [Google Spanner](#google-spanner)
  - [Google Cloud SQL](#google-cloud-sql)
  - [Google Cloud Storage](#google-cloud-storage)
  - [Google Authentication](#google-authentication)


## Summary of Supported Products Types / Providers

Below you can find a summary of each supported type and a brief description of
its intended behavior. For full details about each provider, properties,
parameters, usage and examples please visit its respective Puppet module project
page.


### Google Cloud BigQuery
Detailed information can be found at the
[google-gbigquery][] project home page.
The list below is a summary of the supported types by the module:


- `gbigquery_dataset`
  Datasets allow you to organize and control access to your tables.

### Google Compute Engine
Detailed information can be found at the
[google-gcompute][] project home page.
The list below is a summary of the supported types by the module:


- `gcompute_address`
  Represents an Address resource.
  Each virtual machine instance has an ephemeral internal IP address and,
  optionally, an external IP address. To communicate between instances on
  the same network, you can use an instance's internal IP address. To
  communicate with the Internet and instances outside of the same network,
  you must specify the instance's external IP address.
  Internal IP addresses are ephemeral and only belong to an instance for
  the lifetime of the instance; if the instance is deleted and recreated,
  the instance is assigned a new internal IP address, either by Compute
  Engine or by you. External IP addresses can be either ephemeral or
  static.

- `gcompute_backend_bucket`
  Backend buckets allow you to use Google Cloud Storage buckets with HTTP(S)
  load balancing.
  An HTTP(S) load balancer can direct traffic to specified URLs to a
  backend bucket rather than a backend service. It can send requests for
  static content to a Cloud Storage bucket and requests for dynamic content
  a virtual machine instance.

- `gcompute_backend_service`
  Creates a BackendService resource in the specified project using the data
  included in the request.

- `gcompute_disk_type`
  Represents a DiskType resource. A DiskType resource represents the type
  of disk to use, such as a pd-ssd or pd-standard. To reference a disk
  type, use the disk type's full or partial URL.

- `gcompute_disk`
  Persistent disks are durable storage devices that function similarly to
  the physical disks in a desktop or a server. Compute Engine manages the
  hardware behind these devices to ensure data redundancy and optimize
  performance for you. Persistent disks are available as either standard
  hard disk drives (HDD) or solid-state drives (SSD).
  Persistent disks are located independently from your virtual machine
  instances, so you can detach or move persistent disks to keep your data
  even after you delete your instances. Persistent disk performance scales
  automatically with size, so you can resize your existing persistent disks
  or add more persistent disks to an instance to meet your performance and
  storage space requirements.
  Add a persistent disk to your instance when you need reliable and
  affordable storage with consistent performance characteristics.

- `gcompute_firewall`
  Each network has its own firewall controlling access to and from the
  instances.
  All traffic to instances, even from other instances, is blocked by the
  firewall unless firewall rules are created to allow it.
  The default network has automatically created firewall rules that are
  shown in default firewall rules. No manually created network has
  automatically created firewall rules except for a default "allow" rule for
  outgoing traffic and a default "deny" for incoming traffic. For all
  networks except the default network, you must create any firewall rules
  you need.

- `gcompute_forwarding_rule`
  A ForwardingRule resource. A ForwardingRule resource specifies which pool
  of target virtual machines to forward a packet to if it matches the given
  [IPAddress, IPProtocol, portRange] tuple.

- `gcompute_global_address`
  Represents a Global Address resource. Global addresses are used for
  HTTP(S) load balancing.

- `gcompute_global_forwarding_rule`
  Represents a GlobalForwardingRule resource. Global forwarding rules are
  used to forward traffic to the correct load balancer for HTTP load
  balancing. Global forwarding rules can only be used for HTTP load
  balancing.
  For more information, see
  https://cloud.google.com/compute/docs/load-balancing/http/

- `gcompute_http_health_check`
  An HttpHealthCheck resource. This resource defines a template for how
  individual VMs should be checked for health, via HTTP.

- `gcompute_https_health_check`
  An HttpsHealthCheck resource. This resource defines a template for how
  individual VMs should be checked for health, via HTTPS.

- `gcompute_health_check`
  Health Checks determine whether instances are responsive and able to do work.
  They are an important part of a comprehensive load balancing configuration,
  as they enable monitoring instances behind load balancers.
  Health Checks poll instances at a specified interval. Instances that
  do not respond successfully to some number of probes in a row are marked
  as unhealthy. No new connections are sent to unhealthy instances,
  though existing connections will continue. The health check will
  continue to poll unhealthy instances. If an instance later responds
  successfully to some number of consecutive probes, it is marked
  healthy again and can receive new connections.

- `gcompute_instance_template`
  Defines an Instance Template resource that provides configuration settings
  for your virtual machine instances. Instance templates are not tied to the
  lifetime of an instance and can be used and reused as to deploy virtual
  machines. You can also use different templates to create different virtual
  machine configurations. Instance templates are required when you create a
  managed instance group.
  Tip: Disks should be set to autoDelete=true
  so that leftover disks are not left behind on machine deletion.

- `gcompute_license`
  A License resource represents a software license. Licenses are used to
  track software usage in images, persistent disks, snapshots, and virtual
  machine instances.

- `gcompute_image`
  Represents an Image resource.
  Google Compute Engine uses operating system images to create the root
  persistent disks for your instances. You specify an image when you create
  an instance. Images contain a boot loader, an operating system, and a
  root file system. Linux operating system images are also capable of
  running containers on Compute Engine.
  Images can be either public or custom.
  Public images are provided and maintained by Google, open-source
  communities, and third-party vendors. By default, all projects have
  access to these images and can use them to create instances.  Custom
  images are available only to your project. You can create a custom image
  from root persistent disks and other images. Then, use the custom image
  to create an instance.

- `gcompute_instance`
  An instance is a virtual machine (VM) hosted on Google's infrastructure.

- `gcompute_instance_group`
  Represents an Instance Group resource. Instance groups are self-managed
  and can contain identical or different instances. Instance groups do not
  use an instance template. Unlike managed instance groups, you must create
  and add instances to an instance group manually.

- `gcompute_instance_group_manager`
  Creates a managed instance group using the information that you specify in
  the request. After the group is created, it schedules an action to create
  instances in the group using the specified instance template. This
  operation is marked as DONE when the group is created even if the
  instances in the group have not yet been created. You must separately
  verify the status of the individual instances.
  A managed instance group can have up to 1000 VM instances per group.

- `gcompute_machine_type`
  Represents a MachineType resource. Machine types determine the virtualized
  hardware specifications of your virtual machine instances, such as the
  amount of memory or number of virtual CPUs.

- `gcompute_network`
  Represents a Network resource.
  Your Cloud Platform Console project can contain multiple networks, and
  each network can have multiple instances attached to it. A network allows
  you to define a gateway IP and the network range for the instances
  attached to that network. Every project is provided with a default network
  with preset configurations and firewall rules. You can choose to customize
  the default network by adding or removing rules, or you can create new
  networks in that project. Generally, most users only need one network,
  although you can have up to five networks per project by default.
  A network belongs to only one project, and each instance can only belong
  to one network. All Compute Engine networks use the IPv4 protocol. Compute
  Engine currently does not support IPv6. However, Google is a major
  advocate of IPv6 and it is an important future direction.

- `gcompute_region`
  Represents a Region resource. A region is a specific geographical
  location where you can run your resources. Each region has one or more
  zones

- `gcompute_region_disk`
  Persistent disks are durable storage devices that function similarly to
  the physical disks in a desktop or a server. Compute Engine manages the
  hardware behind these devices to ensure data redundancy and optimize
  performance for you. Persistent disks are available as either standard
  hard disk drives (HDD) or solid-state drives (SSD).
  Persistent disks are located independently from your virtual machine
  instances, so you can detach or move persistent disks to keep your data
  even after you delete your instances. Persistent disk performance scales
  automatically with size, so you can resize your existing persistent disks
  or add more persistent disks to an instance to meet your performance and
  storage space requirements.
  Add a persistent disk to your instance when you need reliable and
  affordable storage with consistent performance characteristics.

- `gcompute_route`
  Represents a Route resource.
  A route is a rule that specifies how certain packets should be handled by
  the virtual network. Routes are associated with virtual machines by tag,
  and the set of routes for a particular virtual machine is called its
  routing table. For each packet leaving a virtual machine, the system
  searches that virtual machine's routing table for a single best matching
  route.
  Routes match packets by destination IP address, preferring smaller or more
  specific ranges over larger ones. If there is a tie, the system selects
  the route with the smallest priority value. If there is still a tie, it
  uses the layer three and four packet headers to select just one of the
  remaining matching routes. The packet is then forwarded as specified by
  the next_hop field of the winning route -- either to another virtual
  machine destination, a virtual machine gateway or a Compute
  Engine-operated gateway. Packets that do not match any route in the
  sending virtual machine's routing table will be dropped.
  A Route resource must have exactly one specification of either
  nextHopGateway, nextHopInstance, nextHopIp, or nextHopVpnTunnel.

- `gcompute_router`
  Represents a Router resource.

- `gcompute_snapshot`
  Represents a Persistent Disk Snapshot resource.
  Use snapshots to back up data from your persistent disks. Snapshots are
  different from public images and custom images, which are used primarily
  to create instances or configure instance templates. Snapshots are useful
  for periodic backup of the data on your persistent disks. You can create
  snapshots from persistent disks even while they are attached to running
  instances.
  Snapshots are incremental, so you can create regular snapshots on a
  persistent disk faster and at a much lower cost than if you regularly
  created a full image of the disk.

- `gcompute_ssl_certificate`
  An SslCertificate resource. This resource provides a mechanism to upload
  an SSL key and certificate to the load balancer to serve secure
  connections from the user.

- `gcompute_subnetwork`
  A VPC network is a virtual version of the traditional physical networks
  that exist within and between physical data centers. A VPC network
  provides connectivity for your Compute Engine virtual machine (VM)
  instances, Container Engine containers, App Engine Flex services, and
  other network-related resources.
  Each GCP project contains one or more VPC networks. Each VPC network is a
  global entity spanning all GCP regions. This global VPC network allows VM
  instances and other resources to communicate with each other via internal,
  private IP addresses.
  Each VPC network is subdivided into subnets, and each subnet is contained
  within a single region. You can have more than one subnet in a region for
  a given VPC network. Each subnet has a contiguous private RFC1918 IP
  space. You create instances, containers, and the like in these subnets.
  When you create an instance, you must create it in a subnet, and the
  instance draws its internal IP address from that subnet.
  Virtual machine (VM) instances in a VPC network can communicate with
  instances in all other subnets of the same VPC network, regardless of
  region, using their RFC1918 private IP addresses. You can isolate portions
  of the network, even entire subnets, using firewall rules.

- `gcompute_target_http_proxy`
  Represents a TargetHttpProxy resource, which is used by one or more global
  forwarding rule to route incoming HTTP requests to a URL map.

- `gcompute_target_https_proxy`
  Represents a TargetHttpsProxy resource, which is used by one or more
  global forwarding rule to route incoming HTTPS requests to a URL map.

- `gcompute_target_pool`
  Represents a TargetPool resource, used for Load Balancing.

- `gcompute_target_ssl_proxy`
  Represents a TargetSslProxy resource, which is used by one or more
  global forwarding rule to route incoming SSL requests to a backend
  service.

- `gcompute_target_tcp_proxy`
  Represents a TargetTcpProxy resource, which is used by one or more
  global forwarding rule to route incoming TCP requests to a Backend
  service.

- `gcompute_target_vpn_gateway`
  Represents a VPN gateway running in GCP. This virtual device is managed
  by Google, but used only by you.

- `gcompute_url_map`
  UrlMaps are used to route requests to a backend service based on rules
  that you define for the host and path of an incoming URL.

- `gcompute_vpn_tunnel`
  VPN tunnel resource.

- `gcompute_zone`
  Represents a Zone resource.

#### Bolt Tasks


- `tasks/reset.rb`
  Resets a Google Compute Engine VM instance

- `tasks/instance.sh`
  Because sometimes you just want a quick way to get (or destroy) an instance

- `tasks/snapshot.rb`
  Create a snapshot of a Google Compute Engine Disk


### Google Container Engine
Detailed information can be found at the
[google-gcontainer][] project home page.
The list below is a summary of the supported types by the module:


- `gcontainer_cluster`
  A Google Container Engine cluster.

- `gcontainer_node_pool`
  NodePool contains the name and configuration for a cluster's node pool.
  Node pools are a set of nodes (i.e. VM's), with a common configuration and
  specification, under the control of the cluster master. They may have a
  set of Kubernetes labels applied to them, which may be used to reference
  them during pod scheduling. They may also be resized up or down, to
  accommodate the workload.

- `gcontainer_kube_config`
  Generates a compatible Kuberenetes '.kube/config' file

#### Bolt Tasks


- `tasks/resize.rb`
  Resizes a cluster container node pool


### Google Cloud DNS
Detailed information can be found at the
[google-gdns][] project home page.
The list below is a summary of the supported types by the module:


- `gdns_managed_zone`
  A zone is a subtree of the DNS namespace under one administrative
  responsibility. A ManagedZone is a resource that represents a DNS zone
  hosted by the Cloud DNS service.

- `gdns_project`
  A project resource. The project is a top level container for resources
  including Cloud DNS ManagedZones.

- `gdns_resource_record_set`
  A single DNS record that exists on a domain name (i.e. in a managed zone).
  This record defines the information about the domain and where the
  domain / subdomains direct to.
  The record will include the domain/subdomain name, a type (i.e. A, AAA,
  CAA, MX, CNAME, NS, etc)

### Google Cloud IAM
Detailed information can be found at the
[google-giam][] project home page.
The list below is a summary of the supported types by the module:


- `giam_service_account`
  A service account in the Identity and Access Management API.

- `giam_service_account_key`
  A service account in the Identity and Access Management API.

### Google Cloud Pub/Sub
Detailed information can be found at the
[google-gpubsub][] project home page.
The list below is a summary of the supported types by the module:


- `gpubsub_topic`
  A named resource to which messages are sent by publishers.

- `gpubsub_subscription`
  A named resource representing the stream of messages from a single,
  specific topic, to be delivered to the subscribing application.

#### Bolt Tasks


- `tasks/publish.rb`
  Publish a message to a specific topic.


### Google Cloud Resource Manager
Detailed information can be found at the
[google-gresourcemanager][] project home page.
The list below is a summary of the supported types by the module:


- `gresourcemanager_project`
  Represents a GCP Project. A project is a container for ACLs, APIs, App
  Engine Apps, VMs, and other Google Cloud Platform resources.

### Google Spanner
Detailed information can be found at the
[google-gspanner][] project home page.
The list below is a summary of the supported types by the module:


- `gspanner_instance_config`
  A possible configuration for a Cloud Spanner instance. Configurations
  define the geographic placement of nodes and their replication.

- `gspanner_instance`
  An isolated set of Cloud Spanner resources on which databases can be
  hosted.

- `gspanner_database`
  A Cloud Spanner Database which is hosted on a Spanner instance.

### Google Cloud SQL
Detailed information can be found at the
[google-gsql][] project home page.
The list below is a summary of the supported types by the module:


- `gsql_instance`
  Represents a Cloud SQL instance. Cloud SQL instances are SQL databases
  hosted in Google's cloud. The Instances resource provides methods for
  common configuration and management tasks.

- `gsql_database`
  Represents a SQL database inside the Cloud SQL instance, hosted in
  Google's cloud.

- `gsql_user`
  The Users resource represents a database user in a Cloud SQL instance.

- `gsql_ssl_cert`
  Represents an SSL certificate created for a Cloud SQL instance. To use the
  SSL certificate you must have the SSL Client Certificate and the
  associated SSL Client Key. The Client Key can be downloaded only when the
  SSL certificate is created with the insert method.

- `gsql_flag`
  Represents a flag that can be configured for a Cloud SQL instance.

- `gsql_tier`
  The Tiers resource represents a service configuration that can be used to
  define a Cloud SQL instance. Each tier has an associated RAM, maximum
  storage, and list of regions in which the tier can be used. Available
  tiers vary depending on whether you use PostgreSQL, MySQL Second
  Generation, or MySQL First Generation instances.

#### Bolt Tasks


- `tasks/clone.rb`
  Clone a CloudSQL database (requires backups and binary logs to be previously enabled)

- `tasks/passwd.rb`
  Allow resetting Cloud SQL password for existing users


### Google Cloud Storage
Detailed information can be found at the
[google-gstorage][] project home page.
The list below is a summary of the supported types by the module:


- `gstorage_bucket`
  The Buckets resource represents a bucket in Google Cloud Storage. There is
  a single global namespace shared by all buckets. For more information, see
  Bucket Name Requirements.
  Buckets contain objects which can be accessed by their own methods. In
  addition to the acl property, buckets contain bucketAccessControls, for
  use in fine-grained manipulation of an existing bucket's access controls.
  A bucket is always owned by the project team owners group.

- `gstorage_bucket_access_control`
  The BucketAccessControls resource represents the Access Control Lists
  (ACLs) for buckets within Google Cloud Storage. ACLs let you specify who
  has access to your data and to what extent.
  There are three roles that can be assigned to an entity:
  READERs can get the bucket, though no acl property will be returned, and
  list the bucket's objects.  WRITERs are READERs, and they can insert
  objects into the bucket and delete the bucket's objects.  OWNERs are
  WRITERs, and they can get the acl property of a bucket, update a bucket,
  and call all BucketAccessControls methods on the bucket.  For more
  information, see Access Control, with the caveat that this API uses
  READER, WRITER, and OWNER instead of READ, WRITE, and FULL_CONTROL.

- `gstorage_object_access_control`
  The ObjectAccessControls resources represent the Access Control Lists
  (ACLs) for objects within Google Cloud Storage. ACLs let you specify
  who has access to your data and to what extent.
  There are two roles that can be assigned to an entity:
  READERs can get an object, though the acl property will not be revealed.
  OWNERs are READERs, and they can get the acl property, update an object,
  and call all objectAccessControls methods on the object. The owner of an
  object is always an OWNER.
  For more information, see Access Control, with the caveat that this API
  uses READER and OWNER instead of READ and FULL_CONTROL.

- `gstorage_default_object_acl`
  The ObjectAccessControls resources represent the Access Control Lists
  (ACLs) for objects within Google Cloud Storage. ACLs let you specify
  who has access to your data and to what extent.
  There are two roles that can be assigned to an entity:
  READERs can get an object, though the acl property will not be revealed.
  OWNERs are READERs, and they can get the acl property, update an object,
  and call all objectAccessControls methods on the object. The owner of an
  object is always an OWNER.
  For more information, see Access Control, with the caveat that this API
  uses READER and OWNER instead of READ and FULL_CONTROL.

#### Bolt Tasks


- `tasks/upload.rb`
  Uploads a local file to Google Cloud Storage


### Google Authentication

This module provides the types to authenticate with Google Cloud Platform.  When
executing operations on Google Cloud Platform, e.g. creating a virtual machine,
a SQL database, etc., you need to be authenticated to be able to carry on with
the request.  All Google Cloud Platform modules use an unified authentication
mechanism, provided by this module.

For examples, installation and usage visit the [google-gauth][] module home
page.


## Supported Operating Systems

<table>
  <tr><th>Product</th><th>Operating Systems</th></tr>
  <tr>
    <td>Google Cloud BigQuery</td>
    <td>
      RedHat 6, 7<br/>
      CentOS 6, 7<br/>
      Debian 7, 8<br/>
      Ubuntu 12.04, 14.04, 16.04, 16.10<br/>
      SLES 11-sp4, 12-sp2<br/>
      openSUSE 13<br/>
      Windows Server 2008 R2, 2012 R2, 2012 R2 Core, 2016 R2, 2016 R2 Core
    </td>
  </tr>
  <tr>
    <td>Google Compute Engine</td>
    <td>
      RedHat 6, 7<br/>
      CentOS 6, 7<br/>
      Debian 7, 8<br/>
      Ubuntu 12.04, 14.04, 16.04, 16.10<br/>
      SLES 11-sp4, 12-sp2<br/>
      openSUSE 13<br/>
      Windows Server 2008 R2, 2012 R2, 2012 R2 Core, 2016 R2, 2016 R2 Core
    </td>
  </tr>
  <tr>
    <td>Google Container Engine</td>
    <td>
      RedHat 6, 7<br/>
      CentOS 6, 7<br/>
      Debian 7, 8<br/>
      Ubuntu 12.04, 14.04, 16.04, 16.10<br/>
      SLES 11-sp4, 12-sp2<br/>
      openSUSE 13<br/>
      Windows Server 2008 R2, 2012 R2, 2012 R2 Core, 2016 R2, 2016 R2 Core
    </td>
  </tr>
  <tr>
    <td>Google Cloud DNS</td>
    <td>
      RedHat 6, 7<br/>
      CentOS 6, 7<br/>
      Debian 7, 8<br/>
      Ubuntu 12.04, 14.04, 16.04, 16.10<br/>
      SLES 11-sp4, 12-sp2<br/>
      openSUSE 13<br/>
      Windows Server 2008 R2, 2012 R2, 2012 R2 Core, 2016 R2, 2016 R2 Core
    </td>
  </tr>
  <tr>
    <td>Google Cloud IAM</td>
    <td>
      RedHat 6, 7<br/>
      CentOS 6, 7<br/>
      Debian 7, 8<br/>
      Ubuntu 12.04, 14.04, 16.04, 16.10<br/>
      SLES 11-sp4, 12-sp2<br/>
      openSUSE 13<br/>
      Windows Server 2008 R2, 2012 R2, 2012 R2 Core, 2016 R2, 2016 R2 Core
    </td>
  </tr>
  <tr>
    <td>Google Cloud Pub/Sub</td>
    <td>
      RedHat 6, 7<br/>
      CentOS 6, 7<br/>
      Debian 7, 8<br/>
      Ubuntu 12.04, 14.04, 16.04, 16.10<br/>
      SLES 11-sp4, 12-sp2<br/>
      openSUSE 13<br/>
      Windows Server 2008 R2, 2012 R2, 2012 R2 Core, 2016 R2, 2016 R2 Core
    </td>
  </tr>
  <tr>
    <td>Google Cloud Resource Manager</td>
    <td>
      RedHat 6, 7<br/>
      CentOS 6, 7<br/>
      Debian 7, 8<br/>
      Ubuntu 12.04, 14.04, 16.04, 16.10<br/>
      SLES 11-sp4, 12-sp2<br/>
      openSUSE 13<br/>
      Windows Server 2008 R2, 2012 R2, 2012 R2 Core, 2016 R2, 2016 R2 Core
    </td>
  </tr>
  <tr>
    <td>Google Spanner</td>
    <td>
      RedHat 6, 7<br/>
      CentOS 6, 7<br/>
      Debian 7, 8<br/>
      Ubuntu 12.04, 14.04, 16.04, 16.10<br/>
      SLES 11-sp4, 12-sp2<br/>
      openSUSE 13<br/>
      Windows Server 2008 R2, 2012 R2, 2012 R2 Core, 2016 R2, 2016 R2 Core
    </td>
  </tr>
  <tr>
    <td>Google Cloud SQL</td>
    <td>
      RedHat 6, 7<br/>
      CentOS 6, 7<br/>
      Debian 7, 8<br/>
      Ubuntu 12.04, 14.04, 16.04, 16.10<br/>
      SLES 11-sp4, 12-sp2<br/>
      openSUSE 13<br/>
      Windows Server 2008 R2, 2012 R2, 2012 R2 Core, 2016 R2, 2016 R2 Core
    </td>
  </tr>
  <tr>
    <td>Google Cloud Storage</td>
    <td>
      RedHat 6, 7<br/>
      CentOS 6, 7<br/>
      Debian 7, 8<br/>
      Ubuntu 12.04, 14.04, 16.04, 16.10<br/>
      SLES 11-sp4, 12-sp2<br/>
      openSUSE 13<br/>
      Windows Server 2008 R2, 2012 R2, 2012 R2 Core, 2016 R2, 2016 R2 Core
    </td>
  </tr>
</table>


[supported-products]: #supported-google-cloud-platform-products
[supported-types]: #summary-of-supported-products-types--providers
[google-gbigquery]: https://github.com/GoogleCloudPlatform/puppet-google-bigquery
[google-gcompute]: https://github.com/GoogleCloudPlatform/puppet-google-compute
[google-gcontainer]: https://github.com/GoogleCloudPlatform/puppet-google-container
[google-gdns]: https://github.com/GoogleCloudPlatform/puppet-google-dns
[google-giam]: https://github.com/GoogleCloudPlatform/puppet-google-iam
[google-gpubsub]: https://github.com/GoogleCloudPlatform/puppet-google-pubsub
[google-gresourcemanager]: https://github.com/GoogleCloudPlatform/puppet-google-resourcemanager
[google-gspanner]: https://github.com/GoogleCloudPlatform/puppet-google-spanner
[google-gsql]: https://github.com/GoogleCloudPlatform/puppet-google-sql
[google-gstorage]: https://github.com/GoogleCloudPlatform/puppet-google-storage
[google-gauth]: https://github.com/GoogleCloudPlatform/puppet-google-auth/blob/master/README.md
[gcp]: https://cloud.google.com
[google-cloud-forge]: https://forge.puppet.com/google/cloud
