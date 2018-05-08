---
title: WCF 疑難排解快速入門
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 5a6ea4f3ba121f419d1a8c46fc2534988a93d554
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-troubleshooting-quickstart"></a>WCF 疑難排解快速入門
本主題列出客戶在開發 WCF 用戶端和服務時會碰到的幾個已知問題。 如果您遇到的問題不在此清單中，建議您為您的服務設定追蹤。 這會產生一個追蹤檔案，您可以使用追蹤檔案檢視器檢視這個檔案，並取得服務中可能會發生之例外狀況的詳細資訊。 如需設定追蹤的詳細資訊，請參閱： [Configuring Tracing](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)。 如需追蹤檔案檢視器的詳細資訊，請參閱： [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)。  
  
1.  [在安裝 Windows 7 和 IIS 後，如果嘗試瀏覽至 WCF 服務，我會收到下列錯誤訊息：HTTP 錯誤 404.3 - 找不到。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     HTTP 錯誤 404.3 – 找不到。由於延伸組態的緣故，無法提供您要求的網頁。 若網頁是指令碼，請加入處理常式。 如應下載檔案，請加入 MIME 對應。 詳細的錯誤 InformationModule StaticFileModule。  
  
2.  [如果我的用戶端在第一個要求之後閒置一陣子，有時我會在第二個要求收到 MessageSecurityException。這是為什麼？](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [我的服務在與大約 10 個用戶端互動之後，開始拒絕新的用戶端。這是為什麼？](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [我可以從 WCF 應用程式的組態檔以外的地方載入我的服務組態嗎？](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [我的服務和用戶端運作良好，但是當用戶端在另一台電腦上時，它們就無法運作。這是為什麼？](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [當我擲回 FaultException\<例外狀況 > 類型的例外狀況，我一定會收到一般的 FaultException 型別，用戶端上並不是泛型類型。這是為什麼？](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [當回覆未包含任何資料時，單向和要求與回覆作業似乎會以大約相同的速度傳回。這是為什麼？](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [我使用 X.509 憑證搭配我的服務，然後得到 System.Security.Cryptography.CryptographicException。這是為什麼？](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [我將作業的第一個參數從大寫變更為小寫；現在我的用戶端擲回了例外狀況。這是為什麼？](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [我正在使用我的其中一種追蹤工具，而我得到 EndpointNotFoundException。這是為什麼？](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [從 WCF SOAP 應用程式呼叫 WCF Web HTTP 應用程式時，服務傳回下列錯誤：405 不允許的方法。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [什麼是基底位址？它與端點位址如何產生關聯？](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>在安裝 Windows 7 和 IIS 後，如果嘗試瀏覽至 WCF 服務，我會收到下列錯誤訊息：HTTP 錯誤 404.3 - 找不到。  
 完整的錯誤訊息是：  
  
 HTTP 錯誤 404.3 – 找不到。由於延伸組態的緣故，無法提供您要求的網頁。 若網頁是指令碼，請加入處理常式。 如應下載檔案，請加入 MIME 對應。 詳細的錯誤 InformationModule StaticFileModule。  
  
 在控制台中未明確設定 「 Windows Communication Foundation HTTP 啟動 」 時，就會發生這個錯誤訊息。 若要設定此項目，請移至控制台，按一下視窗左下角的 [程式]。 按一下 [開啟或關閉 Windows 功能]。 展開 [Microsoft .NET Framework 3.5.1]，並選取 [Windows Communication Foundation Http 啟動]。  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>如果我的用戶端在第一個要求之後閒置一陣子，有時我會在第二個要求收到 MessageSecurityException。 這是為什麼？  
 第二個要求會失敗的主要原因有兩個：(1) 工作階段已逾時或 (2) 主控服務的 Web 伺服器已回收。 第一種情況中，在服務逾時之前工作階段都是有效的。當服務未在服務繫結中指定的時間內收到來自用戶端的要求時 (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>)，服務會終止安全性工作階段。 後續的用戶端訊息會造成 <xref:System.ServiceModel.Security.MessageSecurityException>。 用戶端必須以此服務重新建立安全工作階段，以傳送未來的訊息或使用可設定狀態的安全性內容權杖。 可設定狀態的安全性內容權杖也允許安全工作階段存留已回收的 Web 伺服器。 如需使用安全工作階段的可設定狀態的安全性內容權杖的詳細資訊，請參閱[How to： 建立安全工作階段的安全性內容權杖](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)。 或者，您可以停用安全工作階段。 當您使用[ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)繫結，您可以設定`establishSecurityContext`屬性`false`停用安全工作階段。 如果要為其他繫結停用安全工作階段，必須建立自訂繫結。 如需有關建立自訂繫結的詳細資料，請參閱 [How to: Create a Custom Binding Using the SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。 在您套用其中任何一種選項之前，必須瞭解您應用程式的安全性需求。  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>我的服務在與大約 10 個用戶端互動之後，開始拒絕新的用戶端。 這是為什麼？  
 根據預設，服務同時只能有 10 個工作階段。 因此，如果服務繫結使用工作階段，服務會接受新用戶端連線直到到達該數目，然後拒絕新用戶端連線，直到其中一個目前工作階段結束為止。 您可以使用許多種方法來支援多個用戶端。 如果您的服務不需要工作階段，請勿使用工作階段繫結 (如需詳細資訊，請參閱[Sessions<](../../../docs/framework/wcf/using-sessions.md)。)另一種選擇是將 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> 屬性的值變更為適合您情況的數目，以增加工作階段限制。  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>我可以從 WCF 應用程式的組態檔以外的地方載入我的服務組態嗎？  
 可以，不過您必須建立覆寫 <xref:System.ServiceModel.ServiceHost> 方法的自訂 <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> 類別。 在該方法中，您可以呼叫基底先載入組態 (如果您也想要載入標準組態資訊)，但您也可以完全取代組態載入系統。 請注意，如果您要從與應用程式組態檔不同的組態檔載入組態，必須自行剖析組態檔並載入組態。  
  
 下列程式碼範例將示範如何覆寫 <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> 方法，以及直接設定端點。  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)    
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>   
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>我的服務和用戶端運作良好，但是當用戶端在另一台電腦上時，它們就無法運作。 發生什麼事？  
 根據例外狀況，可能有幾個問題：  
  
-   您可能需要將用戶端端點位址變更為主機名稱而非 "localhost"。  
  
-   您可能需要對應用程式開放連接埠。 如需詳細資料，請參閱 SDK 範例的 [Firewall Instructions](../../../docs/framework/wcf/samples/firewall-instructions.md) 。  
  
-   如需其他可能的問題，請參閱範例主題[在工作群組與跨電腦執行範例](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)。  
  
-   如果您的用戶端是使用 Windows 認證，且例外狀況為 <xref:System.ServiceModel.Security.SecurityNegotiationException>，請設定 Kerberos 如下。  
  
    1.  將身分識別認證新增至用戶端的 App.config 檔案中的端點項目：  
  
        ```xml
        <endpoint   
          address="http://MyServer:8000/MyService/"   
          binding="wsHttpBinding"   
          bindingConfiguration="WSHttpBinding_IServiceExample"   
          contract="IServiceExample"   
          behaviorConfiguration="ClientCredBehavior"   
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2.  在 System 或 NetworkService 帳戶下執行自我主控的服務。 您可以執行這個命令，在 System 帳戶下建立命令視窗：  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  在網際網路資訊服務 (IIS) 下主控服務，根據預設，它會使用服務主要名稱 (SPN) 帳戶。  
  
    4.  使用 SetSPN 向網域註冊新的 SPN。 請注意，您必須是網域系統管理員才能執行這項操作。  
  
 如需有關 Kerberos 通訊協定的詳細資訊，請參閱[WCF 中使用的安全性概念](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md)和：  
  
-   [偵錯 Windows 驗證錯誤](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [使用 Http.sys 登錄 Kerberos 服務主要名稱](http://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [Kerberos 說明](http://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>當我擲回 FaultException\<例外狀況 > 類型的例外狀況，我一定會收到一般的 FaultException 型別，用戶端上並不是泛型類型。 發生什麼事？  
 強烈建議您建議自己的自訂錯誤資料型別，並宣告為您的錯誤合約中的詳細型別。 原因是使用系統提供的例外狀況類型：  
  
-   建立類型依存性，移除服務導向應用程式的其中一個最大的強度。  
  
-   無法依存以標準方式序列化的例外狀況。 有些 (例如 <xref:System.Security.SecurityException>) 可能完全不能序列化。  
  
-   對用戶端公開內部實作詳細資料。 如需詳細資訊，請參閱[指定與處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。  
  
 然而，如果您是對應用程式進行偵錯，可以使用 <xref:System.ServiceModel.Description.ServiceDebugBehavior> 類別來序列化例外狀況資訊，並傳回用戶端。  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>當回覆未包含任何資料時，單向和要求與回覆作業似乎會以大約相同的速度傳回。 這是為什麼？  
 將作業指定為單向只是表示作業合約接受輸入訊息，而沒有傳回輸出訊息。 在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]中，當傳出資料已寫入網路或擲回例外狀況時，所有用戶端叫用都會傳回。 單向作業的運作方式相同，如果找不到服務可以擲回，或如果服務尚未準備好從網路接受資料便會封鎖。 通常在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]中，這會造成單向呼叫比要求與回覆更快傳回用戶端，但是任何減慢傳出資料在網路上的傳送速度的情況，都會減慢單向作業以及要求與回覆作業。 如需詳細資訊，請參閱[單向服務](../../../docs/framework/wcf/feature-details/one-way-services.md)和[使用 WCF 用戶端存取服務](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)。  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>我使用 X.509 憑證搭配我的服務，然後得到 System.Security.Cryptography.CryptographicException。 發生什麼事？  
 這常常發生在變更用來執行 IIS 背景工作處理序的使用者帳戶之後。 例如，在 [!INCLUDE[wxp](../../../includes/wxp-md.md)]中，如果您將用於執行 Aspnet_wp.exe 的預設使用者帳戶從 ASPNET 變更為自訂使用者帳戶，您可能會看到這個錯誤。 如果使用私密金鑰，使用它的處理序將會需要有權限才能存取儲存該金鑰的檔案。  
  
 如果是這種情況，您必須提供存取權限給處理序的帳戶，檔案才能包含私密金鑰。 例如，如果 IIS 背景工作處理序正在 Bob 帳戶下執行，則您會需要為 Bob 提供含有私密金鑰的檔案的讀取權。  
  
 如需如何以正確的使用者帳戶存取權給含有特定 X.509 憑證的私密金鑰檔案的詳細資訊，請參閱[如何： 使能夠存取 X.509 憑證至 WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md)。  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>我將作業的第一個參數從大寫變更為小寫；現在我的用戶端擲回了例外狀況。 這是為什麼？  
 作業簽章中參數名稱的值是合約的一部分，而且必須區分大小寫。 當您需要區分本機參數名稱和描述用戶端應用程式的作業的中繼資料時，請使用 <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> 屬性。  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>我正在使用我的其中一種追蹤工具，而我得到 EndpointNotFoundException。 發生什麼事？  
 如果您使用的追蹤工具不是系統提供的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 追蹤機制，且收到 <xref:System.ServiceModel.EndpointNotFoundException> 指出有位址篩選不符的情況，則您需要使用 <xref:System.ServiceModel.Description.ClientViaBehavior> 類別將訊息導向追蹤公用程式，然後讓公用程式將這些訊息重新導向至服務位址。 <xref:System.ServiceModel.Description.ClientViaBehavior> 類別會變更 `Via` 位址標頭，以指定與最終接收者不同的下一個網路位址，由 `To` 位址標頭指示。 然而，執行這項操作時，請勿變更端點位址，它是用於建立 `To` 值的。  
  
 下列程式碼範例顯示用戶端組態檔範例。  
  
```xml
<endpoint   
  address=http://localhost:8000/MyServer/  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"   
  contract="IMyContract"   
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>   
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>什麼是基底位址？ 它與端點位址如何產生關聯？  
 基底位址是 <xref:System.ServiceModel.ServiceHost> 類別的根位址。 根據預設，如果您將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 類別新增至服務組態中，會從 HTTP 基底位址擷取主機發行的所有端點的 Web 服務描述語言 (WSDL)，加上提供給中繼資料行為的相對位址，加上 "?wsdl"。 如果您熟悉 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 和 IIS，基底位址就等同虛擬目錄。  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>使用 NetTcpBinding 在服務端點與 MEX 端點之間共用通訊埠  
 如果您將服務的基底位址指定為 net.tcp://MyServer:8080/MyService，並且加入下列端點：  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 而且，如果您修改其中一個 NetTcpBinding 設定，如下列組態片段所示：  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 您會看到類似下面的錯誤： 未處理例外狀況： System.ServiceModel.AddressAlreadyInUseException: IP 端點 0.0.0.0:9000 可以解決這個錯誤藉由指定完整的 URL 使用不同的連接埠上已經有一個接聽程式MEX 端點中的下列組態片段所示：  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>從 WCF SOAP 應用程式呼叫 WCF Web HTTP 應用程式時，服務傳回下列錯誤：405 不允許的方法。  
 呼叫 WCF Web HTTP 應用程式 (使用的服務<xref:System.ServiceModel.WebHttpBinding>和<xref:System.ServiceModel.Description.WebHttpBehavior>) 從 WCF 服務可能會產生下列例外狀況： `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: 遠端伺服器傳回未預期的回應: (405) 方法不允許。 ' 發生這個例外狀況，因為 WCF 覆寫傳出<xref:System.ServiceModel.OperationContext>以傳入<xref:System.ServiceModel.OperationContext>。 若要解決這個問題，請在 WCF Web HTTP 服務作業中建立 <xref:System.ServiceModel.OperationContextScope> 。 例如:   
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Windows 驗證錯誤](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
