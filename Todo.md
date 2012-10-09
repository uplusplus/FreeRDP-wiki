# (Longterm) Tasks and Todos
* Collect ideas to ease up command line ([Command Line Interface](https://github.com/FreeRDP/FreeRDP/wiki/CommandLineInterface))
* Create test code for schannel (deeply linked with the certificate validation API)
* Create required subset of bcrypt api (http://msdn.microsoft.com/en-us/library/windows/desktop/aa376210/)
 * write stubs and tests
 * warp openssl (maybe other ssl libraries in future)
* Collect ideas and define a release management
 * stable releases should be available more often
* Create more and in depth documentation
* Replacement for current debug system/macros
 * easy to use
 * option to output to a file
 * create a wrapper printf function in winpr, probably the one from the strsafe api, which provides us with a consistent format string format