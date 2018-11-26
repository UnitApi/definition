# definition
The definition of UnitAPI: the first step to understand what is this and how i can use it


Example for unitapi.yaml


    workplace-software:
      pattern: category-name-version <- should be removed beacuse of name-type
      function: object-object-string <- should be removed beacuse of name-type
      name-type:
        category: object
        name: object
        version: string
      data:        
        ide:
          PHPstorm: latest
          Webstorm: latest
        diagram: ""
        db-connection:
          DataGrip: latest


https://github.com/BiteBit/koa-oai-router

        ErrorModel:
          type: "object"
          required:
            - "code"
            - "message"
          properties:
            code:
              type: "integer"
              format: "int32"
            message:
              type: "string"

# ./api/definitions/pets.yaml

    Pet:
      type: "object"
      allOf:
        - $ref: "#/definitions/NewPet"
        - required:
            - "id"
          properties:
            id:
              type: "integer"
              format: "int64"

    NewPet:
      type: "object"
      required:
        - "name"
      properties:
        name:
          type: "string"
        tag:
          type: "string"
