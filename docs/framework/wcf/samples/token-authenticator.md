---
title: "權杖驗證器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76f3913f5cf6166793cb6f95ef3658c24e2453b4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="token-authenticator"></a>權杖驗證器
這個範例示範如何實作自訂權杖驗證器。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 的權杖驗證器用於驗證搭配訊息使用的權杖、確認其前後一致，以及驗證與權杖關聯的身分識別。  
  
 自訂權杖驗證器適用於各種情況，例如：  
  
-   您想要覆寫與權杖有關聯的預設驗證機制。  
  
-   您正在建置自訂權杖。  
  
 本範例示範以下項目:  
  
-   用戶端如何透過使用者名稱/密碼組進行驗證。  
  
-   伺服器如何使用自訂權杖驗證器驗證用戶端認證。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務程式碼如何與自訂權杖驗證器結合在一起。  
  
-   如何使用伺服器的 X.509 憑證來驗證伺服器。  
  
 這個範例還會示範如何在自訂權杖驗證程序之後，從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 存取呼叫者的身分識別。  
  
 服務會公開 (Expose) 單一的端點來與已使用組態檔 App.config 定義之服務進行通訊。 端點是由位址、繫結及合約所組成。 繫結已設定成標準 `wsHttpBinding`，以及將安全性模式設為訊息 (`wsHttpBinding` 的預設模式)。 這個範例會將標準 `wsHttpBinding` 設定為使用用戶端使用者名稱驗證。 服務也會使用 `serviceCredentials` 行為來設定服務憑證。 `securityCredentials` 行為允許您指定服務憑證。 服務憑證是由用戶端用來驗證服務並提供訊息保護。 下列組態會參考在安裝範例期間所安裝的 localhost 憑證，如下列安裝指示中所述。  
  
```xml  
<system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- configure base address provided by host -->  
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
          The serviceCredentials behavior allows one to define a service certificate.  
          A service certificate is used by a client to authenticate the service and provide message protection.  
          This configuration references the "localhost" certificate installed during the setup instructions.  
....        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 用戶端的端點組態是由組態名稱、服務端點的絕對位址、繫結和合約所組成。 用戶端繫結是透過適當的 `Mode` 和 `clientCredentialType` 所設定。  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint name=""  
                address="http://localhost:8000/servicemodelsamples/service"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
```  
  
 用戶端實作會設定要使用的使用者名稱和密碼。  
  
```  
static void Main()  
{  
     ...  
     client.ClientCredentials.UserNamePassword.UserName = username;  
     client.ClientCredentials.UserNamePassword.Password = password;  
     ...  
}  
```  
  
## <a name="custom-token-authenticator"></a>自訂權杖驗證器  
 使用下列步驟來建立自訂權杖驗證器：  
  
1.  撰寫自訂權杖驗證器。  
  
     範例會實作自訂權杖驗證器，以驗證使用者名稱是否具備有效的電子郵件格式。 此驗證器會衍生 <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>。 這個類別中最重要的方法是 <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>。 在這個方法中，驗證器會確認使用者名稱的格式有效，以及主機名稱不是來自惡意網域。 如果兩個條件都符合，便會傳回 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 執行個體的唯讀集合，而這個集合則用來提供表示儲存於使用者名稱權杖內之資訊的宣告。  
  
    ```  
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)  
    {  
        if (!ValidateUserNameFormat(userName))  
            throw new SecurityTokenValidationException("Incorrect UserName format");  
  
        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));  
        List<IIdentity> identities = new List<IIdentity>(1);  
        identities.Add(new GenericIdentity(userName));  
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);  
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));  
        return policies.AsReadOnly();  
    }  
    ```  
  
2.  提供由自訂權杖驗證器傳回的授權原則。  
  
     這個範例自行提供名為 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 的 `UnconditionalPolicy` 實作，此實作會傳回一組在已於建構函式中傳遞給它的宣告和身分識別。  
  
    ```  
    class UnconditionalPolicy : IAuthorizationPolicy  
    {  
        String id = Guid.NewGuid().ToString();  
        ClaimSet issuer;  
        ClaimSet issuance;  
        DateTime expirationTime;  
        IList<IIdentity> identities;  
  
        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)  
        {  
            if (issuer == null)  
                throw new ArgumentNullException("issuer");  
            if (issuance == null)  
                throw new ArgumentNullException("issuance");  
  
            this.issuer = issuer;  
            this.issuance = issuance;  
            this.identities = identities;  
            this.expirationTime = expirationTime;  
        }  
  
        public string Id  
        {  
            get { return this.id; }  
        }  
  
        public ClaimSet Issuer  
        {  
            get { return this.issuer; }  
        }  
  
        public DateTime ExpirationTime  
        {  
            get { return this.expirationTime; }  
        }  
  
        public bool Evaluate(EvaluationContext evaluationContext, ref object state)  
        {  
            evaluationContext.AddToTarget(this, this.issuance);  
  
            if (this.identities != null)  
            {  
                object value;  
                IList<IIdentity> contextIdentities;  
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))  
                {  
                    contextIdentities = new List<IIdentity>(this.identities.Count);  
                    evaluationContext.Properties.Add("Identities", contextIdentities);  
                }  
                else  
                {  
                    contextIdentities = value as IList<IIdentity>;  
                }  
                foreach (IIdentity identity in this.identities)  
                {  
                    contextIdentities.Add(identity);  
                }  
            }  
  
            evaluationContext.RecordExpirationTime(this.expirationTime);  
            return true;  
        }  
    }  
    ```  
  
