# Approach

Ode positions itself as a multithread helper library for digital product development. Based on Clean Architecture and appling GoF Design Patterns and the principles of Clean Code, SOLID, KISS. It leverages both direct and indirect metrics such as:

- Cyclomatic Complexity
- Circular Dependency
- Number of Dependencies
- Afferent and Efferent Couplings
- Main Sequence

{% include alert.html type="info" title="Clean Architecture book" content="These use cases orchestrate the flow of data to and from the entities, and direct those entities to use their Critical Business Rules to achieve the goals of the use case." %}

![Clean Architecture Approach](https://camo.githubusercontent.com/c8052d44b7355ce3fffc6417575b4b99d2871eefa17b7c6d227f039c7f908286/68747470733a2f2f686162726173746f726167652e6f72672f7765622f6665382f6338322f6133322f66653863383261333262313534386231613239373138376532346165373535612e706e67)

## Layer in ODE

### Business Layer
The Business Layer is responsible for the business logic and the rules that define how the system should operate to meet business requirements. In this layer, **UseCase<P, R>** that represent specific business operations are implemented, coordinating the execution of necessary actions and ensuring that all business rules are followed.

### Domain Layer
The Domain Layer contains the core logic of the application, including entities and services that encapsulate business logic without depending on infrastructure details or user interfaces. This layer is the heart of the application, where models representing business domain concepts reside, as well as the services that manipulate these models.

### Gateway Layer
The Gateway Layer acts as an interface between the application and external infrastructures, such as databases, web services, and other external APIs. This layer is responsible for transforming data from external infrastructures into formats that can be used by the Domain Layer, and vice versa. It isolates the data access logic and external communication from the rest of the application, promoting infrastructure independence.

### View Layer
The View Layer is responsible for the user interface and data presentation. It communicates with the Business Layer to retrieve the necessary data and presents that data in a way that users can interact with. The View Layer should be as simple as possible, containing only the logic necessary to render the interface and handle user interactions.