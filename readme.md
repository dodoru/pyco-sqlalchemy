
# pyco-sqlalchemy

Using `CoModel` to make SqlAlchemy's ORM even simpler for humans, develop with Flask/Django/OtherWebFrames. 

note: 不管在使用任何 web 框架, 我都希望能有统一的 ORM 查询接口, 且易于在不同的数据库间迁移.  


## install

pip install pyco-sqlalchemy


## Tips:
- use `charset=UTF8MB4 collate utf8_general_ci`

  - refer: [What's the difference between utf8_general_ci and utf8_unicode_ci?](https://stackoverflow.com/questions/766809/whats-the-difference-between-utf8-general-ci-and-utf8-unicode-ci)
  

## Samples

- flask

```python
from pyco_sqlalchemy._flask import BaseModel, db

class User(db.Model, BaseModel):
    id = db.Column(db.Integer, primary_key=True, autoincrement=True)
    name = db.Column(db.String(32))
    email = db.Column(db.String(64), unique=True)
     

form = dict(name="dev")
u1 = User.insert(form, email="dev@pypi.com")
u3 = User.upsert_one(form, email="dev@oncode.cc")
assert u1.id == u3.id

```
