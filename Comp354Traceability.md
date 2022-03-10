#### Comp354

###### audit security审计安全

refers to the traceability of the artefacts that have come about during the development process. they are firmly rooted in process standards such as the V model XT. Creating audit security is a topic within version and configuration management

(tracing artefacts’ path)

是指在开发过程中产生的人工制品的可追溯性。它们牢牢植根于 V 型 XT 等工艺标准。创建审计安全性是版本和配置管理中的一个主题

###### compliance 合规性

the ability to look back and ascertain whether processes and standards have been kept. in regulated branches such as the automobile sector compliance is a central aspect of and prerequisite for successful automotive SPICE assessments

回顾并确定是否保留了流程和标准的能力。在受监管的部门（例如汽车行业）中，合规性是成功的汽车 SPICE 评估的核心方面和先决条件

##### traceability (from pp.79/65)

- IEEE: 
  
  - discernable association among two or more logical entities, such as requirements, system elements, verifications and tasks  两个或多个逻辑实体之间可识别的关联，例如需求、系统元素、验证和任务

- BABOK：
  
  - the ability for tracking the relationships between sets of requirements and designs from the original stakeholder need to the actual implemented solution  跟踪从最初的利益相关者需要到实际实施的解决方案的需求和设计集之间关系的能力(both directions)
    
    ###### pre-requirements traceability
    
    ​        trace relationship between requirements and their source, the stakeholders and their needs
    
    ###### post-requirements traceability
    
    ​        trace relationships among the draft, code, and the tests

IEEE：

the traceability of the internal relationships and the relationships with their documentation is known as inner traceability

内部关系及其文档关系的可追溯性称为内部可追溯性

it becomes possible to trace the development with the help of these relationships(that created between requirements and tasks in the project planning). this form of traceability is called requirements-to-task traceability

借助这些关系（在项目规划中的需求和任务之间创建），可以跟踪开发。这种形式的可追溯性称为需求到任务的可追溯性

why is traceability difficult to achieve within agile灵活的 project

many people have significant reservations with regards to the cost-benefit relationship in the context of traceability

许多人对可追溯性背景下的成本收益关系持重大保留意见

## 354 Notes

#### 

UML : unified modeling language

###### Traceability

gives essential assistance in understanding the relationships that exist within and across software requirements, design, and implementation

•Requirements cannot be managed effectively without requirements traceability

requirement is traceable if :

1. •who suggested the requirement, why the requirement exists, 
2. •what requirements are related to it and 
3. •how that requirement relates to other information such as systems designs, implementations, and user documentation

<u>backward traceability:</u> previous stages. depends upon each element explicitly referencing its source in earlier documents

<u>forward traceability:</u> to all documents spawned by a document. depends upon each element in the document having a unique name or reference number 

###### forward-to traceability

link other documents to the requirements

###### forward-from

link requirements to the design and implementation components

###### backward-to traceability

links design and implementation components to the requirement

###### backward-from

links requirements to their source in other documents or people

#### lifecycle model  生命周期模型

**软件**生命周期**是**软件的产生直到报废的**生命周期**。

为了使规模大、结构复杂和管理复杂的软件开发变的容易控制和管理，人们把整个软件**生命周期**划分为若干阶段，使得每个阶段有明确的任务，整理出软件**生命周期模型**。

•Build-and-fix model

•Waterfall model

​    a sequential design **process** 

​    the software **development** activity is divided into different phases and each phase consists of a series of tasks and has different objectives

•Incremental model

•Evolutionary process models

•Rapid prototyping model

•Spiral model

•Agile process models

•Extreme programming

•Object-oriented life-cycle models

•Unified Process 

###### development process:

1. requirements analysis
2. design
3. coding
4. testing
5. delivery

#### domain model

A domain model is a representation of real-world conceptual classes, not of software components. It is not a set of diagrams describing software classes, or software objects with responsibilities.

### difference between System Sequence diagram and sequence diagram

A System sequence diagram visualizes a use case, while a sequence diagram visualizes a method of a class.

系统序列图可视化用例，而序列图可视化类的方法。

The elements participating (exchanging messages) in a 🎈<u>system sequence diagram</u> are **Actors and Systems**.

🎈<u>系统序列图</u>中参与（交换消息）的元素是**Actors和Systems**。

A class diagram shows a set of classes, interfaces, and their relationships and illustrates the static design view of a system, while 🎈a sequence diagram shows **the sequence of actions that occurs in a system and illustrates the dynamic view of a system**.

类图显示了一组类、接口及其关系，并说明了系统的静态设计视图，而🎈序列图显示了**发生在系统中的动作顺序并说明了系统的动态视图** .
