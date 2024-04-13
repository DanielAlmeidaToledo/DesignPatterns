# Singleton

O Singleton é um padrão de projeto criacional que permite a você garantir que uma classe tenha apenas uma instância, enquanto provê um ponto de acesso global para essa instância.

## UML

<img src="https://refactoring.guru/images/patterns/diagrams/singleton/structure-pt-br.png?id=151e5e19974d89c1382c5a92899784c4">

## Implementação

```
public class Singleton
{
    private static Singleton _instance;

    private Singleton() { }

    public static Singleton GetInstance()
    {
        if (_instance == null)
        {
            _instance = new Singleton();
        }
        return _instance;
    }
}
```
