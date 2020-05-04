# schema
The schema file, models for each type of object: Credentials, Device (IoT), ... The object provides metadata about the API

How to define config for apiunit in languages: js, nodejs, php, python, ...


## Environment/Tier 

### Local                
  	Developer's 
  	desktop/workstation
### Development/Trunk   
  |	Development server acting as a sandbox where unit testing may be performed by the developer
### Integration 
	CI build target, or for developer testing of side effects
### Testing/Test/QC/Internal Acceptance 
	The environment where interface testing is performed. A quality control team ensures that the new code will not have any impact on the existing functionality and tests major functionalities of the system after deploying the new code in the test environment.
### Staging/Stage/Model/Pre-production/External-Client Acceptance/Demo 
	Mirror of production environment
### Production/Live       
 	Serves end-users/clients 


## Another standards
http://json-schema.org/

Quickstart

The JSON document being validated or described we call the instance, and the document containing the description is called the schema.

The most basic schema is a blank JSON object, which constrains nothing, allows anything, and describes nothing:

    {}

You can apply constraints on an instance by adding validation keywords to the schema. For example, the “type” keyword can be used to restrict an instance to an object, array, string, number, boolean, or null:

    { "type": "string" }

JSON Schema is hypermedia ready, and ideal for annotating your existing JSON-based HTTP API. JSON Schema documents are identified by URIs, which can be used in HTTP Link headers, and inside JSON Schema documents to allow recursive definitions.


## Interfaces from Typoscript for define the types
https://code.visualstudio.com/docs/languages/typescript

Generates TypeScript definition file(d.ts) from swagger.json

https://github.com/mstssk/sw2dts



## Data Types on swagger

Primitive data types in the OAS are based on the types supported by the JSON Schema Specification Wright Draft 00. Note that integer as a type is also supported and is defined as a JSON number without a fraction or exponent part. null is not supported as a type (see nullable for an alternative solution). Models are defined using the Schema Object, which is an extended subset of JSON Schema Specification Wright Draft 00.

The formats defined by the OAS are:

        type 	format 	Comments
        integer 	int32 	signed 32 bits
        integer 	int64 	signed 64 bits (a.k.a long)
        number 	float 	
        number 	double 	
        string 		
        string 	byte 	base64 encoded characters
        string 	binary 	any sequence of octets
        boolean 		
        string 	date 	As defined by full-date - RFC3339
        string 	date-time 	As defined by date-time - RFC3339
        string 	password 	A hint to UIs to obscure input.



## Struktura:

### Pliki: skrypty, stale, zmienne srodowiskowe
  ukladane w odniesieniu do systemu
  
  
### Zmienne w zaleznosci od systemu

+ os
  + win
    + bash
      config.yaml / default.yaml
        extension = sh
        
### pobranie zmiennej z config do uzycia w pliku apicra.yaml

    {os.bash.config.extension}
    {os.bash.default.extension}
    

## Example config:
[unitapi](https://github.com/UnitApi/examples/blob/master/unitapi.yaml)
    

    to jest truktura danych i skryptow
    jeden moze wywolywac drugi
    moga sie zapetlac

    simple unitApi:
      version: 1.1.0
      install:
      - {ssh.local} {project.path} {cmd.mysql.restore_from_test}
      - {ssh.test} {project.path} {cmd.mysql.backup}
      - {ssh.live} {project.path} {cmd.mysql.backup}

      xampp:    
        path: "c:/xampp"      
        ssh:
          type: 'docker_name'
          credentials:
        db:
          type: 'mysql'
          credentials: "keepass.file"
          backup: {ssh.local} \ {xampp.path} \ backup.bat
          restore: {ssh.local} \ {local.path} \ restore.bat

      docker:
        path: 
          html: "c:/"      
        ssh:
          type: 'docker_name'
          credentials:
        db:
          type: 'mysql'
          credentials: "keepass.file"
          backup: {ssh.local} {local.path} backup.sh
          restore: {ssh.local} {local.path} backup.sh
            - 
      test:
        path: "/"
        ssh: 'ssh credentials'
      live:
        path: "var/www"
        ssh: 'ssh credentials'
      backup:
        path: "var/www"
        ssh: 'ssh credentials'


