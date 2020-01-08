<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at
      http://www.apache.org/licenses/LICENSE-2.0
  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
[<img src="https://nifi.apache.org/assets/images/apache-nifi-logo.svg" width="300" height="126" alt="Apache NiFi"/>][nifi]

This is a split off of the [MarkLogic NIFI Incubator](https://github.com/marklogic-community/marklogic-nifi-incubator) repo which only contains the marklogic specific bundle

If you want to build this marklogic nar bundle for a specific version of Apache NiFi you need to adjust the nifi.version property in the main pom file.  
For now this is set to 1.10.0
Be advised! You need java 11 or up!

To build:
- Execute `mvn clean install` or for parallel build execute `mvn -T 2.0C clean install`. On a
  modest development laptop that is a couple of years old, the latter build takes a couple of seconds.
  After a large amount of output you should eventually see a success message.

        $ mvn -T 2.0C clean install
        [INFO] Scanning for projects...
        [INFO] Inspecting build with total of 7 modules
            ...couple of hunderd of lines elided...
        [INFO] Reactor Summary for nifi-marklogic-bundle 1.10.0-incubator:
        [INFO]
        [INFO] nifi-marklogic-bundle .............................. SUCCESS [  1.672 s]
        [INFO] nifi-marklogic-services-api ........................ SUCCESS [  1.695 s]
        [INFO] nifi-marklogic-services-api-nar .................... SUCCESS [  0.887 s]
        [INFO] nifi-marklogic-services ............................ SUCCESS [  4.413 s]
        [INFO] nifi-marklogic-processors .......................... SUCCESS [  7.489 s]
        [INFO] nifi-marklogic-nar ................................. SUCCESS [  1.752 s]
        [INFO] nifi-marklogic-services-nar ........................ SUCCESS [  1.229 s]
        [INFO] ------------------------------------------------------------------------
        [INFO] BUILD SUCCESS
        [INFO] ------------------------------------------------------------------------
        [INFO] Total time:  18.512 s (Wall Clock)
        [INFO] Finished at: 2020-01-08T12:20:28+01:00
        [INFO] ------------------------------------------------------------------------
        
- Execute `mvn clean install -DskipTests` to compile tests, but skip running them.

To deploy:
- Copy nifi-marklogic-nar/target/nifi-marklogic-nar-[version].nar to .../nifi-1.10.0/lib.
- Copy nifi-marklogic-services-api-nar/target/nifi-marklogic-services-api-nar-[version].nar to .../nifi-1.10.0/lib.
- Restart nifi

