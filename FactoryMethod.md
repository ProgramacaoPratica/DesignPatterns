# Padrão Criacional: Factory Method

---

## Objetivo
Definir uma interface para criação de objetos, permitindo que **subclasses decidam qual classe concreta instanciar**.

---

## Exemplo simples em Java

### 1. Interface (Produto)

    public interface Transporte {
        void entregar();
    }

---

### 2. Implementações concretas

    public class Caminhao implements Transporte {
        @Override
        public void entregar() {
            System.out.println("Entrega realizada por caminhão.");
        }
    }

    public class Navio implements Transporte {
        @Override
        public void entregar() {
            System.out.println("Entrega realizada por navio.");
        }
    }

---

### 3. Classe abstrata (Criadora)

    public abstract class Logistica {

        // Factory Method
        public abstract Transporte criarTransporte();

        public void planejarEntrega() {
            Transporte transporte = criarTransporte();
            transporte.entregar();
        }
    }

---

### 4. Fábricas concretas

    public class LogisticaRodoviaria extends Logistica {
        @Override
        public Transporte criarTransporte() {
            return new Caminhao();
        }
    }

    public class LogisticaMaritima extends Logistica {
        @Override
        public Transporte criarTransporte() {
            return new Navio();
        }
    }

---

## Como usar

    public class Main {
        public static void main(String[] args) {

            Logistica logistica;

            logistica = new LogisticaRodoviaria();
            logistica.planejarEntrega();

            logistica = new LogisticaMaritima();
            logistica.planejarEntrega();
        }
    }

---

## Explicação

- Transporte → contrato comum  
- Caminhao e Navio → implementações  
- Logistica → define o Factory Method  
- Subclasses → decidem qual objeto criar  

---

## Questão crítica

Quando pode ser exagero?

- Sistemas pequenos  
- Pouca variação de objetos  

---

## Benefícios

- Reduz acoplamento  
- Facilita manutenção  
- Permite extensão sem alterar código existente  

---
