    ---

copyright:
 years: 2015 2016

---


# Ativando aplicativos Android para receber {{site.data.keyword.mobilepushshort}}
{: #tag_based_notifications}
Última atualização: 16 de agosto de 2016
{: .last-updated}

Ative aplicativos Android para receber {{site.data.keyword.mobilepushshort}} e enviar {{site.data.keyword.mobilepushshort}} para seus dispositivos.

## Instalando o Client Push SDK com Gradle
{: #android_install}

Esta seção descreve como instalar e usar o Client Push SDK para desenvolver ainda mais os aplicativos Android.

Os serviços Push SDK móveis do Bluemix® podem ser incluídos usando Gradle. O Gradle faz download automaticamente dos artefatos de repositórios e os disponibiliza para seu aplicativo Android. Certifique-se de configurar corretamente o Android Studio e o Android Studio SDK. Para obter mais informações sobre como configurar o sistema, consulte [Visão geral do Android Studio](https://developer.android.com/tools/studio/index.html). Para
obter informações sobre o Gradle, consulte [Configurando construções do Gradle](http://developer.android.com/tools/building/configuring-gradle.html).

1. No Android Studio, depois de criar e abrir seu aplicativo móvel, abra o arquivo
**build.gradle** do aplicativo. 
2. Inclua as seguintes dependências em seu aplicativo móvel. Estas instruções de importação são necessárias para os fragmentos de código:

	```
	import com.ibm.mobilefirstplatform.clientsdk.android.core.api.BMSClient;
	import com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPush;
	import com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushException;
	import com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushResponseListener;
	import com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushNotificationListener;
	import com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPSimplePushNotification;
	```


2. Inclua as seguintes dependências em seu aplicativo móvel. As linhas a seguir incluem o Push client SDK do Bluemix™ Mobile Services e o SDK de serviços do Google Play nas dependências do escopo de compilação.

	```
	dependencies {
	  compile group: 'com.ibm.mobilefirstplatform.clientsdk.android', 
		name: 'push', 
		version: '2.+',
		ext: 'aar', 
		transitive: true
	}  
	```
3. No arquivo **AndroidManifest.xml**, inclua as permissões a seguir. Para visualizar um manifest de amostra, consulte [Aplicativo de amostra Android helloPush](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush/blob/master/helloPush/app/src/main/AndroidManifest.xml). Para visualizar um arquivo Gradle de amostra, consulte
[Arquivo de amostra Build Gradle](https://github.com/ibm-bluemix-mobile-services/bms-samples-android-hellopush/blob/master/helloPush/app/build.gradle).

	```
	<uses-permission android:name="android.permission.INTERNET"/>
	<uses-permission android:name="com.ibm.clientsdk.android.app.permission.C2D_MESSAGE" />
	<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
	<uses-permission android:name="android.permission.WAKE_LOCK" />
	<uses-permission android:name="android.permission.GET_ACCOUNTS" />
	<uses-permission android:name="android.permission.USE_CREDENTIALS" />
	<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
	<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>

	```
   Leia mais sobre as [Permissões do Android](http://developer.android.com/guide/topics/security/permissions.html) aqui.

4. Inclua as configurações de intento de notificação da atividade. Essa configuração inicia o aplicativo quando o usuário clica na notificação recebida da área de notificação.

	```
	<intent-filter>  
		<action android:name="<Your_Android_Package_Name.IBMPushNotification"/>   
		<category  android:name="android.intent.category.DEFAULT"/>
	</intent-filter>
	```
	**Nota**: substitua *Your_Android_Package_Name* na ação anterior pelo nome do pacote de aplicativos usado em seu aplicativo.

5. Inclua o serviço de intento Google Cloud Messaging (GCM) e os filtros de intento das notificações de evento RECEIVE.

	```
	service android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.api.MFPPushIntentService" />

	<receiver
	    android:name="com.ibm.mobilefirstplatform.clientsdk.android.push.internal.MFPPushBroadcastReceiver"
	    android:permission="com.google.android.c2dm.permission.SEND">
	    <intent-filter>
	        <action android:name="com.google.android.c2dm.intent.RECEIVE" />

	        <category android:name="com.ibm.mobilefirstplatform.clientsdk.android.app" />
	    </intent-filter>
	    <intent-filter>
	        <action android:name="android.intent.action.BOOT_COMPLETED" />

	        <category android:name="com.ibm.mobilefirstplatform.clientsdk.android.app" />
	    </intent-filter>
	</receiver>
	```


## Inicializando os apps Push SDK for Android
{: #android_initialize}

Um local comum para colocar o código de inicialização está no método onCreate da atividade principal no aplicativo Android.

Para obter a rota e o GUID do App, selecione a opção Configuração na área de janela de navegação de seus serviços de push inicializados e clique em **Opções móveis**.
Use esses valores para a rota e o GUID do App. Modifique o fragmento de código para usar os parâmetros appRoute e appGUID do app Bluemix.


###Inicializar o SDK principal

```
// Initialize the SDK for Java (Android) with IBM Bluemix AppGUID and
route BMSClient.getInstance().initialize(getApplicationContext(),
appRoute , appGuid, bluemixRegionSuffix);

```


####appRoute
{: approute}

Especifica a rota que é designada ao aplicativo do servidor que você criou no Bluemix.

####AppGUID
{: appguid}

Especifica a chave exclusiva designada à instância de serviço do {{site.data.keyword.mobilepushshort}} no Bluemix. Esse valor faz
distinção entre maiúsculas e minúsculas. É possível obter esse valor em Opções móveis no Painel Push.

####bluemixRegionSuffix
{: bluemixRegionSuffix}

Especifica o local em que o app está hospedado. É possível usar um destes três valores:

- BMSClient.REGION_US_SOUTH
- BMSClient.REGION_UK
- BMSClient.REGION_SYDNEY

###Inicializar o Push SDK do cliente

```
//Initialize client Push SDK for Java
MFPPush push = MFPPush.getInstance();
push.initialize(getApplicationContext(), "AppGUID");
```
####AppGUID
{: AppGUID}

Esta é a chave AppGUID do serviço {{site.data.keyword.mobilepushshort}}.

## Registrando dispositivos Android
{: #android_register}

Use a API `MFPPush.register()` para registrar o dispositivo com o serviço {{site.data.keyword.mobilepushshort}}. Para o registro de dispositivos Android, inclua as informações do Google Cloud Messaging (GCM) no painel de configuração do serviço {{site.data.keyword.mobilepushshort}} do Bluemix. Para obter mais informações, consulte [Configurando credenciais para o Google Cloud Messaging](t_push_provider_android.html).

Copie e cole os seguintes fragmentos de códigos em seu aplicativo móvel Android.

```
	//Register Android devices
	push.registerDevice(new MFPPushResponseListener<String>() {
	    @Override
	    public void onSuccess(String deviceId) {
	           //handle success here
	    }
	    @Override
	    public void onFailure(MFPPushException ex) {
	    //handle failure here
	    }
	});
```

```
	//Handles the notification when it arrives
	MFPPushNotificationListener notificationListener = new MFPPushNotificationListener() {
	    @Override
	    public void onReceive (final MFPSimplePushNotification message){
	      // Handle Push Notification
	    }
	};
```


## Recebendo notificações push em dispositivos Android
{: #android_receive}

Para registrar o objeto notificationListener com push, chame o método **MFPPush.listen()**. Esse método é chamado geralmente a partir do método** onResume() **da atividade que está manipulando as notificações push.

1. Para registrar o objeto notificationListener com push, chame o método **listen()**. Esse método é chamado geralmente a partir do método** onResume() **da atividade que está manipulando as notificações push.

	```
	@Override
	protected void onResume(){
	   super.onResume();
	   if(push != null) {
	       push.listen(notificationListener);
	   }
	}
  ```
2. Compile o projeto e execute-o no dispositivo ou simulador. Quando o método onSuccess() para o listener de resposta no método register() for chamado, ele confirmará que o dispositivo foi registrado com sucesso com o serviço {{site.data.keyword.mobilepushshort}}. Nesse momento, é
possível enviar uma mensagem conforme descrito em Enviando notificações push básicas.
3. Verifique se seus dispositivos receberam sua notificação. Se o aplicativo estiver em execução no primeiro plano, a notificação será manipulada por **MFPPushNotificationListener**. Se o aplicativo estiver em segundo plano, uma mensagem será exibida na barra de notificações.


## Enviando {{site.data.keyword.mobilepushshort}} básicas
{: #send}

Depois de desenvolver seus aplicativos, é possível enviar notificações push básicas (sem usar tags, badges, cargas úteis adicionais ou arquivos de som).

1. Em **Escolher o público**, selecione um dos seguintes públicos: **Todos os dispositivos** ou por plataforma: **Apenas dispositivos iOS** ou **Apenas
dispositivos Android**. 

	**Nota**: ao selecionar a opção **Todos os dispositivos**, todos os dispositivos inscritos para notificações push receberão notificações.

![Tela de notificações](images/tag_notification.jpg)

2. Em **Criar sua notificação**, insira sua mensagem e clique
em **Enviar**.
3. Verifique se seus dispositivos receberam sua notificação. A captura de tela a seguir mostra uma caixa de alerta que manipula uma notificação push no primeiro plano em um dispositivo Android.

![Notificação push de primeiro plano no Android](images/Android_Screenshot.jpg)

A captura de tela a seguir mostra uma notificação push no plano de fundo para Android.

![Notificação push de segundo plano no Android](images/background.jpg)



## Etapas Seguintes
{: #next_steps_tags}

Depois de configurar com êxito notificações básicas, é possível configurar notificações baseadas em tag e opções avançadas.

Inclua esses recursos do serviço de notificações push em seu aplicativo.
Para usar notificações baseadas em tag, consulte [Notificações baseadas em tag](c_tag_basednotifications.html).
Para usar opções de notificações avançadas, consulte [Notificações push avançadas](t_advance_notifications.html).
