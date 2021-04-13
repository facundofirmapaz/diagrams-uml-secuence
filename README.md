# diagrams-uml-secuence
Diagramas de secuencia uml de practica Quality 3



##Ejercicio 1:

sequenceDiagram

    participant RC as RestClient
    participant C as ClienteController
    participant S as ClienteService
    participant R as ClienteRepository 

    RC->>+C: POST(/clientes/crear, {ClienteDto})
    C->>-C: ValidateClienteDto
    alt ClienteDto is valid
        C->>S: newCliente(ClienteDto)
        S->>+R: newCliente(ClienteDto)
        R->>-R: newCliente
        R->>+S: ClienteDto
        S->>+C: ClienteDto
        C->>+RC: Ok(ClienteDto)
    else
        C->>RC: BadRequest(ClienteNotValidException)
    end
    
 https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoic2VxdWVuY2VEaWFncmFtXG5cbnBhcnRpY2lwYW50IFJDIGFzIFJlc3RDbGllbnRcbiAgICBwYXJ0aWNpcGFudCBDIGFzIENsaWVudGVDb250cm9sbGVyXG4gICAgcGFydGljaXBhbnQgUyBhcyBDbGllbnRlU2VydmljZVxuICAgIHBhcnRpY2lwYW50IFIgYXMgQ2xpZW50ZVJlcG9zaXRvcnkgXG5cbiAgICBSQy0-PitDOiBQT1NUKC9jbGllbnRlcy9jcmVhciwge0NsaWVudGVEdG99KVxuICAgIEMtPj4tQzogVmFsaWRhdGVDbGllbnRlRHRvXG4gICAgYWx0IENsaWVudGVEdG8gaXMgdmFsaWRcbiAgICAgICAgQy0-PlM6IG5ld0NsaWVudGUoQ2xpZW50ZUR0bylcbiAgICAgICAgUy0-PitSOiBuZXdDbGllbnRlKENsaWVudGVEdG8pXG4gICAgICAgIFItPj4tUjogbmV3Q2xpZW50ZVxuICAgICAgICBSLT4-K1M6IENsaWVudGVEdG9cbiAgICAgICAgUy0-PitDOiBDbGllbnRlRHRvXG4gICAgICAgIEMtPj4rUkM6IE9rKENsaWVudGVEdG8pXG4gICAgZWxzZVxuICAgICAgICBDLT4-UkM6IEJhZFJlcXVlc3QoQ2xpZW50ZU5vdFZhbGlkRXhjZXB0aW9uKVxuICAgIGVuZCIsIm1lcm1haWQiOnt9LCJ1cGRhdGVFZGl0b3IiOmZhbHNlfQ


##Ejercicio 2:

sequenceDiagram

    participant RC as RestClient
    participant C as ClienteController
    participant S as ClienteService
    participant R as ClienteRepository 

    RC->>+C: DELETE(/clientes/eliminar, {?username=xxxx})
    C->>-C: ValidateParameter
    alt Param is valid
        C->>S: deleteCliente(username)
        S->>+R: deleteCliente(username)
        R->>-R: deleteCliente
        alt IfExist
            R->>+S: true
            S->>+C: true
            C->>+RC: ok()
        else
            R->>+S: false
            S->>+C: false
            C->>+RC: NotFound()
        end    
    else
        C->>RC: BadRequest(ParameterNotValidException)
    end
    
 https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoic2VxdWVuY2VEaWFncmFtXG5cbnBhcnRpY2lwYW50IFJDIGFzIFJlc3RDbGllbnRcbiAgICBwYXJ0aWNpcGFudCBDIGFzIENsaWVudGVDb250cm9sbGVyXG4gICAgcGFydGljaXBhbnQgUyBhcyBDbGllbnRlU2VydmljZVxuICAgIHBhcnRpY2lwYW50IFIgYXMgQ2xpZW50ZVJlcG9zaXRvcnkgXG5cbiAgICBSQy0-PitDOiBERUxFVEUoL2NsaWVudGVzL2VsaW1pbmFyLCB7P3VzZXJuYW1lPXh4eHh9KVxuICAgIEMtPj4tQzogVmFsaWRhdGVQYXJhbWV0ZXJcbiAgICBhbHQgUGFyYW0gaXMgdmFsaWRcbiAgICAgICAgQy0-PlM6IGRlbGV0ZUNsaWVudGUodXNlcm5hbWUpXG4gICAgICAgIFMtPj4rUjogZGVsZXRlQ2xpZW50ZSh1c2VybmFtZSlcbiAgICAgICAgUi0-Pi1SOiBkZWxldGVDbGllbnRlXG4gICAgICAgIGFsdCBJZkV4aXN0XG4gICAgICAgICAgICBSLT4-K1M6IHRydWVcbiAgICAgICAgICAgIFMtPj4rQzogdHJ1ZVxuICAgICAgICAgICAgQy0-PitSQzogb2soKVxuICAgICAgICBlbHNlXG4gICAgICAgICAgICBSLT4-K1M6IGZhbHNlXG4gICAgICAgICAgICBTLT4-K0M6IGZhbHNlXG4gICAgICAgICAgICBDLT4-K1JDOiBOb3RGb3VuZCgpXG4gICAgICAgIGVuZCAgICBcbiAgICBlbHNlXG4gICAgICAgIEMtPj5SQzogQmFkUmVxdWVzdChQYXJhbWV0ZXJOb3RWYWxpZEV4Y2VwdGlvbilcbiAgICBlbmQiLCJtZXJtYWlkIjp7fSwidXBkYXRlRWRpdG9yIjpmYWxzZX0



