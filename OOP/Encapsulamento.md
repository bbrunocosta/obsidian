Protege o estado interno do objeto e controla o acesso a ele através de métodos e propriedades.
Consiste em usar modificadores de acesso (private, protected, public) para impedir acesso direto indevido.

```csharp
public class ContaBancaria
{
    private decimal saldo;
	// Aqui ningém pode alterar o saldo, apenas depositar ou sacar.
    public void Depositar(decimal valor)
    {
        if (valor <= 0)
            throw new ArgumentException("Valor inválido");
        saldo += valor;
    }

    public decimal ObterSaldo() => saldo;
}
```