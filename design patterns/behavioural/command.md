# Command

In the Command pattern, the list of instructions is called a command object. It tells the person or object that is going to do the task what to do and how to do it. It also helps keep things organized and makes it easier to change the task or add new tasks later on.

So, in short, the Command pattern is like giving a set of instructions or commands to someone or something to do a specific task.

```csharp
var sw = new ElectricalSwitch();
sw.LightOn(new TurnOnLightCommand());
sw.LightOff(new TurnOffLightCommand());
```

```csharp
public class ElectricalSwitch
{
    public void LightOn(ICommand command)
    {
        command.Execute();
    }
    public void LightOff(ICommand command)
    {
        command.Execute();
    }
}
```

```csharp
public  interface ICommand
{
    void Execute();
}
public class TurnOffLightCommand : ICommand
  {
      public void Execute()
      {
          Console.WriteLine("Turn off light");
      }
  }
public class TurnOnLightCommand : ICommand
  {
      public void Execute()
      {
          Console.WriteLine("Turn on light");
      }
  }
```
