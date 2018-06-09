---
title: X.509 憑證驗證程式
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 911b6db28f89f7a4266ef1b23246020cd0381ada
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231524"
---
# <a name="x509-certificate-validator"></a>X.509 憑證驗證程式
這個範例會示範如何實作自訂 X.509 憑證驗證程式。 當內建的 X.509 憑證驗證程式模式都不符合應用程式需求時，這個驗證程式就很有用。 這個範例示範的服務具有可接受自動發行之憑證的自訂驗證程式。 用戶端會使用這類憑證來向服務驗證。  
  
 注意：因為任何人都可以建構自動發行的憑證，所以此服務使用的自訂驗證程式所產生的安全性，會低於 ChainTrust X509CertificateValidationMode 提供之預設行為的安全性。 在實際執行程式碼 (Production Code) 中使用這項驗證邏輯之前，應該要謹慎考量這些安全性含義。  
  
 這個範例所示範的作業摘要如下：  
  
-   用戶端可以使用 X.509 憑證進行驗證。  
  
-   伺服器會向自訂 X509CertificateValidator 驗證用戶端的認證。  
  
-   伺服器是使用該伺服器的 X.509 憑證來驗證的。  
  
 服務會公開 (Expose) 單一的端點來與已使用組態檔 App.config 定義之服務進行通訊。端點是由位址、繫結及合約所組成。 繫結設定的標準`wsHttpBinding`經由預設使用`WSSecurity`和用戶端憑證驗證。 服務行為會指定 [自訂] 模式，以驗證用戶端 X.509 憑證以及該驗證程式類別的類型。 行為也會使用 serviceCertificate 項目來指定伺服器憑證。 伺服器憑證必須包含相同值的`SubjectName`為`findValue`中[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)。  
  
