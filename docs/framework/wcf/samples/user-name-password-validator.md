---
title: 使用者名稱密碼驗證程式
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 52c22660e56d63121181bdcb618e0bed598ca585
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773931"
---
# <a name="user-name-password-validator"></a>使用者名稱密碼驗證程式
這個範例會示範如何實作自訂的 UserNamePassword 驗證程式。 當內建 UserNamePassword 驗證模式都不符合應用程式需求時，這個驗證程式就很有用；例如，當使用者名稱/密碼組儲存在某些外部存放區時，例如資料庫中。 這個範例示範的服務具有可檢查兩組特定使用者名稱/密碼組的自訂驗證程式。 用戶端會使用這些使用者名稱/密碼組來向服務驗證。

> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
>  因為任何人都可以建構使用自訂驗證程式能接受之使用者名稱/密碼組的使用者名稱認證，所以服務的安全性會低於標準 UserNamePassword 驗證程式提供之預設行為的安全性。 標準 UserNamePassword 驗證程式會嘗試將提供的使用者名稱/密碼組對應至 Windows 帳戶，並在這個對應失敗時發生驗證失敗。 這個範例中的自訂 UserNamePassword 驗證程式「不得」用於實際執行程式碼 (Production Code) 中，這個驗證程式僅供說明用途。

 這個範例所示範的作業摘要如下：

-   用戶端可以透過使用者名稱權杖進行驗證。

-   伺服器會向自訂 UserNamePasswordValidator 驗證用戶端的認證，以及如何將使用者名稱與密碼驗證邏輯的自訂錯誤傳播至用戶端。

-   伺服器是使用該伺服器的 X.509 憑證來驗證的。

 服務會公開 (Expose) 單一的端點來與已使用組態檔 App.config 定義之服務進行通訊。端點是由位址、繫結及合約所組成。 繫結設定為標準`wsHttpBinding`經由預設使用 WS Securityand 使用者名稱驗證。 服務行為會指定 `Custom` 模式，以驗證用戶端使用者名稱/密碼組以及該驗證程式類別的類型。 行為也會使用 `serviceCertificate` 項目來指定伺服器憑證。 伺服器憑證必須包含相同的值，如`SubjectName`作為`findValue`中[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)。

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <!-- use host/baseAddresses to configure base address provided by host -->
      <host>
        <baseAddresses>
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />
        </baseAddresses>
      </host>
      <!-- use base address specified above, provide one endpoint -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- username binding -->
      <binding name="Binding">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceDebug includeExceptionDetailInFaults ="true"/>
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to
          specify a custom validator for username/password
          combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom"
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

 用戶端的端點組態是由組態名稱、服務端點的絕對位址、繫結和合約所組成。 用戶端繫結已設定了適當的模式與訊息 `clientCredentialType`。

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
address="http://localhost:8001/servicemodelsamples/service/username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
```

 用戶端實作會提示使用者輸入使用者名稱與密碼。

```
// Get the username and password
Console.WriteLine("Username authentication required.");
Console.WriteLine("Provide a username.");
Console.WriteLine("   Enter username: (test1)");
string username = Console.ReadLine();
Console.WriteLine("   Enter password:");
string password = "";
ConsoleKeyInfo info = Console.ReadKey(true);
while (info.Key != ConsoleKey.Enter)
{
    if (info.Key != ConsoleKey.Backspace)
    {
        if (info.KeyChar != '\0')
        {
            password += info.KeyChar;
        }
        info = Console.ReadKey(true);
    }
    else if (info.Key == ConsoleKey.Backspace)
    {
        if (password != "")
        {
            password = password.Substring(0, password.Length - 1);
        }
        info = Console.ReadKey(true);
    }
}
for (int i = 0; i < password.Length; i++)
{
    Console.Write("*");
}
Console.WriteLine();
// Create a proxy with Certificate endpoint configuration
CalculatorProxy proxy = new CalculatorProxy("Username")
try
{
  proxy.ClientCredentials.Username.Username = username;
  proxy.ClientCredentials.Username.Password = password;
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = proxy.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
  }
  catch (Exception e)
  {
      Console.WriteLine("Call failed:");
      while (e != null)
      {
          Console.WriteLine("\t{0}", e.Message);
          e = e.InnerException;
      }
      proxy.Abort();
  }
}
```

 這個範例會使用自訂 UserNamePasswordValidator 來驗證使用者名稱/密碼組。 此範例會實作衍生自 `CustomUserNamePasswordValidator` 的 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>。 如需詳細資訊，請參閱有關 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的文件。 這個特定自訂驗證程式範例會實作 `Validate` 方法，以接受兩組特定使用者名稱/密碼組，如下列程式碼所示。

```
public class CustomUserNameValidator : UserNamePasswordValidator
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
   throw new FaultException("Unknown Username or Incorrect Password");
   }
  }
 }
