# Adapter

O Adapter é um padrão de projeto estrutural que permite objetos com interfaces incompatíveis colaborarem entre si. Atua como um wrapper entre dois objetos, captura chamadas para um objeto e as deixa reconhecíveis tanto em formato como interface para este segundo objeto.

## UML

<img src="https://refactoring.guru/images/patterns/diagrams/adapter/structure-object-adapter.png">

## Implementação

```
public interface ITarget
{
    string GetRequest();
}

class Adaptee
{
    public string GetSpecificRequest()
    {
        return "Specific request.";
    }
}

class Adapter : ITarget
{
    private readonly Adaptee _adaptee;

    public Adapter(Adaptee adaptee)
    {
        this._adaptee = adaptee;
    }

    public string GetRequest()
    {
        return $"This is '{this._adaptee.GetSpecificRequest()}'";
    }
}

class Program
{
    static void Main(string[] args)
    {
        Adaptee adaptee = new Adaptee();
        ITarget target = new Adapter(adaptee);

        Console.WriteLine("Adaptee interface is incompatible with the client.");
        Console.WriteLine("But with adapter client can call it's method.");

        Console.WriteLine(target.GetRequest());
    }
}
```
