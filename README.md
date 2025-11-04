# Sistema de Recomendação de Jogos da Steam

O sistema de recomendação de jogos para a plataforma Steam, desenvolvido por Jorge Sugano Suzart em novembro de 2025. O projeto tem como principal objetivo auxiliar usuários a descobrirem novos títulos semelhantes aos seus jogos favoritos, aplicando conceitos de **Álgebra Linear** e **Processamento de Linguagem Natural (PLN)**.

O sistema utiliza o modelo **TF-IDF** (*Term Frequency-Inverse Document Frequency*) e a **similaridade do cosseno** para calcular a proximidade temática entre os jogos.

-----

## ✨ Funcionalidades e Tecnologia
https://colab.research.google.com/drive/1Qc9kmfOLYn0HJ3kXOTWEQtfDKJ91BI4n este link facilita o uso do programa

### ⚙️ Funcionamento Central

1.  **Preparação dos Dados:** A base de dados `steam.csv` é lida, e as colunas `genres` e `steamspy_tags` são combinadas para formar uma descrição textual completa de cada jogo.
2.  **Pré-processamento:** O texto é limpo (remoção de caracteres especiais e conversão para minúsculas), *stopwords* em inglês são removidas, e é aplicada a lematização usando o *WordNetLemmatizer* da biblioteca NLTK.
3.  **Transformação Vetorial:** O algoritmo `TfidfVectorizer` do *scikit-learn* converte o texto em **vetores numéricos**, onde cada palavra recebe um peso proporcional à sua importância.
4.  **Cálculo da Similaridade:** A matriz de similaridade é calculada usando a `cosine_similarity`, que mede a proximidade entre pares de jogos. A similaridade é dada pelo cosseno do ângulo entre os vetores ( $\cos(\theta)=\frac{\vec{A}\cdot\vec{B}}{||\vec{A}||||\vec{B}||}$).
      * **$\cos(\theta) \approx 1$**: jogos muito semelhantes.
      * **$\cos(\theta) \approx 0$**: jogos compartilham poucos elementos em comum.

### 🖥️ Interface de Interação

O sistema oferece dois modos de uso:

  * **Interface Gráfica no Google Colab:** Utiliza a biblioteca `ipywidgets` para permitir que o usuário digite o nome de um jogo e receba uma tabela com os **10 jogos mais similares**. A tabela é colorida conforme o grau de similaridade.
  * **Interface de Terminal:** O usuário digita o nome do jogo e visualiza os resultados em uma tabela textual ordenada no console.

### 🧠 Tecnologias Utilizadas

O projeto foi desenvolvido em **Python** utilizando as bibliotecas:

  * **Pandas**
  * **NumPy**
  * **scikit-learn**
  * **NLTK**
  * **ipywidgets**

-----

## 📄 Estrutura e Execução do Projeto

### 📁 Principais Componentes do Código

| Arquivo/Função | Descrição |
| :--- | :--- |
| `main.py` | Script principal com a lógica do sistema. |
| `prepare_data()` | Função para limpar e lematizar o texto. |
| `calculate_similarity_matrix()` | Gera a matriz de similaridade TF-IDF. |
| `get_similar_games()` | Retorna os jogos mais semelhantes ao título escolhido. |
| `create_interface()` | Cria a interface interativa para uso no Colab. |
| `steam.csv` | Dataset com as informações de cada jogo. |

### 🚀 Como Executar o Projeto

1.  **Versão Python:** Use Python 3.10 ou superior.
2.  **Instalar Dependências:**
    ```bash
    pip install pandas numpy scikit-learn nltk ipywidgets
    ```
3.  **Configuração:** Garanta que o arquivo `steam.csv` esteja no mesmo diretório do `main.py`.
4.  **Executar:**
    ```bash
    python main.py
    ```
    *Para ambiente Colab, basta carregar o código e o dataset para iniciar a interface gráfica.*

-----

## 🏫 Contexto Acadêmico

Este projeto demonstra a aplicação prática de técnicas de PLN e Álgebra Linear para resolver um problema real. Ao transformar descrições e tags em representações numéricas, o sistema é capaz de identificar padrões semânticos e fornecer recomendações relevantes. O projeto exemplifica como criar interfaces interativas com `ipywidgets` e integrar análises de texto em aplicações de recomendação.
