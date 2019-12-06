### Entrega continua para um [grupo de instancias gerenciadas](https://cloud.google.com/compute/docs/instance-groups/creating-groups-of-managed-instances?hl=pt-br) GCP

#### Requisitos 
Configure as SECRETS GCLOUD_PROJECT_ID e [GOOGLE_APPLICATION_CREDENTIALS](https://console.cloud.google.com/apis/credentials/serviceaccountkey) necessarias do repositorio para que as Actions possa se comunicar com o GCP de maneira segura

A secret [GOOGLE_APPLICATION_CREDENTIALS](https://console.cloud.google.com/apis/credentials/serviceaccountkey) deve ser salva em formato base64 para conversão utilize o comando

```bash
base64 testes-desenvolvimento-e9939a0308a1.json
```
e salve a saida como uma secret


#### Definindo passos do workflow
 O comando a baixo deve ser especificado no seu workflow no parametro args do steps do GCLOUD. 
 O Comando deve enviar um pedido para recriar as instancias no grupo, o gerenciamento automatico do grupo deve remover 
 e recriar as instancias baseadas no [modelo de instancia](https://cloud.google.com/compute/docs/instance-templates/?hl=pt-br) 
 durante a criação do seu modelo na sessão gerenciamento sub-sessão Automatização defina seu [script de inicialização](https://cloud.google.com/compute/docs/startupscript?hl=pt-br) 
 
```bash
gcloud compute instance-groups managed rolling-action replace instance-group-1
```

###### Observações: 
###### Ainda não tenho plena certeza se o metodo proposto de recriar as instancias para que seja entregue uma nova versão do codigo da aplicação para todas as instancias do grupo é a melhor pratica. Mas é uma alternativa viavel, talvez não muito inteligente. Assim que encontrar novos metodos estarei atualizando este documento.

Para mais delhates de implantação e ações do [Google Cloud Shell no Actions](https://github.com/marketplace/actions/google-cloud-platform-gcp-cli-gcloud) 
