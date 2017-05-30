# openstack-heat-templates
A Collection of Openstack Heat Templates

#Cirros Simple Standalone (Heat Commandline Example)

openstack stack create --template cirros_simple_standalone.yaml \
  --parameter "image=cirros" MYSTACK
  
The command returns the following output:

+---------------------+----------------------------------------------------------------+
| Field               | Value                                                          |
+---------------------+----------------------------------------------------------------+
| id                  | 70b9feca-8f99-418e-b2f1-cc38d61b3ffb                           |
| stack_name          | MYSTACK                                                        |
| description         | The heat template is used to demo the 'console_urls' attribute |
|                     | of OS::Nova::Server.                                           |
|                     |                                                                |
| creation_time       | 2016-06-08T09:54:15                                            |
| updated_time        | None                                                           |
| stack_status        | CREATE_IN_PROGRESS                                             |
| stack_status_reason |                                                                |
+---------------------+----------------------------------------------------------------+

To explore the state and history of a particular stack, you can run a number of commands.

To see which stacks are visible to the current user, run the following command:

$ openstack stack list
+--------------------------------------+------------+-----------------+---------------------+--------------+
| ID                                   | Stack Name | Stack Status    | Creation Time       | Updated Time |
+--------------------------------------+------------+-----------------+---------------------+--------------+
| 70b9feca-8f99-418e-b2f1-cc38d61b3ffb | MYSTACK    | CREATE_COMPLETE | 2016-06-08T09:54:15 | None         |
+--------------------------------------+------------+-----------------+---------------------+--------------+
To show the details of a stack, run the following command:

$ openstack stack show MYSTACK
A stack consists of a collection of resources. To list the resources and their status, run the following command:

$ openstack stack resource list MYSTACK
+---------------+--------------------------------------+------------------+-----------------+---------------------+
| resource_name | physical_resource_id                 | resource_type    | resource_status | updated_time        |
+---------------+--------------------------------------+------------------+-----------------+---------------------+
| server        | 1b3a7c13-42be-4999-a2a1-8fbefd00062b | OS::Nova::Server | CREATE_COMPLETE | 2016-06-08T09:54:15 |
+---------------+--------------------------------------+------------------+-----------------+---------------------+
To show the details for a specific resource in a stack, run the following command:

$ openstack stack resource show MYSTACK server
Some resources have associated metadata which can change throughout the lifecycle of a resource. Show the metadata by running the following command:

$ openstack stack resource metadata MYSTACK server
A series of events is generated during the lifecycle of a stack. To display lifecycle events, run the following command:

$ openstack stack event list MYSTACK
2016-06-08 09:54:15 [MYSTACK]: CREATE_IN_PROGRESS  Stack CREATE started
2016-06-08 09:54:15 [server]: CREATE_IN_PROGRESS  state changed
2016-06-08 09:54:41 [server]: CREATE_COMPLETE  state changed
2016-06-08 09:54:41 [MYSTACK]: CREATE_COMPLETE  Stack CREATE completed successfully
To show the details for a particular event, run the following command:

$ openstack stack event show MYSTACK server EVENT
Update a stack

To update an existing stack from a modified template file, run a command like the following command:

$ openstack stack update --template cirros_simple_standalone.yaml \
  --parameter "image=ubuntu" MYSTACK
+---------------------+----------------------------------------------------------------+
| Field               | Value                                                          |
+---------------------+----------------------------------------------------------------+
| id                  | 267a459a-a8cd-4d3e-b5a1-8c08e945764f                           |
| stack_name          | mystack                                                        |
| description         | The heat template is used to demo the 'console_urls' attribute |
|                     | of OS::Nova::Server.                                           |
|                     |                                                                |
| creation_time       | 2016-06-08T09:54:15                                            |
| updated_time        | 2016-06-08T10:41:18                                            |
| stack_status        | UPDATE_IN_PROGRESS                                             |
| stack_status_reason | Stack UPDATE started                                           |
+---------------------+----------------------------------------------------------------+
