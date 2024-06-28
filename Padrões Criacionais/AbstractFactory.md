# Abstract Factory

O Abstract Factory é um padrão de projeto criacional que permite que você produza famílias de objetos relacionados sem ter que especificar suas classes concretas.

## UML

<img src="https://refactoring.guru/images/patterns/diagrams/abstract-factory/structure.png">

## Implementação

```
// Interfaces
interface IAbstractFactory
{
    IProductA CreateProductA();
    IProductB CreateProductB();
}

interface IProductA { string FunctionA(); }
interface IProductB { string FunctionB(); }

// Implementações concretas da Factory e dos Produtos
class Factory1 : IAbstractFactory
{
    public IProductA CreateProductA() => new ProductA1();
    public IProductB CreateProductB() => new ProductB1();
}

class Factory2 : IAbstractFactory
{
    public IProductA CreateProductA() => new ProductA2();
    public IProductB CreateProductB() => new ProductB2();
}

class ProductA1 : IProductA { public string FunctionA() => "A1"; }
class ProductA2 : IProductA { public string FunctionA() => "A2"; }
class ProductB1 : IProductB { public string FunctionB() => "B1"; }
class ProductB2 : IProductB { public string FunctionB() => "B2"; }

// Cliente
class Client
{
    public void Main()
    {
        ClientMethod(new Factory1());
        ClientMethod(new Factory2());
    }

    void ClientMethod(IAbstractFactory factory)
    {
        var productA = factory.CreateProductA();
        var productB = factory.CreateProductB();
        Console.WriteLine(productA.FunctionA());
        Console.WriteLine(productB.FunctionB());
    }
}

```
