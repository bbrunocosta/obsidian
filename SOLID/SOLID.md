[[1 - Single Responsibility Principle]]
Cada classe ou função deve ter um uma única responsabilidade.
- **Regras demais no mesmo método**
	1. **Regra de negócio**: alterar a lógica de preço.
	2. **Persistência**: mudar de `MyDbContext` para `IRepository`.
	3. **Validação**: novas regras de datas.

[[2 - Open-Closed Principle]]
Aberto para extensões, fechado para modificações.
Você não deve mudar código existente para adicionar comportamento novo deve **estender**.
- **PaymentProcessor - StrategyPattern**
	if(PIX) else if(BOLETO) else if(CARTAO_CREDITO)

[[3 - Liskov Substitution Principle]]
Se eu tenho um código que espera um objeto de uma classe base, esse código deve funcionar **perfeitamente** se eu passar qualquer **subclasse**.
- **Subclasses**
	- **CreationAuditedAggregateRoot**
		Deve ser instanciado corretamente com ***CreationTime***.

[[4 - Interface Segregation Principle]]
Nenhuma classe deve ser forçada a implementar métodos e funções que não usa.
- **Interfaces menores**
	- `IHasCreationTime` → só exige `CreationTime` CreatedBy.
	- `IHasModificationTime` → só exige `LastModificationTime LastModifiedBy`.
	- `ISoftDelete` → só exige `IsDeleted`.
	- `IFullAudited` → junta várias (IHasCreationTime, IHasModificationTime, ISoftDelete).x
	``` csharp
	public class SimpleLog : Entity<Guid>, IHasCreationTime
	{
	    public DateTime CreationTime { get; set; }
	    // Creation Time deve sempre ser inicializado corretamente
	    public string Message { get; set; }
	}
	```

[[5 - Dependency Inversion Principle]]
Dependa de abstrações, não de implementações.
- **Injeção de Dependência**
	
	``` csharp
	public class MyApplicationService: AppService
	{
		public IResult EnviarEmail(IEmail email)
		{
			var client = new SMTPClient(configuration);
			client.Send(email);
		}
	}
	```

