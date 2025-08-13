# RAG PDF Chat — Exemplo de Uso

Este projeto demonstra como implementar **RAG (Retrieval-Augmented Generation)** para permitir que um modelo de linguagem converse sobre o conteúdo de **documentos PDF**.  
A aplicação recebe PDFs, processa e armazena seu conteúdo em um repositório vetorial, e responde a perguntas do usuário utilizando **IA Generativa** com recuperação de contexto.

---

## Funcionalidades

- **Upload e Processamento de PDFs** — Extração de texto e conversão em embeddings vetoriais.
- **Busca Semântica** — Localização de trechos relevantes no PDF usando similaridade vetorial.
- **Geração de Respostas Contextualizadas** — Modelo de linguagem responde com base nas informações recuperadas.
- **Arquitetura Modular** — Separação clara entre agentes, utilitários e camadas de API.
- **API REST** — Rotas para upload, consulta e gerenciamento.

---

## Estrutura de Pastas

````commandline
├── app/
│ ├── ia/
│ │ ├── agents/ # Agentes responsáveis pela busca e geração de respostas
│ │ ├── models.py # Definições de modelos e classes da IA
│ │ └── utils.py # Funções auxiliares de processamento
│ ├── models/ # Modelos de dados e schemas
│ └── routers/ # Rotas da API
├── main.py # Ponto de entrada da aplicação
├── database.py # Configuração do banco de dados/vetorial store
├── requirements.txt # Dependências do projeto
├── .gitignore # Arquivos e pastas ignorados pelo Git
````

## Tecnologias Utilizadas

- **Python 3.10+**
- **FastAPI** — Framework para construção da API.
- **LangChain** — Orquestração de LLMs e RAG.
- **FAISS / ChromaDB** — Armazenamento e busca vetorial.
- **PyMuPDF / pdfplumber** — Extração de texto de PDFs.
- **OpenAI API** ou outro provedor LLM.

---

## ⚙Instalação e Configuração

1. **Clonar o repositório**
   ```bash
   git clone https://github.com/seu-usuario/rag-pdf-chat.git
   cd rag-pdf-chat

2. **Criar ambiente virtual**

````bash
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows
````
3. **Instalar dependências**

````bash
pip install -r requirements.txt
````
4.  **Configurar variáveis de ambiente**

Crie um arquivo .env com:

````bash
OPENAI_API_KEY=suachaveaqui
VECTOR_DB_PATH=./vectorstore
````
5.  **Executar a aplicação**

````bash
uvicorn main:app --reload
````

## Endpoints Principais


| Método | Rota      | Descrição                                   |
| ------ | --------- | ------------------------------------------- |
| POST   | `/upload` | Faz upload de um PDF e processa o conteúdo  |
| POST   | `/ask`    | Envia uma pergunta sobre os PDFs carregados |
| GET    | `/health` | Verifica se o servidor está rodando         |

## Fluxo de Funcionamento

1. **Upload** do PDF. 
2. **Extração** do texto e conversão em embeddings. 
3. **Armazenamento** em um banco vetorial. 
4. **Consulta** via pergunta do usuário. 
5. **Recuperação** de trechos relevantes. 
6. **Geração** de resposta pelo LLM com base no contexto encontrado.