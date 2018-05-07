---
title: 使用 WCF 的委派和模擬
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- impersonation [WCF]
- delegation [WCF]
ms.assetid: 110e60f7-5b03-4b69-b667-31721b8e3152
ms.openlocfilehash: 811ab308b881b5209d44612b29fb51d1c79e8bf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="delegation-and-impersonation-with-wcf"></a>使用 WCF 的委派和模擬
「*模擬* 」(Impersonation) 是服務用來限制用戶端存取服務網域資源的常用技術。 服務網域資源可以是像是本機檔案 (模擬) 的電腦資源，或是在另一部電腦上的資源，例如檔案共用 (委派)。 如需範例應用程式，請參閱 [Impersonating the Client](../../../../docs/framework/wcf/samples/impersonating-the-client.md)。 如需如何使用模擬的範例，請參閱 [如何：在服務上模擬用戶端](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)。  
  
> [!IMPORTANT]
>  請留意，在模擬服務上的用戶端時，服務會以用戶端的認證執行，而該認證的權限可能高於伺服器處理序。  
  
## <a name="overview"></a>總覽  
 一般而言，用戶端會呼叫服務，讓服務代表用戶端執行一些動作。 模擬可讓服務在執行動作時擔任用戶端。 委派可讓前端服務將用戶端的要求轉寄到後端服務，如此一來，後端服務也可以模擬用戶端。 模擬是最常用來檢查用戶端是否經過授權可執行特定動作的方法，而委派則是一種將模擬功能連同用戶端的身分識別一起流動至後端服務的方法。 委派是 Windows 網域功能，可以在執行 Kerberos 驗證時使用。 委派與身分識別流動不同，並且由於委派會傳輸此功能以模擬用戶端，而又不需擁有用戶端的密碼，因此它的作業權限比身分識別流動高得多。  
  
 模擬與委派兩者都需要用戶端具有 Windows 身分識別。 如果用戶端沒有 Windows 身分識別，則唯一的選擇就是將用戶端的身分識別流動至第二個服務。  
  
## <a name="impersonation-basics"></a>模擬基本概念  
 Windows Communication Foundation (WCF) 支援各種不同的用戶端認證的模擬。 本主題會說明在服務方法實作期間模擬呼叫者的服務模型支援。 同時會討論有關模擬和 SOAP 安全性以及 WCF 選項在這些案例中的常見部署案例。  
  
 使用 SOAP 安全性時，本主題會著重在模擬與 WCF 的委派。 您也可以使用模擬與委派搭配 WCF 使用傳輸安全性時中所述[使用模擬搭配傳輸安全性](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)。  
  
## <a name="two-methods"></a>兩個方法  
 WCF SOAP 安全性包含兩個不同的方法來執行模擬。 所使用的方法會取決於繫結。 一個是從安全性支援提供者介面 (SSPI) 或 Kerberos 驗證取得之 Windows 權杖進行的模擬，該權杖後來會快取到服務上。 第二個則是從 Kerberos 延伸取得之 Windows 權杖進行的模擬，統稱為「 *Service-for-User* 」(S4U)。  
  
### <a name="cached-token-impersonation"></a>快取權杖模擬  
 您可以用下列項目來執行快取權杖模擬：  
  
-   具有 Windows 用戶端認證的<xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>及 <xref:System.ServiceModel.NetTcpBinding> 。  
  
-   <xref:System.ServiceModel.BasicHttpBinding> ，其 <xref:System.ServiceModel.BasicHttpSecurityMode> 設定為 <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> 認證或是其他任何標準繫結，繫結是指用戶端會在其中提供可由服務用來對應至有效 Windows 帳戶的使用者名稱認證。  
  
-   任何使用 Windows 用戶端認證，而且 <xref:System.ServiceModel.Channels.CustomBinding> 已設定為 `requireCancellation` 的 `true`  (此屬性可在下列類別上使用：<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>、<xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters> 及 <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>)。如果此繫結上有使用安全對話，這時也必須將 `requireCancellation` 屬性設定為 `true`。  
  
-   用戶端在其中提供使用者名稱認證的任何 <xref:System.ServiceModel.Channels.CustomBinding> 。 如果此繫結上有使用安全對話，這時也必須將 `requireCancellation` 屬性設定為 `true`。  
  
