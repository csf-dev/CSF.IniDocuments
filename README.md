# Deprecated
This codebase is no longer maintained and will not be updated in future. For reading and writing of INI files, please consider [this library](https://github.com/rickyah/ini-parser) instead.

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
## Open source license
All source files within this project are released as open source software,
under the terms of [the MIT license].

[the MIT license]: http://opensource.org/licenses/MIT

This software is distributed in the hope that it will be useful, but please
remember that:

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
