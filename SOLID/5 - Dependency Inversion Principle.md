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