##Ejercicio 3:


sequenceDiagram

    participant RC as RestClient
    participant C as ClienteController
    participant S as ClienteService
    participant R as ClienteRepository 

    RC->>+C: PUT(/clientes/actualizar, {ClienteDto})
    C->>-C: ValidateClienteDto
    alt ClienteDto is valid
        C->>S: updateCliente(ClienteDto)
        S->>+R: updateCliente(ClienteDto)
        R->>-R: updateCliente
        R->>+S: ClienteDto
        S->>+C: ClienteDto
        C->>+RC: Ok(ClienteDto)
    else
        C->>RC: BadRequest(ClienteNotValidException)
    end
    
https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoic2VxdWVuY2VEaWFncmFtXG5cbnBhcnRpY2lwYW50IFJDIGFzIFJlc3RDbGllbnRcbiAgICBwYXJ0aWNpcGFudCBDIGFzIENsaWVudGVDb250cm9sbGVyXG4gICAgcGFydGljaXBhbnQgUyBhcyBDbGllbnRlU2VydmljZVxuICAgIHBhcnRpY2lwYW50IFIgYXMgQ2xpZW50ZVJlcG9zaXRvcnkgXG5cbiAgICBSQy0-PitDOiBQVVQoL2NsaWVudGVzL2FjdHVhbGl6YXIsIHtDbGllbnRlRHRvfSlcbiAgICBDLT4-LUM6IFZhbGlkYXRlQ2xpZW50ZUR0b1xuICAgIGFsdCBDbGllbnRlRHRvIGlzIHZhbGlkXG4gICAgICAgIEMtPj5TOiB1cGRhdGVDbGllbnRlKENsaWVudGVEdG8pXG4gICAgICAgIFMtPj4rUjogdXBkYXRlQ2xpZW50ZShDbGllbnRlRHRvKVxuICAgICAgICBSLT4-LVI6IHVwZGF0ZUNsaWVudGVcbiAgICAgICAgUi0-PitTOiBDbGllbnRlRHRvXG4gICAgICAgIFMtPj4rQzogQ2xpZW50ZUR0b1xuICAgICAgICBDLT4-K1JDOiBPayhDbGllbnRlRHRvKVxuICAgIGVsc2VcbiAgICAgICAgQy0-PlJDOiBCYWRSZXF1ZXN0KENsaWVudGVOb3RWYWxpZEV4Y2VwdGlvbilcbiAgICBlbmQiLCJtZXJtYWlkIjp7fSwidXBkYXRlRWRpdG9yIjpmYWxzZX0



##Ejercicio 4:

sequenceDiagram

    participant RC as RestClient
    participant C as ClienteController
    participant S as ClienteService
    participant R as ClienteRepository 

    RC->>+C: GET(/clientes/buscar, {?username=xxxx})
    C->>-C: ValidateParameter
    alt Param is valid
        C->>S: getCliente(username)
        S->>+R: getCliente(username)
        R->>-R: getCliente
        alt IfExist
            R->>+S: ClienteDto
            S->>+C: ClienteDto
            C->>+RC: ok(ClienteDto)
        else
            R->>+S: null
            S->>+C: null
            C->>+RC: NotFound()
        end    
    else
        C->>RC: BadRequest(ParameterNotValidException)
    end

