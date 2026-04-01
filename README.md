```csharp
namespace StevanFreeborn;

public sealed class GitHubProfile
{
  public Identity Me { get; init; }
  public TechStack Stack { get; init; }
  public EngineeringLog CurrentWork { get; init; }
  public Interests Personal { get; init; }

  public GitHubProfile()
  {
    Me = new Identity(
      Name: "Stevan Freeborn",
      Role: "Quality Engineer",
      Location: "Olathe, Kansas"
    );

    Personal = new Interests();

    Stack = new TechStack(new[] { 
      "C#", "TypeScript", "Go", "Rust",
    });

    CurrentWork = new EngineeringLog();
    CurrentWork.AddProject("Zoeae", "My notepad app. It is built in Rust btw.");
    CurrentWork.AddProject("FiscalOS", "A simple personfal finace app.");
    CurrentWork.AddProject("netdi", "Bring the .NET DI system to TypeScript.");
    CurrentWork.AddProject("termchat", "Who doesn't want chat in their terminal?");
    CurrentWork.AddProject("stream-shorts", "Create short form content from long form content");
    CurrentWork.AddProject("termtier", "Tier lists in the terminal.");
  }
}

public sealed record Identity(string Name, string Role, string Location);

public sealed class Interests
{
    public string Coffee => "I'll drink any of it, but the stronger the better.";
    public string Tech => "Windows, Terminal, and Neovim...it gets weird.";
    public string Weightlifting => "You can take the bro out of the gym, but not the gym out of the bro";
}

public sealed class TechStack(IEnumerable<string> Languages)
{
    public IEnumerable<string> Primary => Languages;
}

public sealed class EngineeringLog
{
  private readonly Dictionary<string, string> _projects = new();
  public void AddProject(string name, string desc) => _projects[name] = desc;
}
```
