Se eu tenho um código que espera um objeto de uma classe base, esse código deve funcionar **perfeitamente** se eu passar qualquer **subclasse**.

- **CreationAuditedAggregateRoot**
	Deve ser instanciado corretamente com ***CreationTime***.

``` csharp
class Ave 
{ 
	public virtual fly() => Console.WriteLine("Flying"); 
}

class Pinguin: Ave
{ 
	public override fly() => throw new NotImplementedException();
	//Penguin quebra o contrato de que todos os pássaros voam.!
}
```