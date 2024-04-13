# Builder

O Builder é um padrão de projeto criacional que permite a você construir objetos complexos passo a passo. O padrão permite que você produza diferentes tipos e representações de um objeto usando o mesmo código de construção.

## UML

<img src="https://refactoring.guru/images/patterns/diagrams/builder/structure.png">

## Implementação

```
// Produto a ser construído pelo builder
class Product
{
    public string PartA { get; set; }
    public string PartB { get; set; }

    public void ShowParts()
    {
        Console.WriteLine($"Part A: {PartA}");
        Console.WriteLine($"Part B: {PartB}");
    }
}

// Interface para o Builder
interface IBuilder
{
    void BuildPartA();
    void BuildPartB();
    Product GetProduct();
}

// Um builder concreto
class ConcreteBuilder : IBuilder
{
    private Product _product = new Product();

    public void BuildPartA()
    {
        _product.PartA = "Part A";
    }

    public void BuildPartB()
    {
        _product.PartB = "Part B";
    }

    public Product GetProduct()
    {
        return _product;
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Usando o padrão Builder
        var builder = new ConcreteBuilder();
        builder.BuildPartA();
        builder.BuildPartB();

        var product = builder.GetProduct();
        product.ShowParts();
    }
}
```
