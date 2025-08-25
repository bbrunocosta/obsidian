Cada classe ou função deve ter um único motivo pra mudar.

📌 ***Exemplo prático (com ABP)***
```csharp
public class EventService
{	
	public void CreateEvent(CreateEventDto dto)
    {
        // Validação de negócio
        // Essa classe pode mudar por vários motivos:
        if (dto.Date < DateTime.Now)
            throw new BusinessException("Data inválida");

        // Regra de negócio: alterar a lógica de Cálculo do preço final.
        dto.Price = dto.Price * 1.2m;

        // Persistência no banco:  
        // mudar de `MyDbContext` para `IRepository`.
        using var db = new MyDbContext();
        db.Events.Add(ObjectMapper.Map<Event>(dto));
        db.SaveChanges();
    }


	private readonly EventValidator _validator;
    private readonly EventPriceCalculator _calculator;
    private readonly IRepository<Event, Guid> _repo;

	public async Task CreateEventAsync(CreateEventDto dto)
    {
        _validator.Validate(dto);
        dto.Price = _calculator.Calculate(dto.Price);
        await _repo.InsertAsync(ObjectMapper.Map<Event>(dto));
    }

}
```


1. **Regra de negócio**: alterar a lógica de preço.
2. **Persistência**: mudar de `MyDbContext` para `IRepository`.
3. **Validação**: novas regras de datas.
   