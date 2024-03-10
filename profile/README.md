# CairnsGames.co.za

We used to create games :)

Now we are working on creating a free and public set of libraries to help people start and run SaaS websites. 

Our architecture works on a stach basis. Each component library builds on top of the other. This way the higher level layers can make use of the lower level layer's funtionalities.

At the bottom we have the "Tenant". A tenant is identified by an Application Id, that is used to segment data in all other layers.

Above Tenant we have Auth(entication). A user authenticates with their username/password within a Tenant. This allows users to register on multiple sites but still retian a unique identity. In the same way a user will authenticate using Google against a tenant to identify them uniquely accross all applications.

Auth is currently in development.

To register a tenant you use the third layer, membership. Membership is both a library layer and the first layer of application. The Cairnsgames membership site allows the creation of Applications and the management of users. (and will contain Feature Flags, Application settings - both overridable by User information)