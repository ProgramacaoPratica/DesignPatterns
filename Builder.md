# Padrão Criacional: Builder

---

## Objetivo
Separar a construção de um objeto complexo da sua representação, permitindo **criar diferentes variações usando o mesmo processo de construção**.

---

## Exemplo simples em Java

### Cenário
Vamos montar um objeto **Casa**, que pode ter diferentes configurações:
- Com ou sem piscina
- Com ou sem garagem
- Número de quartos variável

---

## 1. Produto

    public class Casa {
        private int quartos;
        private boolean piscina;
        private boolean garagem;

        public void setQuartos(int quartos) {
            this.quartos = quartos;
        }

        public void setPiscina(boolean piscina) {
            this.piscina = piscina;
        }

        public void setGaragem(boolean garagem) {
            this.garagem = garagem;
        }

        @Override
        public String toString() {
            return "Casa [quartos=" + quartos +
                   ", piscina=" + piscina +
                   ", garagem=" + garagem + "]";
        }
    }

---

## 2. Builder

    public class CasaBuilder {
        private Casa casa;

        public CasaBuilder() {
            casa = new Casa();
        }

        public CasaBuilder construirQuartos(int quantidade) {
            casa.setQuartos(quantidade);
            return this;
        }

        public CasaBuilder construirPiscina(boolean temPiscina) {
            casa.setPiscina(temPiscina);
            return this;
        }

        public CasaBuilder construirGaragem(boolean temGaragem) {
            casa.setGaragem(temGaragem);
            return this;
        }

        public Casa build() {
            return casa;
        }
    }

---

## Como usar

    public class Main {
        public static void main(String[] args) {

            Casa casa = new CasaBuilder()
                    .construirQuartos(3)
                    .construirPiscina(true)
                    .construirGaragem(false)
                    .build();

            System.out.println(casa);
        }
    }

---

## Explicação

- Casa → objeto complexo (produto final)  
- CasaBuilder → responsável por montar o objeto  
- Métodos encadeados → facilitam leitura e uso  
- build() → retorna o objeto pronto  

---

## Questão crítica

Quando usar Builder?

- Muitos parâmetros no construtor  
- Objeto com várias combinações possíveis  

Quando evitar?

- Objetos simples  
- Poucas variações  

---

## Benefícios

- Código mais legível  
- Evita construtores gigantes  
- Facilita criação de diferentes configurações  

---

## Exemplos reais

- Construção de objetos DTO  
- Configuração de APIs (ex: clients HTTP)  
- Montagem de queries complexas  

---
