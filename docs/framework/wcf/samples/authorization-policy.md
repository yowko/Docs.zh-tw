---
title: 授權原則
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 9b73eea1f51454dd82ba577c4d4d5fd5a1c0efd4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990194"
---
# <a name="authorization-policy"></a>授權原則

此範例示範如何實作自訂宣告授權原則以及關聯的自訂服務授權管理員。 當服務對服務作業執行宣告架構的存取檢查，以及在執行存取檢查前便授予呼叫者特定權限時，這個方法就會很有用處。 此範例同時說明新增宣告的處理序，以及對最後宣告集的存取檢查處理序。 用戶端與伺服器之間的所有應用程式訊息都會經過簽署及加密。 根據預設，使用 `wsHttpBinding` 繫結時，會使用用戶端所提供的使用者名稱和密碼來登入有效的 Windows NT 帳戶。 此範例示範如何使用自訂 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 來驗證用戶端。 此外，此範例會說明用戶端如何使用 X.509 憑證來向服務進行驗證。 此範例說明 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 和 <xref:System.ServiceModel.ServiceAuthorizationManager> 的實作 (此實作會針對特定使用者將存取權限授予特定的服務方法)。 這個範例是以[訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)為基礎，但是會示範如何在呼叫之前<xref:System.ServiceModel.ServiceAuthorizationManager>執行宣告轉換。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。

 這個範例所示範的作業摘要如下：

- 用戶端可以使用使用者名稱與密碼來進行驗證。

- 用戶端可以使用 X.509 憑證進行驗證。

- 伺服器會向自訂 `UsernamePassword` 驗證器驗證用戶端認證。

- 伺服器是使用該伺服器的 X.509 憑證來驗證的。

- 伺服器可以使用 <xref:System.ServiceModel.ServiceAuthorizationManager> 來控制服務中特定方法的存取。

- 如何實作 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>。

服務會公開兩個端點，以便與使用組態檔 App.config 定義的服務進行通訊。每個端點是由位址、繫結及合約所組成。 其中一個繫結使用標準 `wsHttpBinding` 繫結 (使用 WS-Security 和用戶端使用者名稱驗證) 來設定。 另一個繫結使用標準 `wsHttpBinding` 繫結 (使用 WS-Security 和用戶端憑證驗證) 來設定。 [ \<> 的行為](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)會指定要將使用者認證用於服務驗證。 伺服器憑證必須包含`SubjectName`屬性的相同值，做為[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)中的`findValue`屬性。

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <!-- configure base address provided by host -->
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>
        </baseAddresses>
      </host>
      <!-- use base address provided by host, provide two endpoints -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <endpoint address="certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding2"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
    <message clientCredentialType="UserName" />
        </security>
      </binding>
      <!-- X509 certificate binding -->
      <binding name="Binding2">
        <security mode="Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior" >
        <serviceDebug includeExceptionDetailInFaults ="true" />
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.
          -->
          <clientCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
          <!--
          The serviceAuthorization behavior allows one to specify custom authorization policies.
          -->
          <authorizationPolicies>
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />
          </authorizationPolicies>
        </serviceAuthorization>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

每個用戶端的端點組態是由組態名稱、服務端點的絕對位址、繫結和合約所組成。 用戶端系結會設定為使用適當的安全性模式，如此案例中的[ \<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)和`clientCredentialType` [ \<訊息 >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)中所指定。

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
            address="http://localhost:8001/servicemodelsamples/service/username"
    binding="wsHttpBinding"
    bindingConfiguration="Binding1"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" >
      </endpoint>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
                        address="http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
            bindingConfiguration="Binding2"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
        <!-- X509 certificate binding -->
        <binding name="Binding2">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
    </wsHttpBinding>
    </bindings>

    <behaviors>
      <behavior name="ClientCertificateBehavior">
        <clientCredentials>
          <serviceCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust
            means that if the certificate
            is in the user's Trusted People store, then it will be
            trusted without performing a
            validation of the certificate's issuer chain. This setting
            is used here for convenience so that the
            sample can be run without having to have certificates
            issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust.
            The security implications of this
            setting should be carefully considered before using
            PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode = "PeerOrChainTrust" />
          </serviceCertificate>
        </clientCredentials>
      </behavior>
    </behaviors>

  </system.serviceModel>
```

針對使用者名稱架構的端點，用戶端實作會設定要使用的使用者名稱和密碼。

```csharp
// Create a client with Username endpoint configuration
CalculatorClient client1 = new CalculatorClient("Username");

client1.ClientCredentials.UserName.UserName = "test1";
client1.ClientCredentials.UserName.Password = "1tset";

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client1.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client1.Close();
```

針對憑證架構的端點，用戶端實作會設定要使用的用戶端憑證。

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client2 = new CalculatorClient("Certificate");

client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client2.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client2.Close();
```

