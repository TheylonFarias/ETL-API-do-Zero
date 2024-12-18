# ETL com Python e Requests

Este projeto implementa um pipeline simples de **ETL** (Extract, Transform, Load) utilizando **Python** e a biblioteca `requests`. O objetivo é extrair dados de uma API, realizar transformações e salvar os resultados em um formato processável, como um arquivo CSV ou banco de dados.

## Estrutura do Projeto

```
.
├── data/               # Diretório para armazenar dados extraídos ou processados
├── src/                # Código-fonte do projeto
│   ├── extract.py      # Função para extração de dados da API
│   ├── transform.py    # Função para limpeza e transformação dos dados
│   ├── load.py         # Função para carregar os dados no destino final
│   └── main.py         # Orquestração do pipeline ETL
├── requirements.txt    # Dependências do projeto
└── README.md           # Documentação do projeto
```

## Funcionalidades

- **Extract**: Coleta dados de uma API pública ou privada usando a biblioteca `requests`.
- **Transform**: Aplica tratamentos nos dados, como limpeza, padronização e formatação.
- **Load**: Salva os dados processados em um arquivo CSV ou insere em um banco de dados.

## Requisitos

Certifique-se de ter o Python 3.8 ou superior instalado. Instale as dependências do projeto com o seguinte comando:

```bash
pip install -r requirements.txt
```

### Dependências

- `requests`: Para realizar requisições HTTP.
- `pandas`: Para manipulação e transformação de dados.

## Configuração

1. Clone este repositório:

   ```bash
   git clone https://github.com/seu-usuario/etl-python-requests.git
   cd etl-python-requests
   ```

2. Crie um arquivo `.env` na raiz do projeto (se necessário) para armazenar variáveis sensíveis, como chaves de API:

   ```env
   API_KEY=seu_api_key
   BASE_URL=https://api.exemplo.com
   ```

## Uso

1. Configure os parâmetros da API no arquivo `extract.py`.
2. Execute o pipeline completo:

   ```bash
   python src/main.py
   ```

3. Os dados processados serão salvos no diretório `data/` por padrão.

## Exemplos de Código

### Extração de Dados (`extract.py`):
```python
import requests

def extract_data(api_url, headers=None):
    response = requests.get(api_url, headers=headers)
    if response.status_code == 200:
        return response.json()
    else:
        raise Exception(f"Erro na requisição: {response.status_code}")
```

### Transformação de Dados (`transform.py`):
```python
import pandas as pd

def transform_data(raw_data):
    df = pd.DataFrame(raw_data)
    # Limpeza e transformação
    df = df.dropna()  # Exemplo: remover valores nulos
    return df
```

### Carregamento de Dados (`load.py`):
```python
import pandas as pd

def load_data(df, output_path="data/processed_data.csv"):
    df.to_csv(output_path, index=False)
```

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou enviar pull requests.

## Licença

Este projeto é licenciado sob a [MIT License](LICENSE).
