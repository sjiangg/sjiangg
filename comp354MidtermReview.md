## comp354MidtermReview

• Exam: March. 10th, 2022: Time: 17.45 – 19.15
• Closed book and notes
Questions: Similar to assignments #2 and #3.
All topics: Purpose/challenges/advantages of a given
approach
Topics to be included

##### • Software life cycle models    Advantages and Disadvantages

ETVX: Entry, Task, Verification, and Exit (software process developed by IBM)

###### process model steps

requirement-specification-design-implementation-integration-maintainence-retirement

***development process :*** requirement analysis(10-20)- design(10-20)- code(20-30)- testing/quality assurance(30-50)

<u>*requirement analysis:*</u>  Output is the SW Requirements Spec (SRS) document

**边做边改模型（Build-and-Fix-Model）**

for small projects which have not to be maintained.

    Disadvantages:     

- No specifications    

- No design    

- no traceability

- could be  high cost and difficult to maintain (total unsatisfactory)

**瀑布模型（Waterfall-Model）**

- a sequential design process in which progress is seen as flowing steadily downwards (like a waterfall) through the phases of SDLC.

- the pioneer of the SDLC processes.

Advantages

- Enforces disciplined approach: 
  
  - <u>Documentation </u>for each phase, each phase checked

- easier Maintenance
  
  - Every change reflected in the relevant documentation

Disadvantages

- “Blocking states” –some project team members must wait for other team members to complete dependent tasks

**快速原型模型（Rapid-Prototype-Model）**

(Used in the requirements phase) The small-scale replica of the end  product and is used for obtaining customer feedback 

Disadvantages:

- not proven and has its own problems  ——waterfall model for the rest of life cycle

**增量模型（Incremental-Model）**

Combines benefit of prototyping and waterfall - Develop and deliver software in increments - Feedback from one iteration is used in the future iterations - Deliver portion of the product at each stage 

Disadvantages:

- requires a good planning designing

- time consumption: Correcting a problem in one unit requires correction in all the units 

Advantages

- Deliver portion of the product at each stage 

- flexible and less expensive to change requirements and scope

- less costly compared to others

- customer can respond to each building

**Timeboxing Pipelined**

fix an iteration duration - Completion time is fixed, the functionality to be delivered is flexible

Advantages

- Has predictable delivery times

- Prevents requirements bloating

- Can reduce the average completion time by exploiting parallelism利用并行性来减少平均完成时间

- Total team size in timeboxing is larger; and this what reduces cycle time

**螺旋模型（Spiral-Model）**

强调风险分析 - 大型复杂的系统 - changes may be required at any time\

Advantage:

- additional functionality can be done at a later stage

- easy cost estimation

- customer feedback

disadvantage:

- demands risk assessment expertise

- protocol needs to be followed strictly

**敏捷开发模型（Agile-Development-Model）**

在敏捷开发中，软件项目的构建被切分成多个子项目，各个子项目的成果都经过测试，具备集成和可运行的特征。换言之，就是把一个大项目分为多个相互联系，但也可独立运行的小项目，并分别完成，在此过程中软件一直处于可使用状态 - Encourages customer satisfaction and early incremental delivery of the software

Extreme programming （XP）**极限编程** 是[敏捷软件开发]的一种方式。

Unified Process (UP) 一种开发方式，使用UML

Advantage:

- Customer satisfaction by rapid, continuous delivery of useful software.

- Working software is delivered frequently (weeks rather than months).

- People and interactions are emphasized rather than process and tools.

Disadvantage:

- lack of emphasis on necessary designing and documentation.

- large  software deliverables:  difficult to assess the effort required at the beginning of the software development life cycle.

**开源周期模型 Open-Source**

Closed-source software is maintained and tested by employees

Open-source software is generally maintained by unpaid volunteers

Advantages

- extremely successful for infrastructure projects, such as : Operating systems (Linux, OpenBSD, Mach, Darwin), Web browsers (Firefox, Netscape), Compilers (gcc), Web servers (Apache), and Database management systems (MySQL)