3.  撰寫自訂安全性權杖管理員。  
  
     您可以使用 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 來為特定 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 物件 (這會在 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 方法中傳遞給前者) 建立 `CreateSecurityTokenAuthenticator`。 安全性權杖管理員也會用來建立權杖提供者與權杖序列化程式，但是這些不在本範例的討論範圍。 在這個範例中，自訂安全性權杖管理員繼承自 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 類別，並且會覆寫 `CreateSecurityTokenAuthenticator` 方法，以便在傳遞的權杖需求表示要求使用者名稱驗證器時傳回自訂使用者名稱權杖驗證器。  
  
    ```  
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager  
    {  
        MyUserNameCredential myUserNameCredential;  
  
        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)  
            : base(myUserNameCredential)  
        {  
            this.myUserNameCredential = myUserNameCredential;  
        }  
  
        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)  
        {  
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)  
            {  
                outOfBandTokenResolver = null;  
                return new MyTokenAuthenticator();  
            }  
            else  
            {  
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);  
            }  
        }  
    }  
    ```  
  
4.  撰寫自訂服務認證。  
  
     服務認證類別可用來表示針對服務所設定的認證，並建立用來取得權杖驗證器、權杖提供者和權杖序列化程式的安全性權杖管理員。  
  
    ```  
    public class MyUserNameCredential : ServiceCredentials  
    {  
  
        public MyUserNameCredential()  
            : base()  
        {  
        }  
  
        protected override ServiceCredentials CloneCore()  
        {  
            return new MyUserNameCredential();  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            return new MySecurityTokenManager(this);  
        }  
  
    }  
    ```  
  
5.  將服務設定為使用自訂服務認證。  
  
     為了讓服務能夠使用自訂服務認證，範例已在擷取預先設定於預設服務認證中的服務憑證之後刪除預設服務認證類別，然後將新的服務認證執行個體設定為使用預先設定的服務憑證，再將這個新服務認證執行個體新增至服務行為。  
  
    ```  
    ServiceCredentials sc = serviceHost.Credentials;  
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;  
    MyUserNameCredential serviceCredential = new MyUserNameCredential();  
    serviceCredential.ServiceCertificate.Certificate = cert;  
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
    serviceHost.Description.Behaviors.Add(serviceCredential);  
    ```  
  
 若要顯示呼叫者的資訊，您可以使用 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>，如下列程式碼所示。 <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 包含有關目前呼叫者的宣告資訊。  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
            ServiceSecurityContext.Current.PrimaryIdentity.Name);  
     return;  
}  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
## <a name="setup-batch-file"></a>設定批次檔  
 本範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的自我裝載應用程式。 這個批次檔必須經過修改才能跨電腦運作，或在非裝載的情況下運作。  
  
 下面提供批次檔的各區段簡要概觀，讓您將批次檔修改為可在適當的組態下執行。  
  
-   建立伺服器憑證。  
  
     下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。 `%SERVER_NAME%` 變數會指定伺服器名稱。 您可以變更這個變數來指定自己的伺服器名稱。 這個批次檔中的預設值為 localhost。  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   將伺服器憑證安裝至用戶端的受信任憑證存放區中。  
  
     Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。 這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。 如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  安裝批次檔是設計用來從 Windows SDK 命令提示字元執行。 它要求 MSSDK 環境變數指向安裝 SDK 的目錄。 這個環境變數是自動在 Windows SDK 命令提示字元中設定。  
  
#### <a name="to-set-up-and-build-the-sample"></a>若要設定和建置範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>若要在同一部電腦上執行範例  
  
1.  在使用系統管理員權限開啟的 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元內部，執行範例安裝資料夾中的 Setup.bat。 這會安裝執行範例所需的所有憑證。  
  
    > [!NOTE]
    >  Setup.bat 批次檔是設計用來從 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元執行。 在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元中設定的 PATH 環境變數會指向包含 Setup.bat 指令碼所需之可執行檔的目錄。  
  
2.  從 service\bin 啟動 service.exe。  
  
3.  從 \client\bin 啟動 client.exe。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
4.  如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
#### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例  
  
1.  在服務電腦上為服務二進位碼檔案建立一個目錄。  
  
2.  將服務程式檔複製到服務電腦上的服務目錄。 同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。  
  
3.  您伺服器憑證的主體名稱必須包含電腦的完整網域名稱。 必須更新服務 App.config 檔以反映這個新憑證名稱。 只要將 `%SERVER_NAME%` 變數設定為服務執行所在之電腦的完整主機名稱，就可以使用 Setup.bat 建立憑證。 請注意，您必須在使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 Setup.bat 檔案。  
  
4.  將伺服器憑證複製到用戶端的 CurrentUser-TrustedPeople 存放區中。 只有在伺服器憑證是由用戶端受信任的簽發者發行時才需要這麼做。  
  
5.  在服務電腦的 App.config 檔中變更基底位址的值，以指定完整電腦名稱而不要指定 localhost。  
  
6.  在服務電腦上，從命令提示字元執行 service.exe。  
  
7.  將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。  
  
8.  在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。  
  
9. 在用戶端電腦上，從命令提示字元啟動 Client.exe。  
  
10. 如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
#### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
1.  當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
  
## <a name="see-also"></a>請參閱
