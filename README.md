# sampleCode
This component is a sample code to edit or modify the DSR using python3

## How to make a AGMAgent component

sampleCode.cdsl
```
Component sampleCode
{
    Communications
    {
        
    };
    language Python;
    options agmagent;
};
```
`make sure the options agmagent will be there.`

You can clone this repository or make your own component.

## Configuration parameters
As any other component, *sampleCode* needs a configuration file to start. In
```
etc/config
```
you can find an example of a configuration file. We can find there the following lines:
```
# Endpoints for implements interfaces
AGMCommonBehavior.Endpoints=tcp -p 45678

# Endpoints for subscriptions interfaces
AGMExecutiveTopicTopic.Endpoints=tcp -p 3127

# Proxies for required interfaces
AGMExecutiveProxy = agmexecutive:tcp -h localhost -p 10198

# This property is used by the clients to connect to IceStorm.
TopicManager.Proxy=IceStorm/TopicManager:default -p 9999

Ice.Warn.Connections=0
Ice.Trace.Network=0
Ice.Trace.Protocol=0
```

## Starting the component
Before starting the component make sure the rcnode, AGMExecutive and RCIS is running.\
To know how to start these component use this [link]().


Go to the component path using the following command
```
cd <sampleCode's path> 
```

After editing the new config file we can run the component:

```
python3 src/sampleCode.py etc/config
```
## About the sampleCode
make sure $ROBOCOMP environment variable is set.
* the function ***self.addNode()*** will add a node in the DSR.
* the function ***self.addLink()*** will add a link between two node in the DSR.
* After making change to the local Graph, the function
***self.updatingDSR()*** will update the DSR with the local Graph.
* There are many more functions that you can use, to view all the functions go to 
`/usr/local/share/agm/AGGL.py`\
you can see these function inside the **AGMGraph class**.

