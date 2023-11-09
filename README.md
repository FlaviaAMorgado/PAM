# PAM
Pesquisa sobre Permissões, Actions e Sensores no Android Studio 

<h1> Permissões Disponíveis e Recursos necessários </h1>
	<p>No Android temos tipos de permissões, sendo no momento da instalação, de execução e permissões especiais. Cada tipo indica o escopo de dados restritos que a sua aplicação pode acessar e os escopo de ações restritas que ele pode realizar quando a permissão for concedida. </p>  
 
<h2> Permissões de instalação </h2>
	<p>Essas permissões dão acesso limitado a dados restritos ou permite que o app execute ações restritas que afetam minimamente o sistema. Quando adicionamos essas permissões, a app store mostra um aviso de permissões na página de detalhes do aplicativo. Essas permissões são concedidas automaticamente quando o usuário efetua a instalação do aplicativo.</p>

<h2> Permissões normais </h2>
	<p>Essas permissões autorizam o acesso a dados e ações que vão além do sandbox (um local de isolado de teste, onde esses não interferem ou danifiquem qualquer outro ambiente e tenham ramificações no mundo real) do seu app, mas apresentam pouco risco à privacidade do usuário e à operação de outros app e sistemas. O sistema atribui o nível de proteção ‘normal’ às permissões normais. </p>

<h2> Permissões de assinatura </h2>
	<p> O sistema concede a permissão de assinatura a um aplicativo quando ele é assinando pelo mesmo certificado do app ou do SO (Sistema Operacional) que define a permissão. Os aplicativos que implementam serviços, como preenchimento automático, também usam permissões d assinatura. Esses apps exigem permissões de assinatura de vinculação de serviço para que somente o sistema posso se vincular aos serviços. </p>

<h2> Permissões de execução </h2>
<p> Também conhecidas como “permissões perigosas”, as permissões de execução dão ao seu app acesso extra de dados restritos ou autorizam que ele execute ações restritas que afetam mais significativamente o sistema e outros apps. Logo, você precisa solicitar permissões no app antes de acessar os dados restritos ou realizar ações restritas. Não suponha que essas permissões já tenham sido concedidas anteriormente; verifique e, se necessário, faça a solicitação delas antes de cada acesso. Muitas permissões de execução acessam dados particulares do usuário. Exemplos de dados particulares do usuário incluem localização e informações de contato. Por exemplo o microfone e a câmera que oferecem acesso a informações confidenciais. </p>	

<h2> Permissões especiais </h2>
	<p> Permissões especiais correspondem a operações de app específicas. Somente a plataforma pode definir permissões especiais. Além disso, a plataforma e os OEMs geralmente definem permissões especiais quando querem proteger o acesso a ações significativas, como sobrepor outros apps. Muitas operações são implementadas como permissões especiais.</p>

<h2> Permissões em geral </h2>
	 <h3>Internet</h3>
	<p>Necessária para aplicativos que precisam se comunicar com servidores remotos, fazer solicitações Http, baixar dados da web etc. Recursos: Acesso à internet.</p>
<h3> Câmera  </h3>	
	<p> Necessária para aplicativos que usam câmera, como app de vídeo chamadas, escanear códigos de barras, entre outros. Recursos: Câmera do dispositivo. </p> 
	<h3> READ_EXTERNAL_STORAGE e WRITE_EXTERNAL_STORAGE </h3>
<p>Necessárias para aplicativos que precisam ler ou gravar dados no armazenamento externo do dispositivo. Recurso: Acesso ao armazenamento externo.</p>	
<h3>ACCESS_FINE_LOCATION e ACCESS_COARSE_LOCATION </h3>
	<p>Necessário para apps de mapeamento, previsão do tempo, compartilhar localização etc. Recursos: GPS e localização. </p>
<h3>READ_CONTACTS e WRITE_CONTACTS </h3>
<p>Necessários para apps que precisam acessar e gerenciar os contatos. Recursos; Acesso à lista de contatos do dispositivo. </p>
<h3> RECORD_AUDIO</h3>
<p>Necessário para apps de gravação de áudio, como, chamada de voz, aplicativos de reconhecimento de voz, app de vídeos entre outros. Recursos:  Microfone do dispositivo. </p>
<h3>CALL_PHONE </h3>
<p>Necessárias para aplicativos que permitem ao usuário fazer chamadas diretamente do app. Recursos: fazer chamadas telefônicas. </p>


<hr> 

<h1> Actions </h1>
<p>No Android Studio, a action refere-se a uma operação ou comando que você pode executar para realizar uma tarefa específica. As action podem incluir coisas como criar um projeto Android, abrir um arquivo, executa, abrir um site da web, fazer uma chamada telefônica, enviar mensagens de texto e entre outras coisas. As actions são usadas para definir o que você deseja que seu aplicativo faça em resposta a uma intente específica.</p> 

<h3> Tipos e Finalidades  </h3>
	 <h4>ACTION_VIEW </h4>
