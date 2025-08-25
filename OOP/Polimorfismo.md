Capacidade de um método ou interface ter comportamentos diferentes dependendo do contexto.
- **Sobrescrita (override):** mesmo método, comportamento diferente na subclasse.
- **Sobrecarga (overload):** mesmo nome, parâmetros diferentes.
  
```csharp
public abstract class Pagamento
{
    public abstract void Processar();
}

public class PagamentoPix : Pagamento
{
    public override void Processar()
    {
        Console.WriteLine("Processando via Pix");
    }
}

public class PagamentoCartao : Pagamento
{
    public override void Processar()
    {
        Console.WriteLine("Processando via Cartão");
    }
}

```