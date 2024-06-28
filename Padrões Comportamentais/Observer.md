# Observer

O Observer é um padrão de projeto comportamental que permite que um objeto notifique outros objetos sobre alterações em seu estado.

## UML

<img src="https://refactoring.guru/images/patterns/diagrams/observer/structure.png">

## Implementação

```
// Interface do Observador
public interface IObserver
{
    void Update(int state);
}

// Interface do Sujeito
public interface ISubject
{
    void Attach(IObserver observer);
    void Detach(IObserver observer);
    void Notify();
}

// Implementação concreta do Sujeito
public class Subject : ISubject
{
    private List<IObserver> _observers = new List<IObserver>();
    private int _state;

    public void Attach(IObserver observer)
    {
        _observers.Add(observer);
        Console.WriteLine("Attached an observer.");
    }

    public void Detach(IObserver observer)
    {
        _observers.Remove(observer);
        Console.WriteLine("Detached an observer.");
    }

    public void Notify()
    {
        Console.WriteLine("Notifying observers...");
        foreach (var observer in _observers)
        {
            observer.Update(_state);
        }
    }

    public void SomeBusinessLogic()
    {
        _state = new Random().Next(0, 10);
        Console.WriteLine($"Subject: My state has changed to {_state}");
        Notify();
    }
}

// Implementações concretas do Observador
public class ConcreteObserverA : IObserver
{
    public void Update(int state)
    {
        if (state < 3)
        {
            Console.WriteLine("ConcreteObserverA: Reacted to the event.");
        }
    }
}

public class ConcreteObserverB : IObserver
{
    public void Update(int state)
    {
        if (state == 0 || state >= 2)
        {
            Console.WriteLine("ConcreteObserverB: Reacted to the event.");
        }
    }
}

// Cliente
class Program
{
    static void Main(string[] args)
    {
        var subject = new Subject();
        var observerA = new ConcreteObserverA();
        var observerB = new ConcreteObserverB();

        subject.Attach(observerA);
        subject.Attach(observerB);

        subject.SomeBusinessLogic();

        subject.Detach(observerB);

        subject.SomeBusinessLogic();
    }
}

```
