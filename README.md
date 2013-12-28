#AspNetAdapter

An adapter that abstracts away the complexity of the ASP.NET Request and Response objects.
Applications using this library simply implement a simple interface to gain access to 
the request and response dictionaries.

```csharp
public interface IAspNetAdapterApplication
{
	void Init(Dictionary<string, object> app,
						Dictionary<string, object> request,
						Action<Dictionary<string, object>> response);
}
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

Frank Hale <frank.hale@gmail.com>
2013