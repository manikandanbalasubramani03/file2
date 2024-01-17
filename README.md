Data Parallelism:

Generally larger the batch size and the more accurate will be get.

In this case each GPU gets a separate slice of data calculate the gradients and thise gradients were average.

So with two GPU my batch size will become 64 and for 4 128 .

By adding more GPU model is able to see more data on each training step which takes less time completion for epoch for pass through the training data.

The Input X is split in  half and the slices were sent to GPU0 and GPU1.


In this case each gpu calcualtes the same opearation but different slice of data.



Synchronous and Asynchronous Updates:  Updates can be made synchronously or asynchronously. Synchronous updates wait for the computation of the slowest computer to complete before going on to the next iteration, guaranteeing consistency of updates across all machines. On the other hand, asynchronous updates let each computer change its model parameters without waiting for other machines to finish. Asynchronous updates have the potential to increase scalability and decrease communication costs, but they can also cause problems with convergence and consistency.

RPC uses the client-server model. The requesting program is a client, and the service-providing program is the server. Like a local procedure call, an RPC is a synchronous operation requiring the requesting program to be suspended until the results of the remote procedure are returned. However, the use of lightweight processes or threads that share the same address space enables multiple RPCs to be performed concurrently.

The interface definition language (IDL) -- the specification language used to describe a software component's application programming interface (API) -- is commonly used in Remote Procedure Call software. In this case, IDL provides a bridge between the machines at either end of the link that may be using different operating systems (OSes) and computer languages.