https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoic2VxdWVuY2VEaWFncmFtXG5cbnBhcnRpY2lwYW50IFJDIGFzIFJlc3RDbGllbnRcbnBhcnRpY2lwYW50IEMgYXMgQ2xpZW50ZUNvbnRyb2xsZXJcbnBhcnRpY2lwYW50IFMgYXMgQ2xpZW50ZVNlcnZpY2VcbnBhcnRpY2lwYW50IFIgYXMgQ2xpZW50ZVJlcG9zaXRvcnkgXG5cblJDLT4-K0M6IEdFVCgvY2xpZW50ZXMvYnVzY2FyLCB7P3VzZXJuYW1lPXh4eHh9KVxuQy0-Pi1DOiBWYWxpZGF0ZVBhcmFtZXRlclxuYWx0IFBhcmFtIGlzIHZhbGlkXG4gICAgQy0-PlM6IGdldENsaWVudGUodXNlcm5hbWUpXG4gICAgUy0-PitSOiBnZXRDbGllbnRlKHVzZXJuYW1lKVxuICAgIFItPj4tUjogZ2V0Q2xpZW50ZVxuICAgIGFsdCBJZkV4aXN0XG4gICAgICAgIFItPj4rUzogQ2xpZW50ZUR0b1xuICAgICAgICBTLT4-K0M6IENsaWVudGVEdG9cbiAgICAgICAgQy0-PitSQzogb2soQ2xpZW50ZUR0bylcbiAgICBlbHNlXG4gICAgICAgIFItPj4rUzogbnVsbFxuICAgICAgICBTLT4-K0M6IG51bGxcbiAgICAgICAgQy0-PitSQzogTm90Rm91bmQoKVxuICAgIGVuZCAgICBcbmVsc2VcbiAgICBDLT4-UkM6IEJhZFJlcXVlc3QoUGFyYW1ldGVyTm90VmFsaWRFeGNlcHRpb24pXG5lbmQiLCJtZXJtYWlkIjp7fSwidXBkYXRlRWRpdG9yIjpmYWxzZX0




##Ejercicio 5:

sequenceDiagram

    participant RC as RestClient
    participant C as ClienteController
    participant S as ClienteService
    participant R as ClienteRepository 

    RC->>+C: GET(/clientes/buscar)
    C->>S: getClientes()
    S->>+R: getClientes()
    R->>-R: getClientes()
    R->>+S: List<ClienteDto>
    S->>+C: List<ClienteDto>
    C->>+RC: ok(List<ClienteDto>)
    

https://mermaid-js.github.io/mermaid-live-editor/#/edit/eyJjb2RlIjoic2VxdWVuY2VEaWFncmFtXG5cbiAgICBwYXJ0aWNpcGFudCBSQyBhcyBSZXN0Q2xpZW50XG4gICAgcGFydGljaXBhbnQgQyBhcyBDbGllbnRlQ29udHJvbGxlclxuICAgIHBhcnRpY2lwYW50IFMgYXMgQ2xpZW50ZVNlcnZpY2VcbiAgICBwYXJ0aWNpcGFudCBSIGFzIENsaWVudGVSZXBvc2l0b3J5IFxuXG4gICAgUkMtPj4rQzogR0VUKC9jbGllbnRlcy9idXNjYXIpXG4gICAgQy0-PlM6IGdldENsaWVudGVzKClcbiAgICBTLT4-K1I6IGdldENsaWVudGVzKClcbiAgICBSLT4-LVI6IGdldENsaWVudGVzKClcbiAgICBSLT4-K1M6IExpc3Q8Q2xpZW50ZUR0bz5cbiAgICBTLT4-K0M6IExpc3Q8Q2xpZW50ZUR0bz5cbiAgICBDLT4-K1JDOiBvayhMaXN0PENsaWVudGVEdG8-KSIsIm1lcm1haWQiOnt9LCJ1cGRhdGVFZGl0b3IiOmZhbHNlfQ
