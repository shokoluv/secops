




cve-20220-24852.cpp - demonsrate improper acess via dummy_bind function. with some modifications on the channel bind methods a  mitm on a channel is possible .Mitm functionality was removed from the code , blocking the improper access would also block the potential Mitm inferred from this code ... 





Flow : 
```mermaid
graph TD;
    main-->transcieverA;
    main-->transcieverB;
    main-->transcieverA-->activate;
    main-->transcieverB-->activate;
    main-->transcieverA-->activate-->dummy_bind;
    main-->transcieverB-->activate-->dummy_bind;
    main-->transcieverA-->activate-->overflow_sctp;
    main-->transcieverB-->activate-->overflow_sctp;
    main-->transcieverA-->activate-->bind_client;
    main-->transcieverB-->activate-->bind_client;
    main-->transcieverA-->activate-->allocate_channel;
    main-->transcieverB-->activate-->allocate_channel;

    main-->transcieverA-->activate-->send_malformed_refresh;
    main-->transcieverB-->activate-->send_malformed_refresh;
    
    main-->transcieverA-->activate-->dummy_bind;
    main-->transcieverB-->activate-->dummy_bind;

    
    

```
 