### <a name="s4u-based-impersonation"></a>S4U 架構模擬  
 您可以用下列項目來執行 S4U 架構模擬：  
  
-   <xref:System.ServiceModel.WSHttpBinding>、 <xref:System.ServiceModel.WSDualHttpBinding>及 <xref:System.ServiceModel.NetTcpBinding> ，包含可讓服務用來對應至有效 Windows 帳戶的憑證用戶端認證。  
  
-   任何使用 Windows 用戶端認證，而且 <xref:System.ServiceModel.Channels.CustomBinding> 屬性已設定為 `requireCancellation` 的 `false`。  
  
-   任何使用使用者名稱或 Windows 用戶端認證以及安全對話，而且 <xref:System.ServiceModel.Channels.CustomBinding> 屬性已設定為 `requireCancellation` 的 `false`。  
  
 服務可以模擬用戶端的程度，取決於服務在嘗試模擬時所擁有的權限、所使用的模擬類型，以及用戶端允許的可能模擬程度。  
  
> [!NOTE]
>  當用戶端和服務在相同電腦上執行，而且用戶端正以系統帳戶執行時 (例如， `Local System` 或 `Network Service`)，用戶端就無法在安全工作階段是以可設定狀態之安全性內容權杖所建立的情況下進行模擬。 Windows Form 或主控台應用程式 (Console Application) 一般都會以目前登入的帳戶執行，因此依預設可以模擬該帳戶。 但當用戶端是 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 頁面，而且該頁面是裝載於 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 或 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]中時，根據預設，用戶端不會以 `Network Service` 帳戶執行。 所有支援安全工作階段的系統提供繫結，根據預設，都會使用沒有狀態 (Stateless) 的安全性內容權杖 (SCT)。 不過，如果用戶端是 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 頁面，而且已使用含有可設定狀態之 SCT 的安全工作階段，就無法模擬該用戶端。 如需有關在安全工作階段中使用具狀態的 Sct 的詳細資訊，請參閱[How to： 建立安全工作階段的安全性內容權杖](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)。  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>使用服務方法的模擬：宣告式模型  
 大多數模擬狀況都牽涉到在呼叫端內容中執行服務方法。 WCF 提供的模擬功能，以簡化這項執行工作允許使用者指定模擬需求，在<xref:System.ServiceModel.OperationBehaviorAttribute>屬性。 例如，下列程式碼中，WCF 基礎結構模擬呼叫者之前執行`Hello`方法。 資源的存取控制清單 (ACL) 必須允許呼叫者存取權限，任何存取 `Hello` 方法內部原生資源的嘗試才能繼續。 若要啟用模擬，請將 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> 屬性設定為其中一個 <xref:System.ServiceModel.ImpersonationOption> 例舉值，也就是 <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> 或 <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>，如下列範例所示。  
  
> [!NOTE]
>  當服務的認證權限高於遠端用戶端時，而 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> 屬性已設定為 <xref:System.ServiceModel.ImpersonationOption.Allowed>，便會使用服務的認證。 也就是說，如果低權限的使用者提供其認證，較高權限的服務會以服務的認證來執行方法，而且可以使用低權限使用者透過其他方法也無法使用的資源。  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 WCF 基礎結構才能模擬呼叫端呼叫端會使用可以對應至 Windows 使用者帳戶的認證驗證。 如果服務是設定成使用無法對應至 Windows 帳戶的認證來進行驗證，該服務方法就不會執行。  
  
> [!NOTE]
>  在 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]上，如果有建立可設定狀態的 SCT，模擬便會失敗，並會造成 <xref:System.InvalidOperationException>。 如需詳細資訊，請參閱[不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)。  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>使用服務方法的模擬：命令式模型  
 有時候呼叫者並不需要模擬整個服務，而只需要模擬服務的部份即可運作。 在此情況下，請從服務方法內取得呼叫者的 Windows 身分識別，而且以命令方式執行模擬。 使用 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> 的 <xref:System.ServiceModel.ServiceSecurityContext> 屬性傳回 <xref:System.Security.Principal.WindowsIdentity> 類別的執行個體，並先呼叫 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> 方法，再使用該執行個體，即可完成這項執行。  
  
