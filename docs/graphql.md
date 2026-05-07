<h1 align="center">GraphQL</h1>

<br>

### Introspection Query

```bash
# On browser
https://example.com/api/graphql?query={ __schema { types { name } } }

# On shell
curl 'https://example.com/api/graphql' \
-H 'Content-Type: application/json' \
--data '{"query": "{ __schema { types { name } } }"}'
```
