# Spring-questions

### 1. Qual é a principal função do Spring Framework?
- a) Facilitar a criação de interfaces gráficas em Java  
- b) Oferecer um contêiner para Inversão de Controle e Injeção de Dependências
- c) Substituir o Java Virtual Machine  
- d) Ser um ORM para mapear objetos em tabelas  

**Resposta correta:** b) Oferecer um contêiner para Inversão de Controle e Injeção de Dependências  

**Comentário:**  
O Spring Framework tem como núcleo o conceito de **Inversão de Controle (IoC)** e **Injeção de Dependências (DI)**, permitindo criar aplicações mais desacopladas, modulares e fáceis de manter. Ele não substitui a JVM nem é um ORM, mas pode integrar-se com bibliotecas ORM como Hibernate.

---

### 2. Qual é a diferença entre @Controller e @RestController?
- a) Não existe diferença, são sinônimos
- b) @Controller retorna apenas JSON, enquanto @RestController retorna views
- c) @RestController é um atalho que combina @Controller + @ResponseBody
- d) @Controller só pode ser usado com Spring Data JPA

**Resposta correta:** c) @RestController é um atalho que combina @Controller + @ResponseBody

**Comentário:**  
@Controller normalmente retorna páginas (ex: Thymeleaf). Já @RestController retorna direto JSON/XML no corpo da resposta.

---

### 3. No Spring, quando usamos @Autowired, qual é o comportamento padrão?
- a) Injeta a dependência pelo construtor
- b) Injeta a dependência por setter obrigatoriamente
- c) Injeta a dependência por tipo (by type)
- d) Injeta a dependência por nome (by name)

**Resposta correta:** c) Injeta a dependência por tipo (by type)

**Comentário:**
O Spring procura pelo tipo da classe. Se houver mais de um Bean do mesmo tipo, pode dar conflito, e aí entramos com @Qualifier ou nome explícito.

---

### 4. Qual das opções é verdadeira sobre o escopo dos Beans no Spring?
- a) O escopo padrão é prototype
- b) O escopo padrão é singleton
- c) Não existe escopo padrão, precisa ser definido sempre
- d) O escopo padrão depende do ambiente (dev/prod)

**Resposta correta:** b) O escopo padrão é singleton

**Comentário:**
Significa que só existe uma instância do Bean por ApplicationContext. Outros escopos: prototype, request, session, etc.

---

### 5. O que a anotação @Transactional faz por padrão?
- a) Abre uma nova transação e a fecha sempre, independentemente do resultado
- b) Executa o método dentro de uma transação e faz rollback em caso de RuntimeException
- c) Apenas registra logs da transação
- d) Impede que o método seja chamado por múltiplas threads
  
**Resposta correta:** b) Executa o método dentro de uma transação e faz rollback em caso de RuntimeException

**Comentário:**
Checked exceptions (ex: IOException) não fazem rollback por padrão — precisa configurar explicitamente.

---

### 6. Quais são anotações válidas para registrar Beans no Spring?
- a) @Component
- b) @Service
- c) @Repository
- d) @Entity
  
**Resposta correta:** a) b) c)

**Comentário:**
@Entity (essa é do JPA, usada para mapear entidades, não vira Bean automaticamente).

---

### 7. Sobre o Spring Boot, quais são corretas?
- a) Usa o conceito de Auto-Configuration para reduzir configuração manual
- b) Substitui completamente o Spring Framework
- c) Permite embutir servidores como Tomcat e Jetty
- d) Requer sempre configuração em arquivos XML

**Resposta Correta:** a) Usa o conceito de Auto-Configuration para reduzir configuração manual; c) Permite embutir servidores como Tomcat e Jetty

---

### 8. Sobre o Spring Data JPA, quais são corretas?
- a) Gera automaticamente implementações de repositórios a partir de interfaces
- b) Substitui a necessidade de usar EntityManager na maioria dos casos
- c) Não suporta consultas personalizadas com JPQL
- d) Pode criar queries automáticas com base na nomenclatura dos métodos

**Resposta Correta:** a) Gera automaticamente implementações de repositórios a partir de interfaces; b) Substitui a necessidade de usar EntityManager na maioria dos casos; d) Pode criar queries automáticas com base na nomenclatura dos métodos
