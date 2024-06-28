# Prototype

O Prototype é um padrão de projeto criacional que permite copiar objetos existentes sem fazer seu código ficar dependente de suas classes.

## UML

<img src="https://refactoring.guru/images/patterns/diagrams/prototype/structure.png">

## Implementação

```
// Classe Prototype
class Person
{
    public int Age;
    public string Name;
    public IdInfo Id;

    public Person ShallowCopy() => (Person)this.MemberwiseClone();
    public Person DeepCopy() => new Person { Age = Age, Name = string.Copy(Name), Id = new IdInfo(Id.IdNumber) };
}

class IdInfo
{
    public int IdNumber;
    public IdInfo(int idNumber) { IdNumber = idNumber; }
}

// Cliente
class Program
{
    static void Main(string[] args)
    {
        var p1 = new Person { Age = 42, Name = "Jack", Id = new IdInfo(666) };
        var p2 = p1.ShallowCopy();
        var p3 = p1.DeepCopy();
    }
}

```
