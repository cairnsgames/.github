# CairnsGames.co.za

We used to create games :)

Now we are working on creating a free and public set of libraries to help people start and run SaaS websites. 

Our architecture works on a stach basis. Each component library builds on top of the other. This way the higher level layers can make use of the lower level layer's funtionalities.

At the bottom we have the "Tenant". A tenant is identified by an Application Id, that is used to segment data in all other layers.

Above Tenant we have Auth(entication). A user authenticates with their username/password within a Tenant. This allows users to register on multiple sites but still retian a unique identity. In the same way a user will authenticate using Google against a tenant to identify them uniquely accross all applications.

Auth is currently in development.

To register a tenant you use the third layer, membership. Membership is both a library layer and the first layer of application. The Cairnsgames membership site allows the creation of Applications and the management of users. (and will contain Feature Flags, Application settings - both overridable by User information)

## Library Repository

A library is a repository that contains

1. A library\* folder, this is a normal Nnpmjs library that can be installed form Github
2. A packages\* folder that is a Module Federation version of the library. This can be installed using module federation and in this way the latest version is always presented

The packages folder (as a standard) is the same name as the library suffixed with mf (for Module Federation).

The Packages folder also acts as a demo of the library, or alternatly the application that supports the library. As an example membershipmf is the actual application to manage Applications and Memberships.

## Styling

Examples and Applications all use Bootstrap, react-bootstrap and sass for styling.

Icons, we use react-bootstrap-icons. As an optimisation icons should be created as components in the repository. But during development we just import the whole library.

## State Management

We use react context for state management. Each library is expected to expose a provider that is imported in the application. We do not use useContext, instead we create subject hooks that expose the functionality for a set of data.

e.g. useTenant exposes the context data for tenants.

## Deployment

All code is built and deployed using GitHub actions.

- Organisation Variables are used for public information
- Organisation secrets are used for Passwords
- Repository variables are used for values specific to the repo (e.g. Folder names) 

## Application Repository

An application is a Module Federation how that imports the Module Federation libraries above.

## Default Ports

Default ports when working locally to allow multiple Module Federation apps to run locally.

- Tenant: 3051
- Auth: 3052
- Membership: 3053
