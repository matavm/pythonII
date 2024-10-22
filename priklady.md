# Priklady 22.10.2024

## Načítanie CSV dát

Tento príklad sťahuje dáta z CSV súboru na webe.

používame:
- dataclass
- requests modul
- xxx

'''python
from dataclasses import dataclass
import requests

@dataclass(frozen=True)
class User:
  id: int
  first_name: str
  last_name: str
  occupation: str

url = "https://webcode.me/users.csv"

resp = requests.get(url)
content = resp.content.decode("utf-8")

lines = content.splitlines()

users = []

for line in lines[1:-1]:
  fields = line.split(",", 3)
  fields_cleaned = fields[0], fields[1], fields[2], fields[3].replace('"', '')
  user = User(*fields_cleaned)
  users.append(user)

for user in users:
  print(users)
'''
