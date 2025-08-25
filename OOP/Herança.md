Permitir que uma classe reaproveite código  e comportamento de outra classe.

```csharp
public class Event: <FullAuditedAggregateRoot<Guid>>
{
	public string Name { get; set; }
}
```