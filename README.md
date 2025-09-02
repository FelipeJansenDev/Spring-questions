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

---

### 14. Qual é a principal diferença entre @Component, @Service e @Repository no Spring?
- a) Não há diferença, todas funcionam exatamente igual  
- b) @Service é especializado para lógica de negócios e @Repository para acesso a dados, mas todos são estereótipos de @Component  
- c) @Repository adiciona tratamento automático de exceções de persistência, enquanto @Service e @Component não  
- d) Tanto b quanto c  

**Resposta correta:** d) Tanto b quanto c  

**Comentário:**  
As três anotações são estereótipos de @Component e, portanto, registram beans no contexto. @Service é usado para lógica de negócio, @Repository para acesso a dados (com tradução automática de exceções) e @Component é genérico.  

---

### 15. O que o Spring usa para implementar AOP?
- a) Apenas reflexão de Java  
- b) Dynamic proxies (JDK) e CGLIB para criar proxies  
- c) Threads dedicadas para interceptar métodos  
- d) Anotações @Aspect apenas  

**Resposta correta:** b) Dynamic proxies (JDK) e CGLIB para criar proxies  

**Comentário:**  
O Spring AOP funciona com proxies. Se a classe tiver interface → JDK dynamic proxies; caso contrário → CGLIB. As anotações apenas definem os pontos de corte, mas quem executa a lógica são os proxies.  

---

### 16. Qual a diferença entre ApplicationContext e BeanFactory?
- a) Nenhuma, ambos são exatamente iguais  
- b) BeanFactory é mais completo que ApplicationContext  
- c) ApplicationContext é uma extensão de BeanFactory, adicionando suporte a eventos, mensagens e recursos de AOP  
- d) BeanFactory só funciona em XML e ApplicationContext em anotações  

**Resposta correta:** c) ApplicationContext é uma extensão de BeanFactory, adicionando suporte a eventos, mensagens e recursos de AOP  

**Comentário:**  
BeanFactory é o contêiner básico. ApplicationContext adiciona recursos como eventos, i18n, integração com AOP, suporte a anotações (@Autowired, @Qualifier). É o mais usado em aplicações modernas.  

---

### 17. Quais métodos podem ser usados para customizar o ciclo de vida de um bean?
- a) @PostConstruct e @PreDestroy  
- b) Implementando InitializingBean e DisposableBean  
- c) Usando métodos customizados via @Bean(initMethod, destroyMethod)  
- d) Todas as anteriores  

**Resposta correta:** d) Todas as anteriores  

**Comentário:**  
O Spring permite customizar o ciclo de vida de várias formas: anotações (@PostConstruct, @PreDestroy), interfaces (InitializingBean, DisposableBean) e métodos definidos no @Bean.  

---

### 18. Qual tipo de injeção é mais recomendado pelo Spring?
- a) Field Injection (@Autowired diretamente no atributo)  
- b) Setter Injection  
- c) Constructor Injection  
- d) Nenhuma, todas são igualmente recomendadas  

**Resposta correta:** c) Constructor Injection  

**Comentário:**  
Constructor injection é a mais recomendada porque promove imutabilidade, facilita testes e garante que as dependências sejam fornecidas logo na inicialização. Field injection é considerada má prática.  

---

### 19. Como o Spring implementa o controle transacional com @Transactional?
- a) Usando proxies que envolvem o método e iniciam/commitam/rollback transações  
- b) Criando threads dedicadas para cada transação  
- c) Apenas com JDBC puro  
- d) Usando reflection sem proxies  

**Resposta correta:** a) Usando proxies que envolvem o método e iniciam/commitam/rollback transações  

**Comentário:**  
@Transactional é implementado via AOP. O proxy intercepta o método, abre a transação, executa e decide commit ou rollback conforme o resultado.  

---

### 20. Qual escopo é padrão no Spring e qual cria um novo bean a cada requisição HTTP?
- a) prototype / session  
- b) singleton / request  
- c) singleton / prototype  
- d) request / application  

**Resposta correta:** b) singleton / request  

**Comentário:**  
O escopo padrão é **singleton** (um bean por ApplicationContext). O escopo **request** cria um bean novo a cada requisição HTTP, muito usado em aplicações web.

---


### 21. O que o Spring Boot faz ao usar @SpringBootApplication?
- a) Apenas inicializa o servidor embutido  
- b) É equivalente a usar @Configuration, @EnableAutoConfiguration e @ComponentScan  
- c) Carrega somente os beans marcados com @Service  
- d) Configura apenas o banco de dados automaticamente  

**Resposta correta:** b) É equivalente a usar @Configuration, @EnableAutoConfiguration e @ComponentScan  

**Comentário:**  
@SpringBootApplication é um atalho para essas três anotações, permitindo autoconfiguração, registro de beans e varredura automática de componentes no pacote base.  

---

### 22. Para que servem os Spring Profiles?
- a) Separar beans por ambientes (dev, test, prod)  
- b) Melhorar a performance de consultas SQL  
- c) Configurar threads diferentes para cada serviço  
- d) Definir roles de segurança para usuários  

**Resposta correta:** a) Separar beans por ambientes (dev, test, prod)  

**Comentário:**  
Profiles permitem ativar configurações específicas de acordo com o ambiente. Exemplo: `@Profile("dev")` ativa um bean apenas no ambiente de desenvolvimento.  

---

### 23. Como aplicar segurança baseada em roles em métodos do Spring?
- a) Usando apenas filtros no web.xml  
- b) Usando @RolesAllowed, @Secured ou @PreAuthorize  
- c) Configurando exclusivamente via application.properties  
- d) Apenas com autenticação básica (BasicAuth)  

**Resposta correta:** b) Usando @RolesAllowed, @Secured ou @PreAuthorize  

**Comentário:**  
Spring Security permite segurança declarativa em nível de método. Com @Secured("ROLE_ADMIN") ou @PreAuthorize("hasRole('ADMIN')"), é possível restringir acesso conforme a role do usuário.  