此範例使用自訂 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 來驗證使用者名稱和密碼。 此範例會實作衍生自 `MyCustomUserNamePasswordValidator` 的 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>。 如需詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 相關文件。 為了示範與 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的整合，此自訂驗證器範例會實作 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法以接受使用者名稱/密碼組，以使其中的使用者名稱符合下列程式碼中所示的密碼。

```csharp
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator
{
  // This method validates users. It allows in two users,
  // test1 and test2 with passwords 1tset and 2tset respectively.
  // This code is for illustration purposes only and
  // MUST NOT be used in a production environment because it
  // is NOT secure.
  public override void Validate(string userName, string password)
  {
    if (null == userName || null == password)
    {
      throw new ArgumentNullException();
    }

    if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
    {
      throw new SecurityTokenException("Unknown Username or Password");
    }
  }
}
```

一旦驗證程式在服務程式碼中實作，服務主機就必須收到要使用的驗證程式執行個體的相關通知。 這會使用下列程式碼來完成：

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

或者，您也可以在設定中執行相同的動作：

```xml
<behavior ...>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

Windows Communication Foundation （WCF）提供以宣告為基礎的豐富模型，以執行存取檢查。 <xref:System.ServiceModel.ServiceAuthorizationManager> 物件會被用來執行存取檢查並判斷與用戶端相關的宣告是否能夠滿足存取服務方法所需的必要需求。

基於示範的目的，這個範例會示範的執行<xref:System.ServiceModel.ServiceAuthorizationManager> <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>方法，以允許使用者根據型`http://example.com/claims/allowedoperation`別的宣告來存取方法，其值是作業的動作 URI允許呼叫。

```csharp
public class MyServiceAuthorizationManager : ServiceAuthorizationManager
{
  protected override bool CheckAccessCore(OperationContext operationContext)
  {
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;
    Console.WriteLine("action: {0}", action);
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)
    {
      if ( cs.Issuer == ClaimSet.System )
      {
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))
        {
          Console.WriteLine("resource: {0}", c.Resource.ToString());
          if (action == c.Resource.ToString())
            return true;
        }
      }
    }
    return false;
  }
}
```

一旦實作了自訂 <xref:System.ServiceModel.ServiceAuthorizationManager>，就必須告知服務主機要使用的 <xref:System.ServiceModel.ServiceAuthorizationManager>。 執行方式如下列程式碼所示。

```xml
<behavior ...>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

要實作的主要 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 方法為 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> 方法。

```csharp
public class MyAuthorizationPolicy : IAuthorizationPolicy
{
    string id;

    public MyAuthorizationPolicy()
    {
    id =  Guid.NewGuid().ToString();
    }

    public bool Evaluate(EvaluationContext evaluationContext,
                                            ref object state)
    {
        bool bRet = false;
        CustomAuthState customstate = null;

        if (state == null)
        {
            customstate = new CustomAuthState();
            state = customstate;
        }
        else
            customstate = (CustomAuthState)state;
        Console.WriteLine("In Evaluate");
        if (!customstate.ClaimsAdded)
        {
           IList<Claim> claims = new List<Claim>();

           foreach (ClaimSet cs in evaluationContext.ClaimSets)
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,
                                         Rights.PossessProperty))
                  foreach (string s in
                        GetAllowedOpList(c.Resource.ToString()))
                  {
                       claims.Add(new
               Claim("http://example.com/claims/allowedoperation",
                                    s, Rights.PossessProperty));
                            Console.WriteLine("Claim added {0}", s);
                      }
                   evaluationContext.AddClaimSet(this,
                           new DefaultClaimSet(this.Issuer,claims));
                   customstate.ClaimsAdded = true;
                   bRet = true;
                }
         else
         {
              bRet = true;
         }
         return bRet;
     }
...
}
```

前一段程式碼說明 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> 方法會檢查並確定未新增任何會影響處理的新宣告，然後再新增特定宣告。 允許的宣告是從 `GetAllowedOpList` 方法取得，此方法經過實作，會傳回可供使用者執行的特定作業清單。 授權原則會新增宣告以便處理特定作業。 此宣告稍後會由 <xref:System.ServiceModel.ServiceAuthorizationManager> 使用，以執行存取檢查決策。

一旦實作了自訂 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>，就必須告知服務主機要使用的授權原則。

```xml
<serviceAuthorization ...>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 用戶端會順利呼叫 Add、Subtract 和 Multiple 方法，並在嘗試呼叫 Divide 方法時取得「拒絕存取」訊息。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。

## <a name="setup-batch-file"></a>設定批次檔

本範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的自我裝載應用程式。

下面提供批次檔的各區段簡要概觀，讓批次檔得以修改為在適當的組態下執行：

