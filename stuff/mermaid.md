# C4 diagram using mermaid

<style>.mermaid svg { height: auto; }</style>

extrtact from discussions here : https://github.com/mermaid-js/mermaid/issues/1276

```text
graph TB
    Customer--"Uses (https)"-->CustomerApp("Customer Application")
    subgraph "Customer Information (System)"
    CustomerApp["Customer Application<br/>(JavaScript/Angular)<br/><br/>Allow customers to manage their profile"]--"Updates customer informationusing<br/>[async, JSON/HTTPS]"-->CustomerService["Customer Service<br/>(Java, Spring Boot)<br/><br/>The point of access for customer information"]
    CustomerService--"Sends events to<br/>[WebSocket]"-->CustomerApp
    CustomerService--"Stores data in<br/>[jdbc]"-->CustomerDatabase("Customer Database<br/>(Oracle, 12c)<br/><br/>Stores customer information")
    CustomerService--"Sends customer update<br/>events to"-->MessageBus
    MessageBus--"Sends customer update<br/>events to"-->ReportingService
    MessageBus--"Sends customer update<br/>events to"-->AuditService["Audit Service<br/>[C#,.Net]<br/><br/>Provides organization wide<br/>auditing facilities"]
    ReportingService["Reporting Service<br/>[Ruby]<br/><br/>Creates normalized data for<br/>reporting purposes"]--"Stores data in"-->ReportingDatabase("Reporting Database<br/>[MySql]<br/><br/>Stores a normalized version<br/>of all business data for<br/>ad hoc reporting purposes")
    AuditService--"Stores events in"-->AuditStore["Audit Store<br/>[Event store]<br/><br/>Stores information about<br/>events that have happened"]
    end
```

## produces

```mermaid
graph TB
    Customer--"Uses (https)"-->CustomerApp("Customer Application")
    subgraph "Customer Information (System)"
    CustomerApp["Customer Application<br/>(JavaScript/Angular)<br/><br/>Allow customers to manage their profile"]--"Updates customer informationusing<br/>[async, JSON/HTTPS]"-->CustomerService["Customer Service<br/>(Java, Spring Boot)<br/><br/>The point of access for customer information"]
    CustomerService--"Sends events to<br/>[WebSocket]"-->CustomerApp
    CustomerService--"Stores data in<br/>[jdbc]"-->CustomerDatabase("Customer Database<br/>(Oracle, 12c)<br/><br/>Stores customer information")
    CustomerService--"Sends customer update<br/>events to"-->MessageBus
    MessageBus--"Sends customer update<br/>events to"-->ReportingService
    MessageBus--"Sends customer update<br/>events to"-->AuditService["Audit Service<br/>[C#,.Net]<br/><br/>Provides organization wide<br/>auditing facilities"]
    ReportingService["Reporting Service<br/>[Ruby]<br/><br/>Creates normalized data for<br/>reporting purposes"]--"Stores data in"-->ReportingDatabase("Reporting Database<br/>[MySql]<br/><br/>Stores a normalized version<br/>of all business data for<br/>ad hoc reporting purposes")
    AuditService--"Stores events in"-->AuditStore["Audit Store<br/>[Event store]<br/><br/>Stores information about<br/>events that have happened"]
    end
```


```mermaid
%%{ init: { "flowchart": { "useMaxWidth": true } }}%%
flowchart TB
classDef borderless stroke-width:0px
classDef darkBlue fill:#00008B, color:#fff
classDef brightBlue fill:#6082B6, color:#fff
classDef gray fill:#62524F, color:#fff
classDef gray2 fill:#4F625B, color:#fff

subgraph ExternalSystem[ ]
    A1[[Public User<br/> Via REST API]]
    B1[Backend Services/<br/>frontend services]
end
class ExternalSystem,A1 gray

subgraph SupportTeam[ ]
    A2[[Authorized User<br/> Via REST API]]
    B2[Backend Services/<br/>frontend services]
end
class SupportTeam,A2 darkBlue

subgraph booksSystem[ ]
    A3[[Books System]]
    B3[Allows interacting with book records]
end
class booksSystem,A3 brightBlue


ExternalSystem--Reads records using-->booksSystem
SupportTeam--Reads and writes records using-->booksSystem

subgraph authorizationSystem[ ]
    A4[[Authorization System]]
    B4[Authorizes access to resources]
end

subgraph publisher1System[ ]
    A5[[Publisher 1 System]]
    B5[Gives details about books publshed by them]
end
subgraph publisher2System[ ]
    A6[[Publisher 2 System]]
    B6[Gives details about books publshed by them]
end
class authorizationSystem,A4,publisher1System,A5,publisher2System,A6 gray2

booksSystem--Accesses authorization details using-->authorizationSystem
booksSystem--Accesses publisher details using-->publisher1System
booksSystem--Accesses publisher details using-->publisher2System

class A1,A2,A3,A4,A5,A6,B1,B2,B3,B4,B5,B6 borderless

click A3 "/csymapp/mermaid-c4-model/blob/master/containerDiagram.md" "booksSystem"
```


<div style='width:130px'>
Legend
<div style='background-color:#00008B;color:white'>Support team</div>
<div style='background-color:#555555;color:white'>External system</div>
<div style='background-color:#DD0044;color:white'>Sitecore</div>
</div>
