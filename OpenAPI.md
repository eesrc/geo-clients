# OpenAPI

OpenAPI Specification (OAS) is a specification standard to represent a public accessible API. By creating a specification, we can generate clients and API documentation "for free" using [SwaggerUI](https://swagger.io/tools/swagger-ui/) and [ReDoc](https://github.com/Redocly/redoc).

The file `GeoOAS3.yml` is the main file to edit when developing on OAS. We're adhering to the OAS 3.0 spec, which while published a while ago, has gotten a bit of a slow traction (think Python2/3). For that case, we run a conversion to both OAS 3.0 [json|yaml] as well as Swagger 2.0 [json|yaml] so anyone can consume the version they want.

![Example of generated ReDoc](/example.png "Example of generated ReDoc")

## How to develop

The project requires Node >`v12.x.x` to work.

### Install dependencies

Run `npm i` to install OAS dependencies.

### Serve doc

Run `npm start` to start a server which serves Redoc with the `GeoOAS3.yml` file. The server is hosted on port `8080`. It will continously check the OpenAPI document for errors and report when something is wrong. Upon change and no error, it will recreate the ReDoc page.

### Build

Run `npm build` to both bundle (see [Bundle](#bundle)) as well as generate OpenAPI/Swagger2.0 specs (see [Generate the different specs](#generate-the-different-specs)).

### Bundle

Run `npm run bundle` to bundle a dependency-free ReDoc page where everything is bundled included the OpenAPI Spec.

### Generate the different specs

As mentioned in the intro, there's varied support for OAS 3.0. To get around this we generate several different versions of the OAS/Swagger so everyone is happy.

Run `npm run generate` to generate OAS3 with YAML and JSON and Swagger 2.0 with YAML and JSON.

### Validate spec

Run `npm run validate` to explicitly validate the OAS document. It will give warnings and errors based on the OAS spec.

## Tools

If you're using VSCode, the [OAS Extension](https://marketplace.visualstudio.com/items?itemName=42Crunch.vscode-openapi) is a necessity to develop OpenAPI as it shows errors and has autocomplete which adheres to the standard.