### Documentação para executar o projeto ###

Este é um projeto de desafio das empresas ROIT em parceria com Kenzie Academy Brasil, para aprender a ferramenta de automação UiPath Studio e desenvolver uma automação que navegue pelo site CNAE IBGE e extraia os dados de códigos e descrições de cada atividade CNAE e depois disso chame um script Python para tratar os dados e escrever em uma nova planilha do Excel.

Para rodar esse projeto você precisará:
Instalação do UiPath Studio;
Instalação do Python 3.10
Instalação das bibliotecas Python: pandas, openpyxl, unidecode e re, para instalar siga os passos:

Clone ou faça o Fork deste projeto;
Depois da instalação do Python, inicie as instalações das bibliotecas globalmente através do prompt de comando e digite:
<br>
````pip install pandas````

````pip install unidecode````

````pip install openpyxl````

````pip install re````

Dentro do Uipath, siga as seguintes intruções:
1. No botão "Gerenciador de pacotes" no painel de propriedades, escreva Python na barra de pesquisa e instale a seguinte atividade: 
````UiPath.Python.Activities ````

2. Após instalado é necessário indicar o caminho da armazenamento do executável do Python na sua máquina, para isso:
Na raiz do diretório do projeto terá a pasta ````"Data"````
Na pasta "Data" terá o arquivo Excel ````"Config"````

3. Abra o arquivo e edite o seguinte campo: 
````PATH_PYTHON````
Substitua ````{NomeUsuárioWindows}```` por seu nome de usuário do Windows.

4. Abra o arquivo e edite o seguinte campo:
````LIBRARY_PATH_PYTHON````
Substitua ````{NomeUsuárioWindows}```` por seu nome de usuário do Windows.

Por fim, abra a automação no Uipath Studio e a execute.

Forneça uma Seção do CNAE para a extração dos dados sendo as opções de A a U.
O robô começará a navegar e extrair os dados, em seguida executará o script.py que transformará os textos das descrições para minúsculo e removerá os acentos, e também removerá tudo diferente de números das colunas de códigos exceto da coluna Código Seção.

Terminando a automação o Robô apresentará um box com a mensagem de sucesso e a automação irá ser concluída.

As matrizes criadas pela automação estarão disponíveis na raiz do diretório deste Projeto., sendo "cnae_atividades" sem tratamento do script Python e "cnae_atividades_fixed" com o respectivo tratamento.


### REFrameWork Template ###
**Robotic Enterprise Framework**

* Built on top of *Transactional Business Process* template
* Uses *State Machine* layout for the phases of automation project
* Offers high level logging, exception handling and recovery
* Keeps external settings in *Config.xlsx* file and Orchestrator assets
* Pulls credentials from Orchestrator assets and *Windows Credential Manager*
* Gets transaction data from Orchestrator queue and updates back status
* Takes screenshots in case of system exceptions


### How It Works ###

1. **INITIALIZE PROCESS**
 + ./Framework/*InitiAllSettings* - Load configuration data from Config.xlsx file and from assets
 + ./Framework/*GetAppCredential* - Retrieve credentials from Orchestrator assets or local Windows Credential Manager
 + ./Framework/*InitiAllApplications* - Open and login to applications used throughout the process

2. **GET TRANSACTION DATA**
 + ./Framework/*GetTransactionData* - Fetches transactions from an Orchestrator queue defined by Config("OrchestratorQueueName") or any other configured data source

3. **PROCESS TRANSACTION**
 + *Process* - Process trasaction and invoke other workflows related to the process being automated 
 + ./Framework/*SetTransactionStatus* - Updates the status of the processed transaction (Orchestrator transactions by default): Success, Business Rule Exception or System Exception

4. **END PROCESS**
 + ./Framework/*CloseAllApplications* - Logs out and closes applications used throughout the process


### For New Project ###

1. Check the Config.xlsx file and add/customize any required fields and values
2. Implement InitiAllApplications.xaml and CloseAllApplicatoins.xaml workflows, linking them in the Config.xlsx fields
3. Implement GetTransactionData.xaml and SetTransactionStatus.xaml according to the transaction type being used (Orchestrator queues by default)
4. Implement Process.xaml workflow and invoke other workflows related to the process being automated
# ChallengeRPA
