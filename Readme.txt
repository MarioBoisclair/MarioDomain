The solution contains a C# implementation of the MVVM and Publish/Subscribe (P/S) patterns.
The intention is to provide a coherent playground for intermediate, or eager junior developers.
It is still eminently improvable. Improving, augmenting, changing etc. are left as valuable exercises.

If you enter the ground you can either use the following rules and/or make up your own (if you can change
all the rules and/or everything else, then you are most likely too advanced to benefit from the playground).
Don't worry if you are not familiar with all rules, the ground was meant as a learning sand box (C#, Generics, 
tree searching, generic and non-generic interfaces, polymorphism, layering, dependencies, EntityFrameworkCore etc.

-------------------------------------------------- IMPORTANT --------------------------------------------------------------------.

Currently the connection string is stored in the Settings.settings files of MarioDomainApp AND
MarioDomainMaintenanceApp projects where it should have the same value and the same scope.
The connection string must be set for a RUNNING DATABASE SERVER (RDBMS) .
The main executable  of the solution (the software included in this download)  will,
with you consent, create the database if needed when you run the main apllication
(MarioDomainApp.exe). It can also seed the newly created database.

If for any reason the database cannot be created, and that should not happen, there is a backup
in the folder DatabaseMSSQLServerBackUp name MarioDomain.Context.bak that you can restore. This
is for a Microsoft SQL Server (Express or not),
-------------------------------------------------- Rules (design decisions) -------------------------------------------------------.:

------  MVVM -------

M is a code-first model.  All pertinent entities in M implement an interface. The V is completely independent of
    all other components including EFCore and targets .NET Standard 2.0

V is a .NET Framework 4.6.1 set of mostly modeless Windows Forms operating within Weifen Luo's DockPanelSuite. 
V should be completely replaceable (WPF, Xamarin etc.). A new V should be able to reuse the M and VM interfaces
    without any changes.
V only knows the interfaces of M and VM. 
   Please forgive V's look, I am definitely not a UI specialist.  It can be much improved.

VM is a set of V agnostic view models who know both M and its interfaces. Outside of its package, a view model can
      only be known through its interface. It targets .NET Standard 2.0

The persistence of the model is in a separate package (Model.Context) containing a derived EFCore.DbContext.
      The package containing the context targets .NET Standard 2.0
      This context is driven by VM. Of course V is completely context agnostic.

------  P/S -------

For now P/S is restricted to intra processing. If you change data in a view, all other active views will "pick-up" and
	refresh if they need to. 
If there is enough interest I might later provide a multi-user version or
	you could do it yourself as an exercise. The hooks are already in place and the help files suggest possible options.


--------------------------------------------------   Requirements    -------------------------------------------------------.:

Requirements:

1. VS 2017 Community Edition above
2. An EntityFrameworkCore friendly RDBMS (I have tested with SQL Server Express). Note that SQL Server Express
   and SQL Server Management Studio (SSMS) are both and downloadable from Microsoft.
   Given the correct connection string the application can connect to and if needed create the Database,
   seed it if desired. Your consent is required for creating and/or seeding the database. 
3.The DockPanelSuite and LinqKit. The zipped source contains all the required libraries. They are both
   free and downloadable  


You will find inside the running software and in the code a list of credentials.

Mario Boisclair.
(I am retired but you can still look me up on LinkedIn.
