# INI document reader and writer
This is a very simple API, exposing functionality for reading and writing INI
documents (typically to & from files).

The primary class of interest is **`CSF.IniDocuments.IniDocument`**.
It has static methods for reading from a file, stream or string.
It then exposes functionality to examine/modify its contents (key/value pairs),
including INI sections (marked by `[section_name]` in the source file).
You may then `Write` the document back to a file, stream or string using an
appropriate method.

## Example
Here is a simple usage example, it should be enough to get you going:

```csharp
using CSF.IniDocuments;
using System.IO;

var myIniFile = IniDocument.Read(new FileInfo(@"C:\Path\To\File.ini"));

// Read the value for key "foo", outside of any section
var fooValue = myIniFile["foo"];

// Set the value for key "bar", outside of any section
myIniFile["bar"] = "baz";

// Get the value for key "foo" inside the "sample" section
var sampleFooValue = myIniFile.Sections["sample"]["foo"];

// Set the value for key "bar", inside the "sample" section
myIniFile.Sections["sample"]["bar"] = "biz";

// Add a section
myIniFile.Sections.Add("new", new IniSection());

// Remove a section
myIniFile.Sections.Remove("old");

// Write the file to disk
myIniFile.Write(@"C:\Path\To\NewFile.ini");
```
