
No vídeo anterior sobre Singleton com CDI, no método updateConfig(Config newConfig) da classe de recurso ConfigResource, falei que não podemos atribuir o parâmetro newConfig ao atributo config. 

Altere o código de tal método para this.config = newConfig; 
Crie uma nova classe de recurso chamada RelatorioResource  como uma cópia da ConfigResource, alterando a anotação @Path para para @Path("/relatorio")
Tal classe simula a geração de um relatório que precisará acessar nosso Singleton Config também. Agora temos dois serviços REST disponíveis: /config e /relatorio. Acesse os métodos nos dois e informe qual o problema ocorrido com a alteração do código do updateConfig.

## Relato ##

Fis o teste instanciando o Config pelo /config, criando relatório **PNG** e gráfico **BARRAS** e sem seguida fiz o mesmo processo pelo /relatorio, criando o relatório **PDF** e gráfico **LINHAS**.
Quando fiz o GET por /config, retornou exatamente e o que alterei via PUT /config. E ao fazer o GET /relatorio retornou extamente o que atualizei no PUT /relatorio. 
Percebi que como newConfig é um novo objeto, perdemos o sentido do singleton que tem o objetivo de criar uma instância única.