> [!NOTE]
>  請務必使用 Visual Basic`Using`陳述式或 C#`using`陳述式自動還原此模擬動作。 如果您不要使用陳述式，或如果您使用 Visual Basic 或 C# 以外的程式設計語言，請確定還原此模擬等級。 若是沒有做到這點，可能就會促使阻絕服務攻擊和提高權限攻擊的發生。  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>所有服務方法的模擬  
 在某些情況下，您必須在呼叫者內容中執行服務的所有方法。 這時並非明確地針對各個方法啟用這項功能，而是使用 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>。 如下列程式碼所示，將 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> 屬性設定為 `true`。 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 是從 <xref:System.ServiceModel.ServiceHost> 類別的行為集合中加以擷取。 同時請注意，套用至每個方法之 `Impersonation` 的 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性，也必須設定為 <xref:System.ServiceModel.ImpersonationOption.Allowed> 或 <xref:System.ServiceModel.ImpersonationOption.Required>。  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 下表描述的所有可能組合的 WCF 行為`ImpersonationOption`和`ImpersonateCallerForAllServiceOperations`。  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|行為|  
|---------------------------|------------------------------------------------|--------------|  
|必要|N/A|WCF 模擬呼叫者|  
|Allowed|False|WCF 不會模擬呼叫者|  
|Allowed|true|WCF 模擬呼叫者|  
|NotAllowed|False|WCF 不會模擬呼叫者|  
|NotAllowed|true|不允許。 (擲回 <xref:System.InvalidOperationException> )。|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>從 Windows 認證和快取權杖模擬取得的模擬等級  
 在某些案例中，若是使用 Windows 用戶端認證，用戶端只能部分控制服務執行的模擬等級。 當用戶端指定 Anonymous 模擬等級時會形成一種案例。 而以快取權杖執行模擬時會發生另一種案例。 設定 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 類別的 <xref:System.ServiceModel.Security.WindowsClientCredential> 屬性 (可以當做泛型 <xref:System.ServiceModel.ChannelFactory%601> 類別的屬性進行存取)，即可做到這點。  
  
> [!NOTE]
>  指定 Anonymous 模擬等級時會導致用戶端以匿名方式登入服務。 因此，無論是否有執行模擬，服務一定會允許匿名登入。  
  
 用戶端可以將模擬等級指定為 <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>、 <xref:System.Security.Principal.TokenImpersonationLevel.Identification>、 <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>或 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>。 這時只會產生指定等級的權杖，如下列程式碼所示。  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 下表會指定在從快取權杖模擬時，服務所取得的模擬等級。  
  
|`AllowedImpersonationLevel` 值|服務具有 `SeImpersonatePrivilege`|服務和用戶端能夠委派|快取權杖 `ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|匿名|[是]|N/A|模擬|  
|匿名|否|N/A|識別|  
|識別|N/A|N/A|識別|  
|模擬|[是]|N/A|模擬|  
|模擬|否|N/A|識別|  
|委派|[是]|[是]|委派|  
|委派|[是]|否|模擬|  
|委派|否|N/A|識別|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>從使用者名稱認證和快取權杖模擬取得的模擬等級  
 藉由傳遞服務，其使用者名稱和密碼，用戶端可讓使用者，這相當於設定的身分登入的 WCF`AllowedImpersonationLevel`屬性<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>。 (`AllowedImpersonationLevel` 可在 <xref:System.ServiceModel.Security.WindowsClientCredential> 和 <xref:System.ServiceModel.Security.HttpDigestClientCredential> 類別上使用)。下表提供當服務接收使用者名稱認證時所取得的模擬等級。  
  
|`AllowedImpersonationLevel`|服務具有 `SeImpersonatePrivilege`|服務和用戶端能夠委派|快取權杖 `ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|N/A|[是]|[是]|委派|  
|N/A|[是]|否|模擬|  
|N/A|否|N/A|識別|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>從 S4U 架構模擬取得的模擬等級  
  
