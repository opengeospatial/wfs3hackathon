* To core spec add canonical endpoint to obtain collections w/ links to first page in collection so all data
can be traversed without need for reading the openapi document.  Something like:
```
/collections:
  [ 'myCollection': {
      'description': '<desc>',
      'firstPage': '<url to first page>',
    },
  ]
```

* As extension to core spec, add endpoint detailing how to filter/query data in the service.  Starting with
detailing available properties & how to ask for features with properties of specified value as a first step.