Disadvantages

- cannot be open-source development of a software product to be used in just one commercial organization

- inapplicable unless the target product is viewed by a wide range of users as useful

• Software Traceability

• Requirements analysis

    Use Cases

    Use case diagram

    System Sequence Diagram

    Sequence Diagrams

    GRASP patterns
• Domain Model

    What is it

    How can it be derived

#### • Cost estimation

    What is it? Why is it difficult?

#### Software Design

    Class model

    GoF patterns: Composite, Adapter, Observer
    (classical), Façade, Singleton patter

##### Design Patterns(GoF)

##### Structural (Adapter Class)

###### Composit Pattern 组合模式

Objects into <u>Tree Structures</u>, a part-whole hierarchy

**Problem**: primitive object and composite object have differednt way of handling. have to "query" each object before processing. 

**Consequences**: Uniformity. Extensibiliyt. Overhead

###### Adapter 适配器

该类负责加入独立的或不兼容的接口功能，结合了两个独立接口的功能。

*区别于 Facade*：The intent of Facade is to produce a simpler interface, and the intent of Adapter is to design to an existing interface（wrap several legacy object）. 

###### Facade立面图案

Facade模式<u>隐藏了系统的复杂性</u>，并为客户端提供了一个<u>接口</u>，客户端可以使用该接口访问系统。Facade decouples a subsystem from its clients.Clients do not have direct access to subsystem classes.A façade can be a single entry point to each subsystem level. This allows layering. Facade可以是每个子系统级别的单个入口点。这允许分层。

**Advantage**: reduces the number of objects that clients deal with(减少客户端的对象处理量). Promotes weak coupling between subsystem and its clients(低耦合LowCoupling). Helps in layering the system.（分层系统） Helps eliminate <u>circular dependencies</u>.（消除循环依赖）

##### Creational (Factory Method)

###### Singleton单例模式

 direct visibility of the unique object without global variables:

Define the class of the unique object to have a special method, instance( ).      1.creates the unique object if it does not already exist.

                        2. or it finds the unique object and returns a reference to it.

这种模式涉及到一个单一的类，该类负责创建自己的对象，同时确保只有单个对象被创建。这个类提供了一种访问其唯一的对象的方式，可以直接访问，不需要实例化该类的对象

###### Factory 工厂模式

在工厂模式中，我们在创建对象时不会对客户端暴露创建逻辑，并且是通过使用一个共同的接口来指向新创建的对象。定义一个用于创建产品的接口，由子类决定生产什么产品。当有families of objects(一起被用) 

AbstractFactory defers creation of product objects to its ConcreteFactory subclasses.

<u>Abstract Factory classes </u>are often implemented with the Factory Method pattern.  Can also be implemented using the<u> Prototype pattern.</u>

A concrete factory is often a <u>Singleton</u>

##### Behavioral (Interpreter/Template Method)

###### Observer观察者模式

当对象间存在一对多关系。one object to monitor the state of another object.  一个对象被修改时，则会自动通知依赖它的对象。

The Subject is coupled only to the Observer base class. 

**Problems**: observers must use getState(), memory leaks , 

 using  an Event based pattern: a management system needs only to register interest in the FaultEvent type to get all fault events, regardless of who publishes them.管理系统只需要注册对 FaultEvent 类型的兴趣即可获取所有故障事件，而不管是谁发布它们。

###### Strategy

定义一系列算法，封装每个算法，并使它们可互换。策略让算法独立于使用它的客户而变化。

#### Frameworks

Frameworks exhibit “inversion of control” at runtime via callbacks框架在运行时通过回调callback表现出“控制反转”"inversion of control"

Frameworks provide integrated domain-specific structures & functionality框架提供集成的特定领域结构和功能

- Key benefits of application frameworks are reusability and extensibility.应用程序框架的主要优点是可重用性和可扩展性。
