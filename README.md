# Cleaning-Bank-Marketing-Campaign-Data
Projeto de desafio da plataforma DataCamp, utilizando técnicas de Python para limpeza de dados.
[https://projects.datacamp.com/projects/1613]

<img src="https://lojaboradecora.com.br/wp-content/uploads/2021/09/por-que-os-cofrinhos-para-moedas-tem-formato-porco-scaled.jpeg" width="600" height="300">

Empréstimos pessoais são uma fonte de receita lucrativa para os bancos. A taxa de juros típica de um empréstimo de dois anos no Reino Unido é em torno de 10%. Isso pode não parecer muito, mas só em setembro de 2022, os consumidores do Reino Unido pegaram emprestado cerca de £1,5 bilhões, o que significaria aproximadamente £300 milhões em juros gerados pelos bancos ao longo de dois anos!

Você foi solicitado a trabalhar com um banco para limpar os dados que eles coletaram como parte de uma campanha de marketing recente, que visava fazer com que os clientes contratassem um empréstimo pessoal. Eles planejam realizar mais campanhas de marketing no futuro, então gostariam que você garantisse que os dados estejam em conformidade com a estrutura específica e os tipos de dados que eles especificam, para que possam usar os dados limpos que você fornecer para configurar um banco de dados PostgreSQL, que armazenará os dados desta campanha e permitirá que os dados de campanhas futuras sejam facilmente importados.

Eles forneceram a você um arquivo csv chamado "bank_marketing.csv", que você precisará limpar, reformatar e dividir os dados, salvando três arquivos csv finais. Especificamente, os três arquivos devem ter os nomes e conteúdos conforme descrito abaixo:
## `client.csv`

| column | data type | description | cleaning requirements |
|--------|-----------|-------------|-----------------------|
| `client_id` | `integer` | Client ID | N/A |
| `age` | `integer` | Client's age in years | N/A |
| `job` | `object` | Client's type of job | Change `"."` to `"_"` |
| `marital` | `object` | Client's marital status | N/A |
| `education` | `object` | Client's level of education | Change `"."` to `"_"` and `"unknown"` to `np.NaN` |
| `credit_default` | `bool` | Whether the client's credit is in default | Convert to `boolean` data type:<br> `1` if `"yes"`, otherwise `0` |
| `mortgage` | `bool` | Whether the client has an existing mortgage (housing loan) | Convert to boolean data type:<br> `1` if `"yes"`, otherwise `0` |

<br>

## `campaign.csv`

| column | data type | description | cleaning requirements |
|--------|-----------|-------------|-----------------------|
| `client_id` | `integer` | Client ID | N/A |
| `number_contacts` | `integer` | Number of contact attempts to the client in the current campaign | N/A |
| `contact_duration` | `integer` | Last contact duration in seconds | N/A |
| `previous_campaign_contacts` | `integer` | Number of contact attempts to the client in the previous campaign | N/A |
| `previous_outcome` | `bool` | Outcome of the previous campaign | Convert to boolean data type:<br> `1` if `"success"`, otherwise `0`. |
| `campaign_outcome` | `bool` | Outcome of the current campaign | Convert to boolean data type:<br> `1` if `"yes"`, otherwise `0`. |
| `last_contact_date` | `datetime` | Last date the client was contacted | Create from a combination of `day`, `month`, and a newly created `year` column (which should have a value of `2022`); <br> **Format =** `"YYYY-MM-DD"` |

<br>

## `economics.csv`

| column | data type | description | cleaning requirements |
|--------|-----------|-------------|-----------------------|
| `client_id` | `integer` | Client ID | N/A |
| `cons_price_idx` | `float` | Consumer price index (monthly indicator) | N/A |
| `euribor_three_months` | `float` | Euro Interbank Offered Rate (euribor) three-month rate (daily indicator) | N/A |
