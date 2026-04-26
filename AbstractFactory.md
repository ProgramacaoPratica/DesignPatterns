# Padrão Criacional: Abstract Factory

---

## Objetivo
Fornecer uma interface para criar **famílias de objetos relacionados** sem especificar suas classes concretas.

---

## Exemplo simples em Java

### Cenário
Vamos criar uma interface gráfica que pode ter dois temas:
- Windows
- Mac

Cada tema possui:
- Botão
- Checkbox

---

## 1. Interfaces (Produtos)

    public interface Botao {
        void renderizar();
    }

    public interface Checkbox {
        void marcar();
    }

---

## 2. Implementações concretas (Windows)

    public class BotaoWindows implements Botao {
        public void renderizar() {
            System.out.println("Botão Windows");
        }
    }

    public class CheckboxWindows implements Checkbox {
        public void marcar() {
            System.out.println("Checkbox Windows");
        }
    }

---

## 3. Implementações concretas (Mac)

    public class BotaoMac implements Botao {
        public void renderizar() {
            System.out.println("Botão Mac");
        }
    }

    public class CheckboxMac implements Checkbox {
        public void marcar() {
            System.out.println("Checkbox Mac");
        }
    }

---

## 4. Abstract Factory

    public interface GUIFactory {
        Botao criarBotao();
        Checkbox criarCheckbox();
    }

---

## 5. Fábricas concretas

    public class WindowsFactory implements GUIFactory {
        public Botao criarBotao() {
            return new BotaoWindows();
        }

        public Checkbox criarCheckbox() {
            return new CheckboxWindows();
        }
    }

    public class MacFactory implements GUIFactory {
        public Botao criarBotao() {
            return new BotaoMac();
        }

        public Checkbox criarCheckbox() {
            return new CheckboxMac();
        }
    }

---

## Como usar

    public class Main {
        public static void main(String[] args) {

            GUIFactory factory;

            // Pode mudar em tempo de execução
            factory = new WindowsFactory();

            Botao botao = factory.criarBotao();
            Checkbox checkbox = factory.criarCheckbox();

            botao.renderizar();
            checkbox.marcar();
        }
    }

---

## Explicação

- Botao e Checkbox → produtos  
- Implementações (Windows/Mac) → famílias de produtos  
- GUIFactory → fábrica abstrata  
- Fábricas concretas → criam objetos da mesma família  

---

## Questão crítica

Quando pode ser exagero?

- Poucas variações de objetos  
- Sistema simples  

---

## Benefícios

- Garante consistência entre objetos  
- Reduz acoplamento  
- Facilita troca de famílias completas  

---

## Exemplos reais

- Temas de interface (Dark/Light)  
- Drivers de banco de dados  
- Sistemas multiplataforma  

---