<p> A Action View pode ser utilizada para solicitar que o sistema exiba dados específicos para o usuário. Ela pode ser usada de diversas maneiras, como por exemplo, abrir uma URL da web, visualizar arquivos, exibir detalhes de contatos, ver mapas e entre muitas outras coisas. </p> 
	 <p> _Exemplo de Código:_ </p>

<h6> Abrir uma URL da web: </h6>

'Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse("https://www.exemplo.com"));
startActivity(intent);'

<h6> Visualizar um arquivo de imagem: </h6>
'Uri uri = Uri.parse("content://media/external/images/media/1");'
'Intent intent = new Intent(Intent.ACTION_VIEW, uri);'
'startActivity(intent);'
	
Visualizar um local no mapa:
Uri uri = Uri.parse("geo:0,0?q=latitude,longitude(Latitude e Longitude)");
Intent intent = new Intent(Intent.ACTION_VIEW, uri);
startActivity(intent);

	ACTION_DIAL
	Essa action, tem como objetivo iniciar um aplicativo de discagem para permitir que o usuário possa fazer uma chamada telefônica, porém ela só traz o número já discado, assim dá a segurança o usuário começar a chamada. Ela é usada principalmente quando a aplicação deseja permitir que o usuário ligue para o número de telefone específico, como um serviço de entrega e suporte ao cliente. 
	Exemplo de Código:
Intent intent = new Intent(Intent.ACTION_DIAL);
intent.setData(Uri.parse("tel:+123456789")); // Substitua com o número de telefone desejado
startActivity(intent);


	ACTION_SENDTO
	Essa ação é usada para iniciar a aplicação de mensagens, com o objetivo de permitir ao usuário criar uma mensagem e definir o destinatário. Ela é útil quando você deseja iniciar a composição de uma mensagem de texto a partir do seu aplicativo, mas não deseja enviar a mensagem automaticamente.
Exemplo de Código:
Intent intent = new Intent(Intent.ACTION_SENDTO);
intent.setData(Uri.parse("smsto:+123456789")); // Substitua com o número de telefone desejado
intent.putExtra("sms_body", "Mensagem de exemplo");
startActivity(intent);

ACTION_IMAGE_CAPTURE
Essa action é utilizada para iniciar o aplicativo da câmera do dispositivo, permitindo ao usuário capturar uma imagem. Para ser algo mais funcional, chamamos a action e depois você deve abrir outra activity, assim após tirar a foto retornamos a imagem capturada. Para trazermos a imagem chamados o método ‘onActivityResult()’. 
Exemplo de Código:
Intent intent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
startActivityForResult(intent, REQUEST_IMAGE_CAPTURE);

ACTION_GET_CONTENT
Essa action é usada para permitir que o usuário selecione um conteúdo de qualquer tipo disponível em seu dispositivo, como imagens, vídeos, documentos entre outras coisas. Logo, essa ação é usada para que o usuário escolha um arquivo ou mídia de sua preferência. 
Exemplo de Código:
Intent intent = new Intent(Intent.ACTION_GET_CONTENT);
intent.setType("ImageOuQualuerOutroTipo/*"); // Defina o tipo de conteúdo desejado (neste caso, imagens)
startActivityForResult(intent, REQUEST_IMAGE_PICK);

Para qualquer action é preciso solicitar as permissões adequadas em seu arquivo manisfest para acessar o conteúdo desejado, como permissões de leitura de armazenamento externo, se aplicável.


 <h2> Referências </h2>


Rafael Negherbon, ‘Sandbox: O Que é E as Vantagens de Testes’, Transfeera, 2023 <https://transfeera.com/blog/sandbox/#:~:text=Um%20sandbox%20%C3%A9%20um%20ambiente,tenham%20ramifica%C3%A7%C3%B5es%20no%20mundo%20real.> [acessado 7 Novembro 2023].

Android Developers, 2023 <https://developer.android.com/guide/topics/manifest/action-element?hl=pt-br> [acessado 7 novembro 2023].

‘Introdução a Atividades’, Android Developers, 2023 <https://developer.android.com/guide/components/activities/intro-activities?hl=pt-br> [acessado 7 novembro 2023].

‘Usar Provedores E Visualizações de Ação’, Android Developers, 2023 <https://developer.android.com/develop/ui/views/components/appbar/action-views?hl=pt-br> [acessado 7 novembro 2023].

‘Intent  |  Android Developers’, Android Developers, 2023 <https://developer.android.com/reference/android/content/Intent> [acessado 7 novembro 2023].

‘Permitir Que Outros Apps Iniciem Sua Atividade’, Android Developers, 2023 <https://developer.android.com/training/basics/intents/filters?hl=pt-br> [acessado 7 novembro 2023].

‘Adicionar E Processar Ações’, Android Developers, 2020 <https://developer.android.com/training/appbar/actions?hl=pt-br> [acessado 7 novembro 2023].

‘Manifest.permission  |  Android Developers’, Android Developers, 2023 <https://developer.android.com/reference/android/Manifest.permission> [acessado 7 novembro 2023].

‘Manifest.permission  |  Android Developers’, Android Developers, 2023 <https://developer.android.com/reference/android/Manifest.permission#READ_EXTERNAL_STORAGE> [acessado 7 novembro 2023].









