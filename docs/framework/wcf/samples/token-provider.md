---
title: 權杖提供者
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: 9f008204c6ff8d3d134dbb17fc445b460f757f13
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038742"
---
# <a name="token-provider"></a>權杖提供者
這個範例會示範如何實作自訂權杖提供者。 Windows Communication Foundation (WCF) 中的權杖提供者是用來提供認證給安全性基礎結構。 一般而言，權杖提供者會檢查目標並發行適當的認證，讓安全性基礎結構能夠保護訊息的安全。 WCF 隨附預設的認證管理員權杖提供者。 WCF 也隨附于 CardSpace 權杖提供者。 自訂權杖提供者適用於下列情況：

- 如果您有這些權杖提供者無法使用的認證存放區。

- 如果您想要提供自己的自訂機制, 讓使用者在 WCF 用戶端架構使用認證時, 將詳細資料提供給該時間點時, 可以將認證轉換成。

- 如果您要建置自訂權杖。

 這個範例會示範如何建置自訂權杖提供者，以便將使用者的輸入轉換為不同的格式。

 簡而言之，這個範例示範下面的情形：

- 用戶端如何透過使用者名稱/密碼組進行驗證。

- 如何使用自訂權杖提供者設定用戶端。

- 伺服器如何搭配自訂 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> (驗證使用者名稱與密碼是否相符) 來使用密碼驗證用戶端認證。

- 用戶端如何使用伺服器的 X.509 憑證來驗證伺服器。

 這個範例也會示範如何在自訂權杖驗證程序之後存取呼叫者的身分識別。

 服務會公開 (Expose) 單一的端點來與已使用組態檔 App.config 定義之服務進行通訊。 端點是由位址、繫結及合約所組成。 繫結已設定成預設會使用訊息安全性的標準 `wsHttpBinding`。 這個範例會將標準 `wsHttpBinding` 設定為使用用戶端使用者名稱驗證。 服務也會使用 serviceCredentials 行為來設定服務憑證。 serviceCredentials 行為可以讓您設定服務憑證。 服務憑證是由用戶端用來驗證服務並提供訊息保護。 下列組態會參考在安裝範例期間所安裝的 localhost 憑證，如下列安裝指示中所述。

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
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
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 用戶端的端點組態是由組態名稱、服務端點的絕對位址、繫結和合約所組成。 用戶端繫結已設定了適當的 `Mode` 與訊息 `clientCredentialType`。

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

 下列步驟示範如何開發自訂權杖提供者, 並將它與 WCF 安全性架構整合:

1. 撰寫自訂權杖提供者。

     此範例會實作取得使用者名稱與密碼的自訂權杖提供者。 密碼必須符合這個使用者名稱。 這個自訂權杖提供者僅供示範之用，因此不建議用於真實世界。

     為了執行這個工作，自訂權杖提供者會衍生 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 類別並覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> 方法。 這個方法會建立並傳回新的 `UserNameSecurityToken`。

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2. 撰寫自訂安全性權杖管理員。

     此 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 會用來建立特定 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> (以 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 方法傳遞至該管理員) 的 `CreateSecurityTokenProvider`。 安全性權杖管理員也會用來建立權杖驗證器與權杖序列化程式，但是這些不在本範例的討論範圍。 在這個範例中，自訂安全性權杖管理員繼承自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別，並且會覆寫 `CreateSecurityTokenProvider` 方法，以便在傳遞的權杖需求表示要求使用者名稱提供者時傳回自訂使用者名稱權杖提供者。

    ```csharp
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3. 撰寫自訂用戶端憑證。

     用戶端認證類別會用來代表針對用戶端 Proxy 設定的認證，並且會建立用來取得權杖驗證器、權杖提供者以及權杖序列化程式的安全性權杖管理員。

    ```csharp
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4. 將用戶端設定成使用自訂用戶端認證。

     為了讓用戶端使用自訂用戶端認證，此範例會刪除預設用戶端認證類別，並提供新的用戶端認證類別。

    ```csharp
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 為了在服務端上顯示呼叫者的資訊，此時會使用 <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>，如下列程式碼範例所示。 <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 包含有關目前呼叫者的宣告資訊。

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。

## <a name="setup-batch-file"></a>設定批次檔
 這個範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的自我裝載應用程式。 這個批次檔必須經過修改才能跨電腦運作，或在非裝載的情況下運作。

 下面提供批次檔的各區段簡要概觀，讓批次檔得以修改為在適當的組態下執行：

- 建立伺服器憑證。

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

- 將伺服器憑證安裝至用戶端的受信任憑證存放區中。

     Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。 這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。 如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
> Setup.bat 批次檔是設計用來從 Windows SDK 命令提示字元執行。 它要求 MSSDK 環境變數指向安裝 SDK 的目錄。 這個環境變數是自動在 Windows SDK 命令提示字元中設定。

#### <a name="to-set-up-and-build-the-sample"></a>若要設定和建置範例

1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。

2. 若要建立方案, 請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。

#### <a name="to-run-the-sample-on-the-same-computer"></a>若要在同一部電腦上執行範例

1. 在以系統管理員許可權開啟的 Visual Studio 2012 命令提示字元內, 從範例安裝資料夾中執行安裝程式 .bat。 這會安裝執行範例所需的所有憑證。

    > [!NOTE]
    > 安裝 .bat 批次檔是設計用來從 Visual Studio 2012 命令提示字元執行。 在 Visual Studio 2012 命令提示字元中設定的 PATH 環境變數會指向包含安裝程式 .bat 腳本所需之可執行檔的目錄。  
  
2. 從 service\bin 啟動 service.exe。  
  
3. 從 \client\bin 啟動 Client.exe。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
4. 在使用者名稱提示中，輸入使用者名稱。  
  
5. 在密碼提示中，使用在使用者名稱提示中輸入的相同字串。  
  
6. 如果用戶端和服務無法通訊, 請參閱[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
#### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例  
  
1. 在服務電腦上為服務二進位碼檔案建立一個目錄。  
  
2. 將服務程式檔複製到服務電腦上的服務目錄。 同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。  
  
3. 您伺服器憑證的主體名稱必須包含電腦的完整網域名稱。 此 Service.exe.config 檔必須更新以反映這個新憑證名稱。 您可以修改 Setup.bat 批次檔來建立伺服器憑證。 請注意, 您必須從開發人員命令提示字元執行安裝 .bat 檔案, 才能以系統管理員許可權開啟 Visual Studio。 您必須將 `%SERVER_NAME%` 變數設定為用來裝載服務之電腦的完整主機名稱。  
  
4. 將伺服器憑證複製到用戶端的 CurrentUser-TrustedPeople 存放區中。 當伺服器憑證是由用戶端信任的簽發者發行時，您就不需要這麼做。  
  
5. 在服務電腦的 Service.exe.config 檔中變更基底位址的值，以指定完整電腦名稱而不要指定 localhost。  
  
6. 在服務電腦上，從命令提示字元執行 service.exe。  
  
7. 將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端電腦。  
  
8. 在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。  
  
9. 在用戶端電腦上，從命令提示字元視窗啟動 `Client.exe`。  
  
10. 如果用戶端和服務無法通訊, 請參閱[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
#### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
1. 當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