- 建立伺服器憑證。

    下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。 %SERVER_NAME% 變數會指定伺服器名稱。 您可以變更這個變數來指定自己的伺服器名稱。 預設值為 localhost。

    ```bat
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

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- 建立用戶端憑證。

    下列 Setup.bat 批次檔中的程式行會建立要使用的用戶端憑證。 %USER_NAME% 變數會指定伺服器名稱。 這個值會設定為 "test1"，因為這是 `IAuthorizationPolicy` 會尋找的名稱。 如果變更了 %USER_NAME% 的值，您就必須在 `IAuthorizationPolicy.Evaluate` 方法中變更對應的值。

    憑證會儲存在 CurrentUser 存放區位置下的 My (Personal) 存放區中。

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- 將用戶端憑證安裝至伺服器的受信任憑證存放區中。

    Setup.bat 批次檔中的下列程式行會將用戶端憑證複製到受信任人的存放區。 這是必要步驟，因為伺服器系統並未隱含信任 Makecert.exe 產生的憑證。 如果您已經有一個以信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將用戶端憑證填入伺服器憑證存放區的步驟。

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>若要設定和建置範例

1. 若要建立方案，請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。

2. 若要在單一或跨電腦的組態中執行本範例，請使用下列指示。

> [!NOTE]
> 如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以符合用戶端程式碼。

### <a name="to-run-the-sample-on-the-same-computer"></a>若要在同一部電腦上執行範例

1. 以系統管理員許可權開啟 Visual Studio 的開發人員命令提示字元，然後從範例安裝資料夾中執行*安裝程式 .bat* 。 這會安裝執行範例所需的所有憑證。

    > [!NOTE]
    > 安裝 .bat 批次檔是設計用來從 Visual Studio 的開發人員命令提示字元執行。 在開發人員命令提示字元中設定的 PATH 環境變數會 Visual Studio 指向包含*安裝程式*所需之可執行檔的目錄。

1. 從*service\bin*啟動 setup.exe。

1. 從啟動 Client.exe *\client\bin* 。 用戶端活動會顯示在用戶端主控台應用程式上。

如果用戶端和服務無法通訊，請參閱[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。

### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例

1. 在服務電腦上建立目錄。

2. 將服務程式檔案從 *\service\bin*複製到服務電腦上的目錄。 同時將 Setup.bat、Cleanup.bat、GetComputerName.vbs 和 ImportClientCert.bat 檔複製到服務電腦上。

3. 在用戶端電腦上為用戶端二進位碼檔案建立一個目錄。

4. 將用戶端程式檔複製到用戶端電腦上的用戶端目錄。 同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。

5. 在伺服器上，于`setup.bat service`開發人員命令提示字元中執行，Visual Studio 以系統管理員許可權開啟的。

    使用引數執行時，會建立具有電腦完整功能變數名稱的服務憑證，並將服務憑證匯出至名為 .cer 的檔案。 `setup.bat` `service`

6. 編輯*setup.exe*以反映新的憑證名稱（在`findValue` [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)的屬性中），這與電腦的完整功能變數名稱相同。 同時將\<服務中的**computername** >/\<baseAddresses > 元素從 localhost 變更為服務電腦的完整名稱。

7. 將*service .cer*檔案從服務目錄複寫到用戶端電腦上的用戶端目錄。

8. 在用戶端上， `setup.bat client`于使用系統管理員許可權開啟 Visual Studio 的開發人員命令提示字元中執行。

    使用引數執行會建立名為**test1**的用戶端憑證，並將用戶端憑證匯出至名為*client .cer*的檔案。 `client` `setup.bat`

9. 在用戶端電腦上的*machine.config*檔案中，變更端點的位址值以符合服務的新位址。 若要這麼做，請以伺服器的完整功能變數名稱取代**localhost** 。

10. 從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。

11. 在用戶端上，于開發人員命令提示字元中執行*importservicecert.bat* ，以 Visual Studio 以系統管理員許可權開啟的。

    這樣會將服務 .cer 檔案中的服務憑證匯入**CurrentUser-TrustedPeople**存放區。

12. 在伺服器上，于開發人員命令提示字元中執行*importclientcert.bat* ，以 Visual Studio 以系統管理員許可權開啟的。

    這會從用戶端 .cer 檔案將用戶端憑證匯入至**LocalMachine-TrustedPeople**存放區。

13. 在伺服器電腦上，從命令提示字元視窗啟動 Service.exe。

14. 在用戶端電腦上，從命令提示字元視窗啟動 Client.exe。

    如果用戶端和服務無法通訊，請參閱[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。

### <a name="clean-up-after-the-sample"></a>在範例之後清除

若要在範例之後進行清除，請在完成執行範例後，在 samples 資料夾中執行*清除。* 這樣會從憑證存放區中移除伺服器與用戶端憑證。

> [!NOTE]
> 跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。 如果您已執行跨電腦使用憑證的 WCF 範例，請務必清除已安裝在 CurrentUser-TrustedPeople 存放區中的服務憑證。 若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`例如： `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。
