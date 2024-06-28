# Factory Method

O Factory Method é um padrão criacional de projeto que fornece uma interface para criar objetos em uma superclasse, mas permite que as subclasses alterem o tipo de objetos que serão criados.

## UML

<img src="https://refactoring.guru/images/patterns/diagrams/factory-method/structure.png">

## Implementação

```
// Interface do Produto
interface IProduct
{
    string Operation();
}

// Produtos Concretos
class Product1 : IProduct
{
    public string Operation() => "Result of Product1";
}

class Product2 : IProduct
{
    public string Operation() => "Result of Product2";
}

// Criador abstrato
abstract class Creator
{
    public abstract IProduct FactoryMethod();
}

// Criadores Concretos
class Creator1 : Creator
{
    public override IProduct FactoryMethod() => new Product1();
}

class Creator2 : Creator
{
    public override IProduct FactoryMethod() => new Product2();
}

// Cliente
class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine(new Creator1().FactoryMethod().Operation());
        Console.WriteLine(new Creator2().FactoryMethod().Operation());
    }
}

```
