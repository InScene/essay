# Third-Party libraries

[License checklist](https://www.osadl.org/Access-to-raw-data.oss-compliance-raw-data-access.0.html) encode license obligations in clearly defined language elements (e.g. YOU MUST), actions (e.g. Provide) and terms (e.g. Copyright notice).
 
Specific optional features are dependent on third-party libraries. 
Any third-party library which may be used is inside this `/deps` folder.

Anyways you should make sure that the corresponding third-party license matches your needs.

 - [opcua-z](#opcua-z)
 - [Open62541](#open62541)
 - [Android](#android)


## <a name="opcua-z"></a> opcua-z

| Component       | Licensor           | License          |  Description                                  |  Website                                      |
|-----------------|--------------------|------------------|-----------------------------------------------|-----------------------------------------------|
| pcre-8.44       | PERL               | BSD 3-Clause     | regex library.                                | https://ftp.pcre.org/pub/pcre                 |
| pcre2-10.36     | PERL               | BSD 3-Clause     | regex library.                                | https://ftp.pcre.org/pub/pcre                 |
| mxml-3.1        | Michael R Sweet    | Apache-2.0       | Tiny XML library.                             | https://github.com/michaelrsweet/mxml         |
| mbedtls         | Arm Mbed           | Apache-2.0       | An SSL library.                               | https://github.com/ARMmbed/mbedtls            |

## <a name="open62541"></a> Open62541
Up to now all these libraries have a less strict License compared to MPL 2.0.

| Component       | Licensor           | License          |  Description                                  |  Website                                      |
|-----------------|--------------------|------------------|-----------------------------------------------|-----------------------------------------------|
| jsmn            |                    | MIT              | json parser                                   |                                               |
| mdnsd           |                    | BSD 3-Clause     | mDNS library                                  |                                               |
| ua-nodeset      |                    | MIT              | Official OPC UA Nodeset files by the OPCF     |                                               |
| atoi            |                    | MIT              | char to int conversion                        |                                               |
| base64          |                    | BSD              | Base64 encoding and decoding                  |                                               |
| itoa            |                    | MIT              | int to char conversion                        |                                               |
| ms_stdint       |                    | BSD 3-Clause     | Replacement for stdint on older Visual Studio |                                               |
| open62541_queue |                    | BSD 3-Clause     | FIFO and LIFO queue implementation            |                                               |
| pcg_basic       |                    | Apache-2.0      | Random Number Generation                       |                                               |
| string_escape   |                    | MIT              | utf8 encoding and decoding                    |                                               |
| ziptree         |                    | MPL 2.0          | Reusable zip tree implementation              |                                               |

## <a name="android"></a> Android

| Component       | Licensor           | License          |  Description                                  |  Website                                      |
|-----------------|--------------------|------------------|-----------------------------------------------|-----------------------------------------------|
| Ktlint Gradle   | Jonathan Leitschuh | MIT              | Kotlin linter                                 | https://github.com/JLLeitschuh/ktlint-gradle  |