```

 一旦驗證程式在服務程式碼中實作，服務主機就必須收到要使用的驗證程式執行個體的相關通知。 這個動作是使用下列程式碼完成。

```
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 或者，您可以在組態中執行如下所示的動作。

```xml
<behaviors>
 <serviceBehaviors>
  <behavior name="CalculatorServiceBehavior">
  ...
   <serviceCredentials>
    <!--
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.
    -->
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 用戶端應該會成功呼叫所有方法。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。

## <a name="setup-batch-file"></a>設定批次檔
 本範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的自我裝載應用程式。 這個批次檔必須經過修改才能跨機器運作，或在非自動裝載的情況下運作。

 下面提供批次檔的各區段簡要概觀，讓將批次檔得以修改為在適當的組態下執行。

-   建立伺服器憑證：

     下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。 %SERVER_NAME% 變數會指定伺服器名稱。 您可以變更這個變數來指定自己的伺服器名稱。 預設值為 localhost。

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   將伺服器憑證安裝至用戶端的受信任憑證存放區中：

     Setup.bat 批次檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。 這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。 如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證存放區的步驟。

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>若要設定和建置範例

1. 若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。

2. 若要在單一或跨電腦的組態中執行本範例，請使用下列指示。

#### <a name="to-run-the-sample-on-the-same-machine"></a>若要在同一部機器上執行範例

1. 從範例安裝資料夾，在 Visual Studio 2012 的命令提示字元執行 Setup.bat。 這會安裝執行範例所需的所有憑證。

    > [!NOTE]
    >  Setup.bat 批次檔被設計來從 Visual Studio 2012 命令提示字元執行。 路徑環境變數設定在 Visual Studio 2012 命令提示字元會指向包含 Setup.bat 指令碼所需的可執行檔的目錄。  
  
2. 從 service\bin 啟動 Service.exe。  
  
3. 從 \client\bin 啟動 Client.exe。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
4. 如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
#### <a name="to-run-the-sample-across-machines"></a>若要跨機器執行範例  
  
1. 在服務機器上為服務二進位碼檔案建立一個目錄。  
  
2. 將服務程式檔複製到服務機器的服務目錄上。 同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務機器中。  
  
3. 您伺服器憑證的主體名稱必須包含機器的完整網域名稱。 伺服器的組態檔必須更新以反映這個新憑證名稱。  
  
4. 將伺服器憑證複製到用戶端的 CurrentUser-TrustedPeople 存放區中。 只有在伺服器憑證不是由受信任的簽發者發行時才需要這麼做。  
  
5. 在服務機器的 App.config 檔中變更基底位址的值，以指定完整機器名稱而不要指定 localhost。  
  
6. 在服務機器上，從命令提示視窗啟動 Service.exe。  
  
7. 將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端機器中。  
  
8. 在用戶端機器上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。  
  
9. 在用戶端機器上，從命令提示字元視窗啟動 Client.exe。  
  
10. 如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
#### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
1. 當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。 這樣會從憑證存放區中移除伺服器憑證。  
