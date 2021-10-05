# Level zero loader changelog

## v1.5.0
* Added Intel VPU driver to Linux known driver list
* Fixed default symbol visibility in Linux builds
* Added zeInit call earlier in loader init path to prevent loading drivers that don't match the ze_init_flags_t
* Fixed build for certain SLES distros
* Fixed bug that prevented tracers from being reenabled after being disabled. 
* Multi Driver Support: Return success if initialization of at least one driver succeeds. 
* Updated L0 API headers to 1.2.43 which includes:
  * Clarification to documentation of several APIs
  * Added missing STYPE ZE_STRUCTURE_TYPE_IMAGE_MEMORY_EXP_PROPERTIES
  * Added new experimental metrics extension to retrieve multiple metrics values

## v1.4.1
* Added support for Level Zero Specification 1.2.13
* Fixed a bug that resulted in zeInit failing when multiple drivers are discovered and one of them fails to load. 

## v1.3.7
* Fixed build warnings generated when `-Wall` is enabled

## v1.3.6
* New Tracing Layer APIs to support tracing Level Zero core APIs introduced after the 1.0 Specification. A change of design was needed to allow extension to new APIs without breaking backwards compatibility of original tracing APIs. The original tracing layer APIs will continue to be supported for 1.0 core APIs, but users are encouraged to switch to the new tracing layer APIs. 
* New Loader API to retrieve version information of loader and layers: `zelLoaderGetVersions`
* Enabled discovery of Level Zero Compute Accelerators Drivers on windows
* Bug Fixes:
  * Fixed loader bug that could cause corruption of handles when there are multiple drivers loaded. 
  * Corrected version check in layers to future-proof compatibility checks


## v1.2.3
* Support for the new 1.1 Level Zero Specification
* Improved library variable lifetime management by initializing variables at load time rather than as static globals. 
* Added environment variable that allows optionally specifying runtime drivers to use on Linux
* Note: Tracing Layer support is not yet available for the APIs newly introduced in the 1.1 spec. Tracing layer support for all other APIs remains functional. 



## v1.1.0
Note: Level Zero Specification API did not change.

* Update loader library to 1.1.0 to indicate addition of tracing layer implementation and associated APIs
* Fixed bug when reading windows environment variables set by process before zeInit call. Before variables were not read correctly resulting in layers not being enabled as expected
* Fixed bug in loader when using multiple drivers and a driver API returns an error code. Previously loader would incorrectly translate output handles from failed API calls
* Deprecated a tracing implementation layer descriptor enum value due to incorrect name and added a replacement.