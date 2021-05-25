# PlantUML - A versatile tool for sequence diagrams and more

Have you ever needed to create complicated sequence diagrams only to have to spend considerable time updating and reviewing it countless times? Using applications like Microsoft Visio or LucidChart can make this manual work incredibly time consuming. But what if instead of using your mouse to manually draw and adjust the shapes and sequences and their content, you could write a few lines of text instead? 

If you make a mistake, instead of having to massage your change back into your diagram it can be as simple as changing one line of text. Intrigued? Read on...

## What is PlantUML?

First let's start with understanding what UML means. From Wikipedia: "The *Unified Modeling Language* (UML) is a general-purpose, developmental, modeling language in the field of software engineering that is intended to provide a standard way to visualize the design of a system."

So you can think of it as a standardised set of symbols, shapes and arrows that are automatically generated so you don't have to waste time dragging, linking and resizing these types of objects.

To answer the original topic, wha PlantUML is a tool that is used to draw UML diagrams, using a simple and human readable text description. The tool can output a diagram in PNG, SVG or LaTeX format.

An example:

![](C:\Users\Sarah\Documents\PlantUML\jokediagram.png)

This diagram was generating using the following text:

`@startuml`
`Andy -> Bill: Hey`
`Bill --> Andy: Hey there`
`Andy -> Bill: How are you?`
`Bill --> Andy: I'm good. How are you?`
`Andy -> Bill: Same old. Same old.`
`Bill --> Andy: Fair enough.`
`@enduml`

This diagram can then be easily expanded in multiple ways or edited by simply editing the text. For example, we can add another participant, Sam:

![](C:\Users\Sarah\Documents\PlantUML\jokediagram2.png)

This diagram was generated using the following additional lines of text:

`Sam --> Bill: Heeey Bill!`
`Bill --> Andy: Oh no.`
`Andy -> Bill: What is it?`
`Bill --> Andy: Sam's here.`
`Bill -> Sam: Hi Sam.`
`Andy -> Bill: Don't tell Sam I'm`
`Sam --> Andy: Heeey Andy!` 
`Andy -> Bill: ...here.`

For many different examples of how you can modify your diagram to your needs you can look at the [PlantUML wiki.](https://plantuml.com/sequence-diagram)

## How can I use PlantUML?

There are two options to use PlantUML. 

1. You can use the PlantUML [online server](http://plantuml.com/plantuml). Here you can generate diagrams on the fly and refer back to them by a unique PlantUML URL. E.g. `http://www.plantuml.com/plantuml/png/<unique string here>`

2. You can install the tool locally on your PC. This option may be useful if you want to generate diagrams offline. The tool can be operated by a GUI interface or by command line. Instructions for how to install the tool locally are in the next section.

## How to install PlantUML locally on Windows

1. Firstly, you will need to install [Java](https://www.java.com/en/download/). Make sure that you select the appropriate licence for your use.
2. Once Java is installed, download [plantUML.jar](http://sourceforge.net/projects/plantuml/files/plantuml.jar/download) and save it in a directory where you will want to store your input text files and generated diagrams.

## Using PlantUML locally

Now you have PlantUML installed these are the ways that you can use it:

### Using the GUI

To activate the GUI, double-click on the plantuml.jar file that you downloaded earlier. On the interface you will see an empty file list. To get started, create a *.txt file using your editor of your choice. I like to use Notepad++. This file should be stored in the same folder as your plantuml.jar file. Save the below text to your *.txt file.

`@startuml`
`Alice -> Bob: test`
`@enduml`

Now if you look at the interface you should see your newly saved file listed. Double click on the file to generate the diagram as a PNG image. Congratulations! You made your first UML diagram using PlantUML.

### Using the command line

To get started, create a *.txt file using your text editor of your choice. This file should be stored in the same folder as your plantuml.jar file. Save the below text to your *.txt file.

`@startuml`
`Alice -> Bob: test`
`@enduml`

Open your preferred terminal application. I prefer to use [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab).

Input the following command and press enter:

`java -jar plantuml.jar <your filename>.txt`

*Note: you need to replace `<your file name>` with the actual name of your `*`.txt file.*

This will generate the diagram as an image. Congratulations! You made your first UML diagram using PlantUML.

## Further Reading

This article only contains a very small portion of PlantUML's capabilities. PlantUML is also integrated in many platforms and applications such as GitLab, GitHub, Confluence, WordPress and more. See here for the full [list](https://plantuml.com/running). PlantUML can even be used to create non-UML diagrams! To understand the full scope of what this tool has to offer, which is extensive, you should explore the [PlantUML wiki.](https://plantuml.com/sequence-diagram) Happy reading!