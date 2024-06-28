# Strategy

O Strategy é um padrão de projeto comportamental que transforma um conjunto de comportamentos em objetos e os torna intercambiáveis dentro do objeto de contexto original.

## UML

<img src="https://refactoring.guru/images/patterns/diagrams/strategy/structure.png">

## Implementação

```
// Interface do Strategy
public interface IStrategy
{
    List<string> DoAlgorithm(List<string> data);
}

// Contexto
class Context
{
    private IStrategy _strategy;

    public Context(IStrategy strategy)
    {
        this._strategy = strategy;
    }

    public void SetStrategy(IStrategy strategy)
    {
        this._strategy = strategy;
    }

    public void DoSomeBusinessLogic(List<string> data)
    {
        Console.WriteLine("Context: Sorting data using the strategy (not sure how it'll do it)");
        var result = _strategy.DoAlgorithm(data);
        Console.WriteLine(string.Join(",", result));
    }
}

// Concrete Strategy A
class ConcreteStrategyA : IStrategy
{
    public List<string> DoAlgorithm(List<string> data)
    {
        data.Sort();
        return data;
    }
}

// Concrete Strategy B
class ConcreteStrategyB : IStrategy
{
    public List<string> DoAlgorithm(List<string> data)
    {
        data.Sort();
        data.Reverse();
        return data;
    }
}

// Cliente
class Program
{
    static void Main(string[] args)
    {
        var context = new Context(new ConcreteStrategyA());

        Console.WriteLine("Client: Strategy is set to normal sorting.");
        context.DoSomeBusinessLogic(new List<string> { "a", "b", "c", "d", "e" });

        Console.WriteLine();

        Console.WriteLine("Client: Strategy is set to reverse sorting.");
        context.SetStrategy(new ConcreteStrategyB());
        context.DoSomeBusinessLogic(new List<string> { "a", "b", "c", "d", "e" });
    }
}
```
