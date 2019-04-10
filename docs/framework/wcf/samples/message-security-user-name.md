---
title: 訊息安全性使用者名稱
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 947ef3c2120377fe33e0062d1ed508ddda432314
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335318"
---
# <a name="message-security-user-name"></a>訊息安全性使用者名稱
這個範例會示範如何實作應用程式，該應用程式會對用戶端使用搭配使用者名稱驗證的 WS-Security，並要求使用伺服器之 X.509v3 憑證進行驗證的伺服器驗證。 用戶端與伺服器之間的所有應用程式訊息都會經過簽署及加密。 根據預設，用戶端提供的使用者名稱與密碼會用來登入有效的 Windows 帳戶。 此樣本根據[WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md)。 這個範例是由用戶端主控台程式 (Client.exe) 和網際網路資訊服務 (IIS) 所裝載的服務程式庫 (Service.dll) 所組成。 服務會實作定義要求-回覆通訊模式的合約。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例也會示範下列作業：  
  
-   預設的 Windows 帳戶對應，所以能夠執行額外的授權。  
  
-   如何從服務程式碼存取呼叫者的身分識別資訊。  
  
 服務會公開 (Expose) 單一的端點來與已使用組態檔 Web.config 定義之服務進行通訊。端點是由位址、繫結及合約所組成。 繫結設定的標準[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)，預設為使用訊息安全性。 這個範例會設定標準[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)使用用戶端使用者名稱驗證。 此行為會指定用來進行服務驗證的使用者認證。 伺服器憑證必須包含相同的值做為主體名稱`findValue`屬性中[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)。  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 用戶端端點組態是由服務端點的絕對位址、繫結及合約所組成。 用戶端繫結是透過適當的 `securityMode` 和 `authenticationMode` 所設定。 在跨電腦案例中執行時，服務端點位址必須隨同變更。  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 用戶端實作會設定要使用的使用者名稱和密碼。  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 訊息安全性範例所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要憑證安全性的裝載應用程式。 此批次檔可以在兩種模式中執行。 若要在單一電腦模式中執行此批次檔，請在命令列中輸入 `setup.bat`。 若要在服務模式中執行此批次檔，請輸入 `setup.bat service`。 您可以在跨電腦執行範例時使用這個模式。 如需詳細資訊，請參閱本主題結尾的安裝程序。  
  
 下面會提供批次檔之不同區段的簡短概觀。  
  
-   建立伺服器憑證  
  
     下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     %SERVER_NAME% 變數會指定伺服器名稱。 憑證是儲存在 LocalMachine 存放區中。 如果使用 service 引數執行 Setup.bat 批次檔 (例如，`setup.bat service`)，%SERVER_NAME% 就會包含電腦的完整網域名稱。  否則，預設為 localhost。  
  
-   將伺服器憑證安裝至用戶端的受信任憑證存放區中。  
  
     下列程式行會將伺服器憑證複製到用戶端受信任人的存放區中。 這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。 如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證的步驟。  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   授與憑證私密金鑰的權限  
  
     在 Setup.bat 批次檔中的下列程式行，會讓儲存在 LocalMachine 存放區的伺服器憑證可由 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 背景工作處理序帳戶存取。  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  如果您使用的是非美式英文版的 Windows，則必須編輯 Setup.bat 檔案，並以適用您所在地區的對等帳戶取代 `NT AUTHORITY\NETWORK SERVICE` 帳戶名稱。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>若要在同一部電腦上執行範例  
  
1. 確認路徑中包含 Makecert.exe 和 FindPrivateKey.exe 所在的資料夾。  
  
2. 以系統管理員權限開啟的 Visual studio，從範例安裝資料夾中開發人員命令提示字元執行 Setup.bat。 這會安裝執行範例所需的所有憑證。  
  
    > [!NOTE]
    >  Setup.bat 批次檔被設計來從開發人員命令提示字元執行適用於 Visual Studio。 它要求 path 環境變數指向安裝 SDK 的目錄。 這個環境變數是自動設定 Visual Studio 在開發人員命令提示字元。  
  
3. 驗證的存取權的服務使用瀏覽器輸入位址 `http://localhost/servicemodelsamples/service.svc` 。
  
4. 從 \client\bin 啟動 Client.exe。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
5. 如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例  
  
1. 在服務電腦上建立目錄。 使用 Internet Information Services 管理工具，為這個目錄建立名為 servicemodelsamples 的虛擬應用程式。  
  
2. 將 \inetpub\wwwroot\servicemodelsamples 中的服務程式檔複製至服務電腦上的虛擬目錄中。 確定複製 \bin 子目錄中的檔案。 同時，將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。  
  
3. 在用戶端電腦上為用戶端二進位碼檔案建立一個目錄。  
  
4. 將用戶端程式檔複製到用戶端電腦上的用戶端目錄。 同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。  
  
5. 在伺服器上，執行`setup.bat service`在開發人員命令提示字元適用於 Visual Studio 開啟系統管理員權限。 執行`setup.bat`與`service`引數會建立具有電腦完整網域名稱的服務憑證，並將服務憑證匯出為名為 Service.cer 的檔案。  
  
6. 編輯 Web.config 以反映新的憑證中的名稱 （在 serviceCertificate 項目的 findValue 屬性） 也就是電腦的完整網域名稱相同`.`  
  
7. 從服務目錄中將 Service.cer 檔案複製至用戶端電腦上的用戶端目錄。  
  
8. 在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。  
  
9. 在用戶端，以系統管理員權限開啟的 Visual studio 中開發人員命令提示字元執行 ImportServiceCert.bat。 這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。  
  
10. 在用戶端電腦上，從命令提示字元啟動 Client.exe。 如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
-   當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
  
    > [!NOTE]
    >  跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。 如果您已執行跨電腦使用憑證的 Windows Communication Foundation (WCF) 範例，請務必清除已安裝在 CurrentUser-TrustedPeople 存放區的服務憑證。 若要這樣做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` 例如： `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。  
