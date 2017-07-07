
Google Cloud Platform for Puppet
--------------------------------

This module installs all Google modules for Puppet to allow managing
[Google Cloud Platform][gcp] resources from your Puppet environment


## Module Description

This module is a convenience to install all Google Cloud Platform modules for
Puppet with a single command. You can install them individually if you wish as
well.


## Setup

To install this module on your Puppet Master (or Puppet Client/Agent), use the
Puppet module installer:

    puppet module install google/cloud


## Supported Google Cloud Platform Products

The `google/cloud` module installs the following modules automatically:

Product                 | Puppet Module
----------------------- | --------------
Google Compute Engine   | [google-gcompute][]
Google Cloud DNS        | [google-gdns][]
Google Cloud SQL        | [google-gsql][]
Google Compute Storage  | [google-gstorage][]
Google Container Engine | [google-gcontainer][]
Google Authentication   | [google-gauth][]



## Supported Operating Systems

<table>
  <tr><th>Product</th><th>Operating Systems</th></tr>
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
    <td>Google Compute Storage</td>
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
</table>


[google-gcompute]: https://github.com/GoogleCloudPlatform/puppet-google-compute/blob/master/README.md
[google-gdns]: https://github.com/GoogleCloudPlatform/puppet-google-dns/blob/master/README.md
[google-gsql]: https://github.com/GoogleCloudPlatform/puppet-google-sql/blob/master/README.md
[google-gstorage]: https://github.com/GoogleCloudPlatform/puppet-google-storage/blob/master/README.md
[google-gcontainer]: https://github.com/GoogleCloudPlatform/puppet-google-container/blob/master/README.md
[google-gauth]: https://github.com/GoogleCloudPlatform/puppet-google-auth/blob/master/README.md
[gcp]: https://cloud.google.com
