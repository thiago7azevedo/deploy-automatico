# Sugestão de automatização de deploy para produção

> Uma vez recebido o pacote via FTP da fábrica de software, antes de alocar o arquivo para o servidor linux correspondente, ele entrará na esteira de integração contínua previamente construída no Jenkins. Ao final, é criado o pacote .jar e liberado para produção.

### Seguiremos os seguintes processos no suite de teste na pipeline do Jenkins:

**1. Testes Unitários:**
   - [x] Como já recebemos o pacote com o build já efetuado, começamos a esteira do pipeline nos testes unitários com Junit;

**2. Sonar:**
   - [x] Análise do código passo a passo via integração com Sonar;

**3. Quality gate:**
   - [x] través da análise feita via Sonar, o Quality gate afere todos os pontos que o sonar registrou, de maneira que só libera para o próximo passo se a porcentagem de cobertura estiver acima de 70% de qualidade;

**4. Deploy Backend:**
   - [x] Após aprovado, a esteira faz o deploy do Backend, onde será testado separadamente do front, chamado em uma API de Homologação;

**5. Teste API:**
   - [x] Teste do Crud da API e conexões de backend em Homologação, utilizando o REST assured;

**6. Deploy Frontend:**
   - [x] Chegando na reta final de automatização em Homologação, o deploy do frontend gera uma nova versão.

**7. Testes funcionais:**
   - [x] São executados testes funcionais com Selenium, em um gird que executa uma suite de testes, todos rodando em paralelo e em java.

**8. Deploy em produção:**
   - [x] No deploy de produção, é criado o pacote .jar para em seguida subir em produção para a seguinte etapa.

**9. Health Check:**
   - [x] Após nova versão no Ar, a esteira possui o teste final via Selenium, o health check, que verifica se de fato a aplicação está no ar.
