# databricks_keyvault
Conexão para que databricks tenha acesso ao key vault Azure 

Na frente da url do seu work space databricks coloque: #secrets/createScope. Isso fara com que abra a tela abaixo : 
![SECRETSCOPE](https://github.com/gabrielabrag/databricks_keyvault/assets/108342265/e0931505-8026-4727-b66a-0371a9b977a7)

#Busce as informaçõe na Azure: 
Acesse o seu Key vault na aba de Properties pegue as informações: DNS Name e Resource ID
![keyVault](https://github.com/gabrielabrag/databricks_keyvault/assets/108342265/d6d0358e-9708-4b5d-a834-6f42f808e641)



Ao terminar de preencher as informações o botão CREATE sera habilitado. 

Pronto ja consegue chamar o secret no seus notbooks 

dbutils.secrets.get(scope="ScopeName", key="NameSecretAzure")

#Listar scopes criados no databricks :
dbutils.secrets.listScopes()

#Lista os secrets desse scopo 
dbutils.secrets.list('scopeName')

#Apagar scope 
Até a data atual ainda não conseguimos apagar o scope pelo notbook Databricks, esse scope tem que ser apagado por uma api. 

Requisicao api: 

request: POST https://{DATABRICKS_HOST}/api/2.0/secrets/scopes/delete
authorization: Bearer {DATABRICKS_TOKEN}
params: cluster_id {CLUSTER_ID}
body: {"scope": "scopoName"}



para criar o token: 
![gerartoken](https://github.com/gabrielabrag/databricks_keyvault/assets/108342265/4d884c83-ccfb-4096-8bd6-197ba65d634f)

para pegar o cluster id: 
Na aba COMPUTE , selecione o seu CLUSTER, na lateral direita click em JSON , no final do json encontrara o CLUSTER_ID.



