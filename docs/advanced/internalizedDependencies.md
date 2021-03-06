---
layout: docs-default
---

#Internalized dependencies

An interesting aspect about how IdentityServer v3 is architected and built is that all dependencies other than those in the .NET framework are internalized. This means during our build we IL-rewrite all the dependent assemblies into the IdentityServer.Core.dll assembly itself. This means our use of ASP.NET Web API, JSON.NET, Autofac, Katana, Cookie middleware, etc. are all internalized. This avoids conflicts when an application uses IdentityServer and then Web API itself – our internalized Web API will not conflict with the version being used by the hosting application.