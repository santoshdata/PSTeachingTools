# PSTeachingTools

## about_PSTeachingTools

# SHORT DESCRIPTION

The PSTeachingTools module is designed to offer a set of PowerShell commands
that can be used to demonstrate and teach PowerShell fundamentals.

# LONG DESCRIPTION

Very often PowerShell teachers use out of the box cmdlets like Get-Process and
Get-Service. However, sometimes the commands themselves or their output might
be distracting. This module contains a set of commands based on a more neutral
noun.


The commands are designed to be used together in pipelined expressions. They
write objects to the pipeline. The default output of Get-Vegetable includes a
custom format.ps1xml file, like many PowerShell commands. The idea is that once
students see how vegetable objects can be used, consumed and manipulated in
PowerShell, the concepts and techniques can be applied to service, process or
anything else in PowerShell.


For advanced classes, you can use the module files themselves to teach concepts
as module development, advanced functions, PowerShell classes, working with
JSON and CSV files, and format.ps1xml files.

# EXAMPLES

The Get-Vegetable command is designed to demonstrate how PowerShell works and
how you can work with PowerShell. Once the student understands how this command
works, they should be able to apply the concepts to any other command.

```powershell
PS C:\> Get-Vegetable

UPC     Count Name                 State    Color
---     ----- ----                 -----    -----
4078       12 corn                 Roasted  yellow
4064        4 tomato               Raw      red
4062       11 cucumber             Raw      green
4562       10 carrot               Raw      orange
4089       13 radish               Raw      red
4674       14 peas                 Steamed  green
4811       12 turnip               Boiled   purple
4725       18 russet potato        Fried    brown
4060       15 broccoli             Steamed  green
4067        7 zucchini             Raw      green
4090        4 spinach              Raw      green
4572        7 cauliflower          Steamed  white
3125       17 habanero pepper      Raw      orange
4677       16 Anaheim pepper       Raw      green
4088       19 red bell pepper      Sauteed  red
4081        6 eggplant             Fried    purple
4604        2 endive               Raw      green
```

When you import the module, a set of vegetables is generated from a json file.

```powershell
PS C:\> Get-Vegetable corn | Get-Member

   TypeName: Vegetable

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Peel        Method     void Peel()
Prepare     Method     void Prepare(Status State)
ToString    Method     string ToString()
Color       Property   VegColor Color {get;set;}
CookedState Property   Status CookedState {get;set;}
Count       Property   int Count {get;set;}
IsPeeled    Property   bool IsPeeled {get;set;}
IsRoot      Property   bool IsRoot {get;set;}
Name        Property   string Name {get;set;}
UPC         Property   int UPC {get;set;}
```

The default display uses the format.ps1xml file which does not reflect the
complete object, which is typical PowerShell behavior. Here are some other
ways you could use the command to demonstrate common PowerShell techniques:

```powershell
PS C:\> Get-Vegetable | Group-Object -Property Color

Count Name                      Group
----- ----                      -----
    7 green                     {Vegetable, Vegetable, Vegetable, Vegetable…}
    3 red                       {Vegetable, Vegetable, Vegetable}
    1 white                     {Vegetable}
    1 yellow                    {Vegetable}
    2 orange                    {Vegetable, Vegetable}
    2 purple                    {Vegetable, Vegetable}
    1 brown                     {Vegetable}

PS C:\> Get-Vegetable -RootOnly | Measure-Object -Property count -sum

Count             : 4
Average           :
Sum               : 53
Maximum           :
Minimum           :
StandardDeviation :
Property          : Count
```

Read full help and examples for New-Vegetable and Set-Vegetable.

## Vegetable Class
The object class and its enumerations are now exposed in PowerShell.

```powershell
PS C:\> [enum]::GetNames([vegcolor])
green
red
white
yellow
orange
purple
brown

PS C:\> [vegetable]::new.OverloadDefinitions
Vegetable new(string Name, bool IsRoot, VegColor Color, int UPC)
Vegetable new()
```

# SEE ALSO

https://aka.ms/powershell

https://jdhitsolutions.com/blog/essential-powershell-resources/

https://jdhitsolutions.com/blog/powershell-tips-tricks-and-advice/

# KEYWORDS

- teaching
- demo
