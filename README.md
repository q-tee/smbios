# about
complete structures definitions and simple parser of the [SMBIOS](https://www.dmtf.org/standards/smbios) (System Management BIOS) information, based on the actual DMTF specification.
there's no CRT dependencies and no heap-allocations performed by the library itself.

versions of the reference DMTF specifications can be accessed with the following definitions:
- SMBIOS:
  * `Q_SMBIOS_SPECIFICATION_MAJOR`
  * `Q_SMBIOS_SPECIFICATION_MINOR`
  * `Q_SMBIOS_SPECIFICATION_PATCH`
- MCTP:
  * `Q_SMBIOS_MCTP_SPECIFICATION_MAJOR`
  * `Q_SMBIOS_MCTP_SPECIFICATION_MINOR`
  * `Q_SMBIOS_MCTP_SPECIFICATION_PATCH`
- Redfish:
  * `Q_SMBIOS_REDFISH_SPECIFICATION_MAJOR`
  * `Q_SMBIOS_REDFISH_SPECIFICATION_MINOR`
  * `Q_SMBIOS_REDFISH_SPECIFICATION_PATCH`

# usage
library does provide single function to iterate structure table.
more details about usage can be found at [examples/smbios-dump](https://github.com/q-tee/examples/) page.

iterate structure table:
```cpp
// extract the structures table from the entry point
// ...

// strings table of the current structure
const char* arrStringMap[256];
// count of the strings present in the current structure
std::size_t nStringCount;
const SMBIOS::StructureHeader_t* pNextStructure = pFirstStructure;
do
{
	const SMBIOS::StructureHeader_t* pCurrentStructure = pNextStructure;
	
	// advance to the next structure
	pNextStructure = SMBIOS::ReadStructure(pCurrentStructure, arrStringMap, &nStringCount);

	// process the current structure
	// ...
} while (pNextStructure != nullptr);
```

# further information
requires [common](https://github.com/q-tee/common/) library to be also installed.
you can read about installation, contributing and look for other general information on the [q-tee](https://github.com/q-tee/) main page.