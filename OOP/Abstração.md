(Não sabe quem é o Povider de um serviço)
Consiste em Mostrar apenas o que é necessário, ocultando o "como ele faz".

Ex: Em um RepositoryPattern, quem chama Repository.InsertAsync() não sabe se está usando EFCore, MongoDB ou outro provider. 

```csharp
public interface INotificador
{
    void Enviar(string mensagem);
}
```
