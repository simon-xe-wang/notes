### Key problems

- DTO
- Validator 
- Aggregate Root
- Value Object
- Repository
	- Repo vs DAO
	- Which layer does Repo belong to?
		- Repo interface (app or domain)
		- Repo implementation (adaptor)
	







 Repo is defined by Aggregation while DAO is defined by DB table, i.e., one repo instance per aggregation while 1 DAO instance per table.
-  Driving vs Driven
	- Application implements Driving ports (REST API, grpc API)
	- Application uses Driven ports (Repository)
	- Not completely determined by tech. For example, in event driven applications, kafka message could be both input and output
- DTO should be application layer or adapter layer, but not in domain layer
- Validator
	- business validator and arg validator
	- business validator should be in domain layer ( **Domain Service pattern** )


# Reference
- *Hexagonal Architecture* from https://web.archive.org/web/20180822100852/http://alistair.cockburn.us/Hexagonal+architecture
- https://zhuanlan.zhihu.com/p/113681224




## Demo Project (Org Management)

### Function requirements:
- add org
- org hierarchy
- validation
	- name
	- parent
	- type
	- owner
	- status is valid
### Design Requirements
- build org object
- http and grpc
- Encapsulation
- package
