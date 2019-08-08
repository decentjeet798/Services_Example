# Services_Example
Service Example


A service is a component which runs in the background without direct interaction with the user. As the service has no user interface, it is not bound to the lifecycle of an activity.

Services are used for repetitive and potentially long running operations, i.e., Internet downloads, checking for new data, data processing, updating content providers and the like.

Services run with a higher priority than inactive or invisible activities and therefore it is less likely that the Android system terminates them. Services can also be configured to be restarted if they get terminated by the Android system once sufficient system resources are available again.

It is possible to assign services the same priority as foreground activities. In this case it is required to have a visible notification active for the related service. It is frequently used for services which play videos or music







To create service we will create a normal class extending the class Service. And we should override the following methods.

## onStartCommand()

This method is invoked when the service is started using the startService() method. We can call the method startService() from any activity and it will request the service to start.
## onBind()

If it is needed to bind the service with an activity this method is called. The service can result back something to the activity after binding. But if you do not want to bind the service with activity then you should return null on this method.
## onCreate()

This method is called when the service is created.
## onDestroy()

When the service is no longer used and destroyed this method is called by the system.





By default, a service runs in the same process as the main thread of the application.

Therefore, you need to use asynchronous processing in the service to perform resource intensive tasks in the background. A commonly used pattern for a service implementation is to create and run a new Thread in the service to perform the processing in the background and then to terminate the service once it has finished the processing.

Services which run in the process of the application are sometimes called local services




Service.START_STICKY

Service is restarted if it gets terminated. Intent data passed to the onStartCommand method is null. Used for services which manages their own state and do not depend on the Intent data.

Service.START_NOT_STICKY

Service is not restarted. Used for services which are periodically triggered anyway. The service is only restarted if the runtime has pending startService() calls since the service termination.

Service.START_REDELIVER_INTENT

Similar to Service.START_STICKY but the original Intent is re-delivered to the onStartCommand method.





Stopping a service
You stop a service via the stopService() method. No matter how frequently you called the startService(intent) method, one call to the stopService() method stops the service.

A service can terminate itself by calling the stopSelf() method. This is typically done if the service finishes its work
