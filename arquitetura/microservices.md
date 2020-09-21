## What are microservices?

"Microservices are small autonomous services that work together"

- Independent processes
- Communicate over APIs, events ou messages
- High degree of autonomy
- Small, focused on doing one thing well

SOA: service oriented architecture

Microservice should be focused on doing one thing and doing one thing well that allow for independent change.

## What are the advantages of microservices?

- organisational aligment: alinhar a organização com a arquitetura e vice-versa
- ship features faster, and safer : mudanças mais seguras, não é necessário testar todo o monilito, somente a parte alterada
- independent scaling: escalar up ou dowm um component quando for necessário
- target security concerns: focar em serviçoes que tem dadas mais sensíveis e focar em proteção no que for necessário 
- adopt technology more easily: experimentar novas coisas, deixar devs mais felizes 
- embrace incertainty in digital age: mais oportunidade de adaptar a mudanças com finer-grained APIs

## What are the disavantages of microservices?

- many, many options: muitas escolhas, se a organização tem burocracia para tomar escolhar
- takes time to get there: can take a while to see the benefits
- testing is more complex
- monitoring is more complex: onde está o problema?
- resiliency isn't free
- lots more boxes: provisioning and configuring environments, deployment - precisa automatizar
- distributed systems are hard



***

Fonte: The principles of microservices: embrace autonomy to optimize performance (Sam Newman)