|服務具有 `SeTcbPrivilege`|服務具有 `SeImpersonatePrivilege`|服務和用戶端能夠委派|快取權杖 `ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|[是]|[是]|N/A|模擬|  
|[是]|否|N/A|識別|  
|否|N/A|N/A|識別|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>將用戶端憑證對應至 Windows 帳戶  
 用戶端本身可以利用憑證讓自己通過對服務的驗證，並且讓服務將用戶端透過 Active Directory 對應到現有的帳戶。 下列 XML 示範如何對服務進行設定以對應憑證。  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="MapToWindowsAccount">  
      <serviceCredentials>  
        <clientCertificate>  
          <authentication mapClientCertificateToWindowsAccount="true" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 下列程式碼會示範如何設定服務。  
  
```  
// Create a binding that sets a certificate as the client credential type.  
WSHttpBinding b = new WSHttpBinding();  
b.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a service host that maps the certificate to a Windows account.  
Uri httpUri = new Uri("http://localhost/Calculator");  
ServiceHost sh = new ServiceHost(typeof(HelloService), httpUri);  
sh.Credentials.ClientCertificate.Authentication.MapClientCertificateToWindowsAccount = true;  
```  
  
## <a name="delegation"></a>委派  
 若要委派給後端服務，服務必須使用用戶端的 Windows 身分識別，對後端服務執行多支線 (Multi-leg) Kerberos 驗證 (無 NTLM 後援的 SSPI) 或 Kerberos 直接驗證。 若要委派給後端服務，請建立 <xref:System.ServiceModel.ChannelFactory%601> 和通道，然後在模擬用戶端時透過通道通訊。 透過這種委派，後端服務離前端服務的距離取決於前端服務達成的模擬等級。 當模擬等級為 <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>時，前端和後端服務必須在相同電腦上執行。 當模擬等級為 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>時，前端和後端服務可以在不同電腦或相同電腦上執行。 啟用委派等級模擬需要 Windows 網域原則已設定，才能允許委派。 如需設定 Active Directory 以支援委派的詳細資訊，請參閱 [啟用委派驗證](http://go.microsoft.com/fwlink/?LinkId=99690)(英文)。  
  
> [!NOTE]
>  當用戶端使用對應至後端服務 Windows 帳戶的使用者名稱和密碼驗證前端服務時，前端服務可以重複使用用戶端的使用者名稱和密碼來驗證後端服務。 這是身分識別流動特別強大的形式，因為將使用者名稱和密碼傳遞至後端服務可讓後端服務執行模擬，但它不會構成委派，因為並未使用 Kerberos。 委派上的 Active Directory 控制項不會套用至使用者名稱和密碼驗證。  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>模擬等級功能的委派能力  
  
|模擬等級|服務可以執行跨處理序委派|服務可以執行跨電腦委派|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|否|否|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|是|否|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|是|[是]|  
  
 下列程式碼範例示範如何使用委派。  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>如何設定應用程式使用限制委派  
 在您可以使用限制委派之前，傳送者、接收者和網域控制站必須先設定為可使用限制委派。 下列程序列出啟用限制委派的步驟。 如需委派和限制委派之間差異的詳細資訊，請參閱 [Windows Server 2003 Kerberos 延伸](http://go.microsoft.com/fwlink/?LinkId=100194) (英文) 部分中有關限制的討論。  
  
1.  在網域控制站上，清除用戶端應用程式執行所在之帳戶的 [ **這是機密帳戶，無法委派** ] 核取方塊。  
  
2.  在網域控制站上，選取用戶端應用程式執行所在之帳戶的 [ **帳戶受信任可以委派** ] 核取方塊。  
  
3.  在網域控制站上，按一下 [ **信任電腦以便進行委派** ] 選項，將中介層電腦設定為受信任，可進行委派。  
  
4.  在網域控制站上，按一下 [ **信任這台電腦所委派的特定服務** ] 選項，將中介層電腦設定為使用限制委派。  
  
 如需設定限制委派的詳細指示，請參閱 MSDN 的下列主題：  
  
-   [疑難排解 Kerberos 委派](http://go.microsoft.com/fwlink/?LinkId=36724)  
  
-   [Kerberos 通訊協定轉換與限制委派 (英文)](http://go.microsoft.com/fwlink/?LinkId=36725)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>  
 <xref:System.ServiceModel.ImpersonationOption>  
 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>  
 <xref:System.ServiceModel.ServiceSecurityContext>  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.ChannelFactory%601>  
 <xref:System.Security.Principal.TokenImpersonationLevel.Identification>  
 [使用模擬搭配傳輸安全性](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 [模擬用戶端](../../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [如何：在服務上模擬用戶端](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
