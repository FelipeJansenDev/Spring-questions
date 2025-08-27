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

---

### 9. Qual a principal diferença entre o uso de @Component, @Service, @Repository e @Controller no Spring?
- a) Não existe diferença, todos registram o bean no contexto
- b) A diferença é apenas semântica e de legibilidade, mas cada um pode ter comportamentos específicos em camadas distintas
- c) Apenas @Service pode ser usado em transações
- d) @Controller substitui @RestController

**Resposta correta:** b) A diferença é apenas semântica e de legibilidade, mas cada um pode ter comportamentos específicos em camadas distintas

**Comentário:**
Embora todos registrem o bean no contexto do Spring, as anotações possuem semântica diferente.

@Component: genérica.

@Service: usada para camada de negócio (facilita entendimento e pode habilitar aspectos como logging ou transações).

@Repository: usada para camada de persistência (habilita tradução de exceções para DataAccessException).

@Controller: usada na camada web para MVC.
Ou seja, o funcionamento básico é igual, mas cada um traz intenções de uso e comportamentos extras.

---

### 10. Em relação ao ciclo de vida de um bean no Spring, qual é a ordem correta de execução?
- a) Instanciação → Injeção de dependências → PostConstruct → AfterPropertiesSet → Uso do bean → PreDestroy
- b) Injeção de dependências → Instanciação → Uso do bean → Destruição
- c) Instanciação → Uso do bean → PostConstruct → PreDestroy
- d) Instanciação → PostConstruct → Injeção de dependências → Uso do bean → Destruição

**Resposta correta:** a) Instanciação → Injeção de dependências → PostConstruct → AfterPropertiesSet → Uso do bean → PreDestroy

**Comentário:**
O ciclo de vida de um bean é bem definido no Spring. Primeiro ocorre a instanciação, depois a injeção de dependências, em seguida chamadas de callbacks como @PostConstruct e InitializingBean#afterPropertiesSet(). Após o uso, antes da remoção, o Spring chama métodos de destruição como @PreDestroy. Isso garante inicialização controlada e cleanup adequado.

---

### 11. O que o @Transactional realmente faz em métodos de serviços no Spring?
- a) Cria uma nova transação sempre que o método é chamado
- b) Gerencia o escopo transacional, podendo criar, participar ou marcar rollback de transações existentes
- c) Apenas garante que os métodos sejam executados em paralelo
- d) É usado apenas em métodos de repositórios do JPA

**Resposta correta:** b) Gerencia o escopo transacional, podendo criar, participar ou marcar rollback de transações existentes

**Comentário:**
@Transactional não cria sempre uma nova transação. Ele segue propagações de transação (REQUIRED, REQUIRES_NEW, MANDATORY, etc.), gerencia commits e rollbacks e pode ser aplicado tanto em serviços quanto em repositórios. Além disso, respeita configurações como readOnly e níveis de isolamento.

---

### 12. Qual é a principal vantagem de usar Spring Boot AutoConfiguration?
- a) Elimina completamente a necessidade de configuração manual
- b) Garante que nenhum XML seja usado na aplicação
- c) Fornece configurações padrão baseadas no classpath e propriedades definidas, reduzindo configuração manual
- d) Substitui totalmente a anotação @Configuration

**Resposta correta:** c) Fornece configurações padrão baseadas no classpath e propriedades definidas, reduzindo configuração manual

**Comentário:**
O AutoConfiguration do Spring Boot verifica o classpath e aplica configurações padrão para diversos componentes (DataSource, JPA, Security, etc.). Isso diminui a configuração manual, mas não elimina a possibilidade de sobrescrevê-las. Não significa ausência de XML (ainda pode ser usado), e também não substitui @Configuration, que continua sendo válida.

---

### 13. Qual a diferença entre ApplicationContext e BeanFactory?
- a) Nenhuma, ambos são exatamente iguais
- b) BeanFactory é mais completo que ApplicationContext
- c) ApplicationContext é uma extensão de BeanFactory, adicionando suporte a eventos, mensagens e recursos de AOP
- d) BeanFactory só funciona em XML e ApplicationContext em anotações

**Resposta correta:** c) ApplicationContext é uma extensão de BeanFactory, adicionando suporte a eventos, mensagens e recursos de AOP

**Comentário:**
O BeanFactory é o contêiner básico de IoC, já o ApplicationContext adiciona funcionalidades como: suporte a eventos de aplicação, resolução de mensagens para i18n, integração com Spring AOP, suporte a anotações como @Autowired e @Qualifier. Hoje, em aplicações modernas, quase sempre usamos o ApplicationContext.
