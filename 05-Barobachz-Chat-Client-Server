## `xmlrpc messageboard of "barobachz"

### create a user

```python
import barobachz 

status = barobachz.client.register(username="s.hedayat", password="theBlindAnonymousOwl")
print(status)
```

### log-in as user

```python
import barobachz 

cli = barobachz.client.login(user="s.hedayat", password="theBlindAnonymousOwl")
cli.send("here are certain sores in life that,")
cli.send("like a canker, gnaw at the soul in solitude and diminish it.")
```

### update (get `new` messages from `barobachz`)

```python
import barobachz 

cli = barobachz.client.login(user="s.hedayat", password="theBlindAnonymousOwl")
messages = cli.update()

for user, dtime, msg from messages:
    print(f"[{dtime}] @{user} : {msg}")
```


## implement an sqlite db


## a bit cooler w/ Flask

