# Padrão Criacional: Singleton

---

## Objetivo
Garantir que uma classe tenha **apenas uma única instância** e fornecer um ponto global de acesso a ela.

---

## Exemplo simples em Java

### 1. Classe Singleton

    public class Singleton {

        // Instância única criada na inicialização (Eager)
        private static Singleton instancia = new Singleton();

        // Construtor privado impede instanciação externa
        private Singleton() {
        }

        // Método público de acesso
        public static Singleton getInstancia() {
            return instancia;
        }

        public void exibirMensagem() {
            System.out.println("Instância única em execução.");
        }
    }

---

## Como usar

    public class Main {
        public static void main(String[] args) {

            Singleton s1 = Singleton.getInstancia();
            Singleton s2 = Singleton.getInstancia();

            s1.exibirMensagem();

            // Teste: ambas apontam para o mesmo objeto
            System.out.println(s1 == s2); // true
        }
    }

---

## Explicação

- instancia → armazena a única instância da classe  
- construtor privado → impede uso de new fora da classe  
- getInstancia() → fornece acesso global controlado  

---

## Questão crítica

Quando pode causar problemas?

- Uso como variável global disfarçada  
- Dificulta testes (mock)  
- Alto acoplamento  

---

## Benefícios

- Controle da instância única  
- Economia de recursos  
- Acesso global simples  

---

## Exemplos reais

- Logger  
- Configuração do sistema  
- Cache compartilhado  

---
