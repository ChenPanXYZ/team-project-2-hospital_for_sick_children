# Records API

## Path: ```/records```

## Related Model: [records](../models/records.md)

## Supported HTTP Verbs: ```GET```, ```POST```, ```PUT```, ```PATCH```, ```DELETE```

## Supported Socket Methods: ```find()```, ```get()```, ```create()```, ```update()```, ```patch()```, ```remove()```

### ```GET``` / ```find()```:

request:
Does not have a body

response:
```json
[
  {
    "id": RECORD_ID,
    "condition": [
      true / false,
      true / false,
      true / false
    ],
    "pcomment": null / SOME_WORDS,
    "ccomment": null / SOME_WORDS,
    "patient_id": USERID,
    "createdAt": TIMESTAMP,
    "updatedAt": TIMESTAMP
  }, ...
] -- a list of records models
```

### ```GET``` / ```get()``` and ```DELETE``` / ```remove()```:

request: ```?id=RECORD_ID```, does not have a body

response:
```json
[
  {
    "id": RECORD_ID,
    "condition": [
      true / false,
      true / false,
      true / false
    ],
    "pcomment": null / SOME_WORDS,
    "ccomment": null / SOME_WORDS,
    "patient_id": USERID,
    "createdAt": TIMESTAMP,
    "updatedAt": TIMESTAMP
  }
] -- though a list, it only contains one records model
```

### ```POST``` / ```create()```:

request:
```json
{
  "condition": [
    true / false,
    true / false,
    true / false
  ],
  "uri": URI, -- the data uri
  "pcomment": SOME_WORDS, -- optional, null by default
  "ccomment": SOME_WORDS -- optional, null by default
}
```

response:
```json
{
  "id": RECORD_ID,
  "condition": [
    true / false,
    true / false,
    true / false
  ],
  "pcomment": null / SOME_WORDS,
  "ccomment": null / SOME_WORDS,
  "patient_id": USERID,
  "createdAt": TIMESTAMP,
  "updatedAt": TIMESTAMP
} -- only a simple records model
```

### ```PUT``` / ```update()``` and ```PATCH``` / ```patch()```:

request: ```?id=RECORD_ID```, body same as ```POST``` / ```create()```

response: same as ```POST``` / ```create()```


## Additional Notes:

1. **MUST** include data uri while creating a new record
2. Audio file will be automatically generated by the given uri without additional api call
3. the audio file that has been generated will be named as RECORD_ID.wav