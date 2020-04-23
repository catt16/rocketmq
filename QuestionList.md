## 1. Q: After calling resetOffsetByTime, all the messages are marked as unconsumed. But those messages could not be consumed as expected. 

    mqadmin resetOffsetByTime -n ***:9876 -g A_Test_SubGroup -t A_Test_Topic -f true -s 1536820000

** A: The root cause is the messages are not in commit log any more. They are removed after the fileReservedTime interval:

    deleteWhen=04
    fileReservedTime=48
