# Projeto Academia Churn

Sistema para monitoramento de frequência de alunos e previsão de churn em academias.

## Funcionalidades
- Cadastro de alunos
- Registro de check-in
- Consulta de frequência
- Previsão de risco de churn
- Processamento assíncrono com RabbitMQ
- Geração de relatórios automáticos
- Atualização automática do modelo de IA
- Autenticação JWT (admin e aluno)

## Tecnologias
- Python 3.10+
- FastAPI
- SQLAlchemy
- PostgreSQL
- RabbitMQ
- Pydantic
- Scikit-learn
- Docker
- Faker (popular banco)

## Instalação e Execução (Docker)

1. **Clone o repositório:**
   ```bash
   git clone <seu-fork>
   cd projeto-academia-churn
   ```
2. **Suba tudo com Docker Compose:**
   ```bash
   docker-compose up --build
   ```
   Isso irá subir:
   - API FastAPI (porta 8000)
   - PostgreSQL (porta 5432)
   - RabbitMQ (porta 5672 e 15672)

3. **Acesse a documentação da API:**
   - [http://localhost:8000/docs](http://localhost:8000/docs)

4. **(Opcional) Inicialize as tabelas:**
   ```bash
   docker-compose exec app python scripts/init_db.py
   ```

5. **Popule o banco com dados fake:**
   - Com a API rodando, execute:
   ```bash
   python faker-academia.py
   ```
   Isso irá criar planos, alunos e checkins automaticamente via API.

6. **Execute os workers RabbitMQ:**
   Em terminais separados, rode:
   ```bash
   docker-compose exec app python app/messaging/worker_checkin.py
   docker-compose exec app python app/messaging/worker_relatorio_frequencia.py
   docker-compose exec app python app/messaging/worker_modelo.py
   ```

7. **Testes automatizados:**
   ```bash
   pytest
   ```
   Ou:
   ```bash
   python tests/test_full_flow.py
   ```

## Autenticação JWT
- **Endpoint de login:** `POST /token`
- **Usuários de exemplo:**
  - admin / admin
  - aluno / aluno
- **No Swagger:** Clique em "Authorize", preencha apenas username e password, e clique em Authorize.

## Como cumprir os requisitos do recrutador

1. **API REST com endpoints:**
   - Todos os endpoints pedidos estão implementados e documentados no Swagger.
2. **Banco de dados PostgreSQL:**
   - Estrutura criada automaticamente (ou via script/init_db.py).
3. **Processamento assíncrono com RabbitMQ:**
   - Workers e producers implementados, basta rodar os scripts indicados.
4. **Modelo de IA para previsão de churn:**
   - Notebook em `ml/churn.ipynb` e integração com a API.
5. **Popular banco:**
   - Use `faker-academia.py` para gerar dados realistas.
6. **Testes automatizados:**
   - Execute `pytest` ou `python tests/test_full_flow.py`.
7. **Documentação:**
   - Swagger disponível em `/docs`.
8. **Autenticação JWT:**
   - Implementada para admin e aluno.
9. **Docker:**
   - Projeto pronto para rodar com `docker-compose up --build`.

## Passos para entrega
1. Faça um fork do repositório.
2. Suba seu código e scripts.
3. Certifique-se de que o README está atualizado.
4. Crie um Pull Request para o repositório original.
5. Envie um e-mail para o recrutador com:
   - Seu currículo
   - Link do Pull Request
   - Informações de contato

---

**Dúvidas?** Consulte a documentação da API ou entre em contato.
>>>>>>> 455b3a0 (Entrega do teste - projeto academia churn)
