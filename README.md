# geo-client

Geo-client is a project for generating clients based on an OpenAPI Spec.

## Generating clients

To generate clients you need Java (>7) installed as we're basing the generation of clients upon [openapi-codegen](https://github.com/OpenAPITools/openapi-generator), which is again created and maintained in java. It is a fork from the [swagger-codegen](https://github.com/swagger-api/swagger-codegen/) which have postponed support for OpenAPI. There's also [go-swagger](https://github.com/go-swagger/go-swagger) as an alternative for creating clients for go, but as it's only go, we're using `openapi-codegen` for now.

### Prequesites

You need both Node and Java installed to use the generators.

Install the dependencies by entering

```bash
npm i
```

This will install a specific version of the openapi-generator (java) which will be used to generate the clients through npx.

### Client generation

You need to run the following command to generate a client:

```bash
npx openapi-generator generate \
    -i your-openapi.yaml \
    -g your-generator \
    -o clients/geoclient-your-language \
    -c configs/your-language-config.json
```

Ex: To run the geo OpenAPI with go as a target generator, run:

```bash
npx openapi-generator generate \
    -i example/GeoOAS3.yml \
    -g go \
    -o clients/geoclient-go \
    -c configs/go-client-config.json
```

This will generate a go client for the pet store which is the default OpenAPI example.

#### Input OpenAPI/Swagger spec

The input (`-i`) must be a valid OpenAPI (JSON or YAML) file which contains information about the API and which types and methods it exposes.

To still be able to have fun with OpenAPI 3.0 you can take inspiration from the [geo-openapi](https://ghe.telenordigital.com/iot/geo-openapi) which lets you develop your OpenAPI in version 3.0 and generate the different versions.

#### Languages

The generator (`-g`) you want to generate a client for. To see a full list of languages available, use `npx openapi-generator` which will list out the different available generators.

#### Output

The output directory (`-o`), determines where you want the clients to be generated. By default we use clients/geoclient-`name-of-language` as output to keep things tidy.

#### Configs

While a plethora of languages can be generated, every language is its own special little flower and needs some special configuration to get it to work better in its paradigm.

We have added some configurations to be used in the client generation, but if you're missing your favorite language and want to see which config parameters are available, you can run `npx openapi-generator config-help -g your-language`.
