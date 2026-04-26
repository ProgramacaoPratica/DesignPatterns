# Padrão Criacional: Prototype

---

## Objetivo
Permitir a criação de novos objetos **a partir da cópia de um objeto existente (protótipo)**, evitando recriação custosa ou complexa.

---

## Exemplo simples em Java

### Cenário
Vamos duplicar objetos do tipo **Documento**, podendo gerar cópias independentes.

---

## 1. Interface Prototype

    public interface Prototype {
        Prototype clonar();
    }

---

## 2. Classe concreta

    public class Documento implements Prototype {
        private String titulo;
        private String conteudo;

        public Documento(String titulo, String conteudo) {
            this.titulo = titulo;
            this.conteudo = conteudo;
        }

        public void setTitulo(String titulo) {
            this.titulo = titulo;
        }

        public void setConteudo(String conteudo) {
            this.conteudo = conteudo;
        }

        @Override
        public Prototype clonar() {
            // cópia simples (shallow copy)
            return new Documento(this.titulo, this.conteudo);
        }

        @Override
        public String toString() {
            return "Documento [titulo=" + titulo + ", conteudo=" + conteudo + "]";
        }
    }

---

## Como usar

    public class Main {
        public static void main(String[] args) {

            Documento original = new Documento("Contrato", "Conteúdo original");

            Documento copia = (Documento) original.clonar();
            copia.setTitulo("Contrato - Cópia");

            System.out.println(original);
            System.out.println(copia);
        }
    }

---

## Explicação

- Prototype → define o método de clonagem  
- Documento → implementa a cópia do objeto  
- clonar() → cria um novo objeto com base no existente  
- original e cópia → objetos independentes  

---

## Questão crítica

Shallow vs Deep Copy

- Shallow Copy → copia referências (mais simples, pode gerar efeitos colaterais)  
- Deep Copy → copia tudo (mais seguro, porém mais custoso)  

---

## Benefícios

- Evita recriação de objetos complexos  
- Melhora performance em certos cenários  
- Reduz acoplamento com classes concretas  

---

## Exemplos reais

- Clonagem de objetos em editores (documentos, gráficos)  
- Jogos (duplicação de personagens/inimigos)  
- Templates reutilizáveis  

---
