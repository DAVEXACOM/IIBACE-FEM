# IIBACE-FEM
IBM Integration Bus    - Failed Event Management (FEM) Utility
App Connect Enterprise - Failed Event Management (FEM) Utility

Update

ACE11005 folder added with collaterial imported and updated to ACE v11.0.0.5
The Key file is the server.conf.yaml file.
I have created this collateral based on an independent integration server called FEMServer.
I have not yet updated the documentation, but I have added to FEMScripts folder the commands I ran to create and configure the FEMServer
The record and replay tables etc in my testing were in database MBRECORD which differs in name from FEMDB
The integration server had a default queue manager called FEMQM

Description

The IBM Integration Bus (IIB) v9.0 Failed Event Management Utility (FEMU) facilitates the capture and store for resubmission of events (or messages) that for whatever reason an IIB message flow cannot deliver. The failure may be due to a transient problem with the network or a failure to validate the data content of the message for example.
Based on a group identifier (an employee id for example) the FEMU will also manage events (or messages) that are related to the original failure by queuing those messages (in order) until some resubmission action is taken against the original failure.
This means by identifying how messages are grouped, related messages can be managed and kept in order by that group identifier even in the case of a failure, whilst messages with a different value for that group identifier continue to flow uninterrupted.
The IBM products, WebSphere Process Server and WebSphere Enterprise Service Bus had a component called the Failed Event Manager that provided this style of failure management.

The operational tooling is facilitated by the IIB Record and Replay capability. A FEMToolingWrapper subflow is supplied to wrapper the runtime FEMU subflows enabling resubmission of failed events via the IIB Web GUI.

Supported re-submission options are:

1.	ReplayOnly: Replay the original failed event directing it to is original out path and release all blocked events of the same GroupID to the original out path
2.	RedirectFirstOnly: Redirect the original failed event to an alternative out path and release all blocked events of the same GroupID to the original out path
3.	RedirectAll: Redirect the original failed event and all blocked events of the same GroupID to the alternative out path. 			
4.	RedirectAllPermanent: Redirect the original failed event, all blocked events of the same GroupID and any new events of the same GroupID to the alternative out path
5.	ClearRedirectAllPerm:  Manually clear the RedirectAllPermanent for the GroupID - this function does not propagate the event to an out path.

Detailed documentation can be found in the PDFs located in the FEMDocumentation folder.
Sample test data and a harness to drive it are provided.
Sample scripts for the set up of IIB Record and Replay and a test MQ environment are provided

If you wish to contribute please email Dave - davearno@au1.ibm.com