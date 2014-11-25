#AspNetAdapter

An adapter that abstracts away the complexity of the ASP.NET Request and 
Response objects.

This is currently undergoing a rebirthing process to add middleware capability 
and to tune what is already present.

Usage information will be provided at a later date.

###Usage

Write a class that implements IAspNetAdapterApplication and add in the bits to 
set the ASP.NET Adapter handler and module in your web.config.

```xml
<system.web>
	<httpHandlers>
		<add verb="*" path="*" validate="false" type="AspNetAdapter.AspNetAdapterHandler"/>
	</httpHandlers>
	<httpModules>
		<add type="AspNetAdapter.AspNetAdapterModule" name="AspNetAdapterModule" />
	</httpModules>
</system.web>
```

The IAspNetAdapterApplication provides the following method:

```csharp
 void Init(Dictionary<string, object> app, 
           Dictionary<string, object> request, 
           Action<Dictionary<string, object>> response);
```

The Init() method gets an app and request dictionary. The app dictionary 
contains callbacks for things like adding to the Session or getting something
from the Session. The request dictionary contains the information you'd 
expect from an http request and finally the response callback takes a 
dictionary with response values. All of the dictionary keys can be found in
the HttpAdapterConstants class.

Middleware:

```xml
<configSections>
	<section name="aspNetAdapter" type="AspNetAdapter.AspNetAdapterWebConfig"/>
</configSections>
<aspNetAdapter>
	<middleware>
		<add name="Foo" type="MyApp.Foo" />
	</middleware>
</aspNetAdapter>
```

Additionally to the middleware you can specify the application that implements
the IAspNetAdapterApplication interface:

```xml
<application name="Engine" type="Aurora.Engine" /> 
```

###License

GNU GPL version 3 <http://www.gnu.org/licenses/gpl-3.0.html>
```
// This program is free software: you can redistribute it and/or modify it under
// the terms of the GNU General Public License as published by the Free Software
// Foundation, either version 3 of the License, or (at your option) any later
// version.
//
// This program is distributed in the hope that it will be useful, but WITHOUT
// ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
// FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more
// details.
//
// You should have received a copy of the GNU General Public License along with
// this program.  If not, see <http://www.gnu.org/licenses/>.
```

Frank Hale &lt;frank.hale@gmail.com&gt;  
24 November 2014