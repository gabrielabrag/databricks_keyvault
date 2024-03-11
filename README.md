# databricks_keyvault
Conexão para que databricks tenha acesso ao key vault Azure 

Na frente da url do seu work space databricks coloque: #secrets/createScope

Isso fara com que abra a tela abaixo : 
![SECRETSCOPE](https://github.com/gabrielabrag/databricks_keyvault/assets/108342265/e0931505-8026-4727-b66a-0371a9b977a7)

Busce as informaçõe na Azure: 

Acesse o seu Key vault na aba de Properties pegue as informações 

DNS Name e Resource ID

![keyVault](https://github.com/gabrielabrag/databricks_keyvault/assets/108342265/d6d0358e-9708-4b5d-a834-6f42f808e641)



Ao terminar de preencher as informações o botão CREATE sera habilitado. 

Pronto ja consegue chamar o secret no seus notbooks 

dbutils.secrets.get(scope="ScopeName", key="NameSecretAzure")