```xml  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use host/baseAddresses to configure base address -->  
        <!-- provided by host -->  
        <host>  
          <baseAddresses>  
            <add baseAddress =  
                "http://localhost:8001/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address specified above, provide one endpoint -->  
        <endpoint address="certificate"  
               binding="wsHttpBinding"  
               bindingConfiguration="Binding"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <!-- X509 certificate binding -->  
        <binding name="Binding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults ="true"/>  
          <serviceCredentials>  
            <!--The serviceCredentials behavior allows one -->  
            <!-- to specify authentication constraints on -->  
            <!-- client certificates. -->  
            <clientCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- Custom means that if the custom -->  
              <!-- X509CertificateValidator does NOT throw -->  
              <!-- an exception, then the provided certificate -- >  
              <!-- will be trusted without performing any -->  
              <!-- validation beyond that performed by the custom-->  
              <!-- validator. The security implications of this -->  
              <!-- setting should be carefully considered before -->  
              <!-- using Custom in production code. -->  
              <authentication   
                 certificateValidationMode="Custom"   
                 customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />  
            </clientCertificate>  
            <!-- The serviceCredentials behavior allows one to -- >  
            <!--define a service certificate. -->  
            <!--A service certificate is used by a client to  -->  
            <!--authenticate the service and provide message  -->  
            <!--protection. This configuration references the  -->  
            <!--"localhost" certificate installed during the setup  -->  
            <!--instructions. -->  
            <serviceCertificate findValue="localhost"   
                 storeLocation="LocalMachine"   
                 storeName="My" x509FindType="FindBySubjectName" />  
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
      <!-- X509 certificate based endpoint -->  
      <endpoint name="Certificate"  
        address=  
        "http://localhost:8001/servicemodelsamples/service/certificate"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
    <bindings>  
        <wsHttpBinding>  
            <!-- X509 certificate binding -->  
            <binding name="Binding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
               </security>  
            </binding>  
       </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- PeerOrChainTrust means that if the certificate -->  
              <!-- is in the user's Trusted People store, then it -->  
              <!-- is trusted without performing a validation of -->  
              <!-- the certificate's issuer chain. -->  
              <!-- This setting is used here for convenience so -->  
              <!-- that the sample can be run without having to -->  
              <!-- have certificates issued by a certification -->  
              <!-- authority (CA). This setting is less secure -->  
              <!-- than the default, ChainTrust. The security -->  
              <!-- implications of this setting should be -->  
              <!-- carefully considered before using -->  
              <!-- PeerOrChainTrust in production code.-->  
              <authentication   
                  certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 用戶端實作會設定要使用的用戶端憑證。  
  
```csharp
// Create a client with Certificate endpoint configuration  
CalculatorClient client = new CalculatorClient("Certificate");  
try  
{  
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");  
  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    client.Close();  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine("Call timed out : {0}", e.Message);  
    client.Abort();  
}  
catch (CommunicationException e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
```  
  
 這個範例會使用自訂 X509CertificateValidator 以驗證憑證。 此範例會實作衍生自 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 的 CustomX509CertificateValidator。 如需詳細資訊，請參閱有關 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 的文件。 這個特定自訂驗證程式範例會實作 Validate 方法，以接受任何自動發行的 X.509 憑證，如下列程式碼所示。  
  
```csharp
public class CustomX509CertificateValidator : X509CertificateValidator  
{  
  public override void Validate ( X509Certificate2 certificate )  
  {  
   // Only accept self-issued certificates  
   if (certificate.Subject != certificate.Issuer)  
     throw new Exception("Certificate is not self-issued");  
   }  
}  
```  
  
 一旦驗證程式在服務程式碼中實作，服務主機就必須收到要使用的驗證程式執行個體的相關通知。 這個動作是使用下列程式碼完成。  
  
```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 或者，您可以在組態中執行如下所示的動作。  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
     <behavior name="CalculatorServiceBehavior">  
       ...  
   <serviceCredentials>  
    <!--The serviceCredentials behavior allows one to specify -->   
    <!--authentication constraints on client certificates.-->  
    <clientCertificate>  
    <!-- Setting the certificateValidationMode to Custom means -->   
    <!--that if the custom X509CertificateValidator does NOT -->   
    <!--throw an exception, then the provided certificate will-- >   
    <!-- be trusted without performing any validation beyond that-- >  
    <!-- performed by the custom validator. The security -- >   
    <!--implications of this setting should be carefully -- >  
    <!--considered before using Custom in production code. -->  
    <authentication certificateValidationMode="Custom"  
       customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />  
   </clientCertificate>  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 用戶端應該會成功呼叫所有方法。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
## <a name="setup-batch-file"></a>設定批次檔  
 本範例中所包含的 Setup.bat 批次檔可讓您使用相關的憑證設定伺服器，以執行需要伺服器憑證安全性的自我裝載應用程式。 這個批次檔必須經過修改才能跨電腦運作，或在非裝載的情況下運作。  
  
 下面提供批次檔的各區段簡要概觀，讓批次檔得以修改為在適當的組態下執行：  
  
-   建立伺服器憑證：  
  
     下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證。 %SERVER_NAME% 變數會指定伺服器名稱。 您可以變更這個變數來指定自己的伺服器名稱。 預設值為 localhost。  
  
    ```bash  
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
  
    ```bash  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   建立用戶端憑證：  
  
     下列 Setup.bat 批次檔中的程式行會建立要使用的用戶端憑證。 %USER_NAME% 變數會指定用戶端名稱。 這個值會設定為 "test1"，因為這是用戶端程式碼會尋找的名稱。 如果變更了 %USER_NAME% 的值，您就必須在 Client.cs 原始程式檔中變更對應的值，並重新建置該用戶端。  
  
     憑證會儲存在 CurrentUser 存放區位置下的 My (Personal) 存放區中。  
  
    ```bash  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   將用戶端憑證安裝至伺服器的受信任憑證存放區中：  
  
     Setup.bat 批次檔中的下列程式行會將用戶端憑證複製到受信任人的存放區。 這是必要步驟，因為伺服器系統並未隱含信任 Makecert.exe 產生的憑證。 如果您已經有一個以信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將用戶端憑證填入伺服器憑證存放區的步驟。  
  
    ```bash  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>若要設定和建置範例  
  
1.  若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
2.  若要在單一或跨電腦的組態中執行本範例，請使用下列指示。  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>若要在同一部電腦上執行範例  
  
1.  在使用系統管理員權限開啟的 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元內部，執行範例安裝資料夾中的 Setup.bat。 這會安裝執行範例所需的所有憑證。  
  
    > [!IMPORTANT]
    >  Setup.bat 批次檔是設計用來從 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元執行。 在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元中設定的 PATH 環境變數會指向包含 Setup.bat 指令碼所需之可執行檔的目錄。  
  
2.  從 service\bin 啟動 Service.exe。  
  
3.  從 \client\bin 啟動 Client.exe。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
4.  如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
#### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例  
  
1.  在服務電腦上建立目錄。  
  
2.  將 \service\bin 中的服務程式檔複製到服務電腦上的虛擬目錄中。 同時將 Setup.bat、Cleanup.bat、GetComputerName.vbs 和 ImportClientCert.bat 檔複製到服務電腦上。  
  
3.  在用戶端電腦上為用戶端二進位碼檔案建立一個目錄。  
  
4.  將用戶端程式檔複製到用戶端電腦上的用戶端目錄。 同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。  
  
5.  在伺服器上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 `setup.bat service`。 執行`setup.bat`與`service`引數建立服務憑證的電腦匯出的完整網域名稱服務憑證，若要為名為 Service.cer 的檔案。  
  
6.  編輯 Service.exe.config 以反映新的憑證名稱 (在`findValue`屬性[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) 做為電腦的完整網域名稱相同。 中的電腦名稱也會變更\<服務 > /\<baseAddresses > 項目服務電腦的完整名稱從 localhost。  
  
7.  從服務目錄中將 Service.cer 檔案複製至用戶端電腦上的用戶端目錄。  
  
8.  在用戶端上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 `setup.bat client`。 使用 `setup.bat` 引數來執行 `client`，就會建立名稱為 client.com 的用戶端憑證，並且會將用戶端憑證匯出為名為 Client.cer 的檔案。  
  
9. 在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。 若要這麼做，請使用伺服器的完整網域名稱取代 localhost。  
  
10. 從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。  
  
11. 在用戶端上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 ImportServiceCert.bat。 這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。  
  
12. 在伺服器上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 ImportClientCert.bat。 這樣便會從 Client.cer 檔將用戶端憑證匯入至 LocalMachine - TrustedPeople 存放區中。  
  
13. 在伺服器電腦上，從命令提示字元視窗啟動 Service.exe。  
  
14. 在用戶端電腦上，從命令提示字元視窗啟動 Client.exe。 如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
#### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
1.  當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。 這樣會從憑證存放區中移除伺服器與用戶端憑證。  
  
> [!NOTE]
>  跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。 如果您已執行跨電腦使用憑證的 Windows Communication Foundation (WCF) 範例，請務必清除安裝在 CurrentUser-TrustedPeople 存放區的服務憑證。 若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。  
  
## <a name="see-also"></a>另請參閱
