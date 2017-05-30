# openstack-heat-templates
A Collection of Openstack Heat Templates

#Cirros Simple Standalone (Heat Commandline Example)

openstack stack create --template cirros_simple_standalone.yaml \
  --parameter "image=cirros" MYSTACK
  

To explore the state and history of a particular stack, you can run a number of commands.

To see which stacks are visible to the current user, run the following command:

$ openstack stack list

To show the details of a stack, run the following command:

$ openstack stack show MYSTACK
A stack consists of a collection of resources. To list the resources and their status, run the following command:

$ openstack stack resource list MYSTACK

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
