Aberto para extensão, fechado para modificação.

- If-Elses em uma factory de pagamentos. 
- resolve com strategy pattern.

```csharp
public class EventPriceCalculator
{
	public decimal CalculatePrice(Event e)
	{
		if(e.Type == "VIP")
			return e.BasePrice * 2;
		else if(e.Type == "Standard")
			return e.BasePrice * 3;
		else if(e.Type == "Premim")
			return e.BasePrice * 4;
		else
			return 0;
	}
}
```

```csharp
public interface IPriceStrategy
{
	public bool CanHandle(Event e);
	public decimal Calculate(e);
}


public class StandardPriceStrategy: IPriceStrategy
{
	public bool CanHandle(Event e) => e.Type == "Standard";
	public decimal Calculate(e) => e.BasePrice * 3;
}

public class PremiumPriceStrategy: IPriceStrategy
{
	public bool CanHandle(Event e) => e.Type == "Premium";
	public decimal Calculate(e) => e.BasePrice * 4;
}

public class EventPriceCalculator
{
	private readonly Enumerable<IPriceStrategy> strategies;
	public PriceCalculator(Enumerable<IPriceStrategy> _strategies)
	{
		strategies = _strategies
	}

	public  decimal CalculatePrice(Event e)
	{
		var strategy = strategies.FirstOrDefault(s => s.CanHandle(e));
		return strategy.Calculate(e);
	}
}
```