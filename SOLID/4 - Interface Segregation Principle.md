Nenhuma classe deve ser forçada a implementar métodos e funções que não usa.

- `IHasCreationTime` → só exige `CreationTime`.
- `ISoftDelete` → só exige `IsDeleted`.
- `IFullAudited` → junta várias (Creation, Modification, Deletion).x

``` csharp
public class SimpleLog : Entity<Guid>, IHasCreationTime
{
    public DateTime CreationTime { get; set; }
	// Creation Time deve sempre ser inicializado corretamente
    public string Message { get; set; }
}
```
