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



##Ejercicio 4:

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
    
    
    
