### jsonnet
---
https://jsonnet.org/

```json
{
  person1: {
    name: "Alice",
    welcome: "Hello " + self.name + "!",
  },
  person2: self.person1 { name: "Bob" },
}
```

```js
local application = 'my-app';
local module = 'uwsgi_module';
local dir = '';
local permission = 644;

{
  '': std.manifestIni({
  
  }),
  'init.sh': |||
    #!/bin/bash
    mkdir -p %(dir)s
    touch %(dir)s/initialized
    chomd %(perm)d %(dir)s/initialized
  ||| % {dir: dir, perm: permission},
  
  'cassandra.conf': std.manifestYamlDoc({
    cluster_name: application,
    seed_provider: [
      {
        class_name: 'SimpleSeedProvider',
        parameters: [{ seeds: '127.0.0.1' }],
      },
    ],
  }),
}
```

```
```


