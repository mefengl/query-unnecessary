# query-unnecessary

```js
// https://tkdodo.eu/blog/breaking-react-querys-api-on-purpose#defining-on-demand-messages
const queryClient = new QueryClient({
  queryCache: new QueryCache({
    onError: (error, query) => {
      if (query.meta.errorMessage) {
        toast.error(query.meta.errorMessage)
      }
    },
  }),
})

export function useTodos() {
  return useQuery({
    queryKey: ['todos', 'list'],
    queryFn: fetchTodos,
    meta: {
      errorMessage: 'Failed to fetch todos',
    },
  })
}
```
