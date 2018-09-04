---
title: 自訂繫結安全性
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 61e8be6f7f621340a684bff69ec5c9d64ab36c61
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565186"
---
# <a name="custom-binding-security"></a>自訂繫結安全性
這個範例會示範如何使用自訂繫結來設定安全性。 它會顯示如何使用自訂繫結同時啟用訊息層級安全性和安全傳輸。 當在用戶端和服務之間傳輸訊息需要安全傳輸，且同時必須保護訊息層級上訊息的安全時，這是相當有用的。 系統提供的繫結不支援這個組態。  
  
 這個範例是由用戶端主控台程式 (EXE) 與服務主控台程式 (EXE) 所組成。 服務會實作雙工合約。 合約是由 `ICalculatorDuplex` 介面所定義，這個介面會公開數學運算作業 (加、減、乘、除)。 `ICalculatorDuplex` 介面允許用戶端執行數學運算，計算整個工作階段的執行結果。 服務可能會獨立地傳回 `ICalculatorDuplexCallback` 介面上的結果。 雙工合約需要一個工作階段，因為必須建立內容，將用戶端與服務之間傳送的訊息關聯在一起。 自訂繫結已定義成支援雙工通訊，而且具備安全性。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 服務組態會定義支援下列作業的自訂繫結：  
  
-   使用 TLS/SSL 通訊協定保護的 TCP 通訊。  
  
-   Windows 訊息安全性。  
  
 自訂繫結組態會同時啟用訊息層級安全性以啟用安全傳輸。 繫結項目的順序很重要定義自訂繫結，因為每個都代表通道堆疊中的圖層 (請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md))。 自訂繫結會定義在服務與用戶端組態檔中，如下列範例組態所示。  
  
```xml  
<bindings>  
  <!-- Configure a custom binding. -->  
  <customBinding>  
    <binding name="Binding1">  
      <security authenticationMode="SecureConversation"  
                 requireSecurityContextCancellation="true">  
      </security>  
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
      <sslStreamSecurity requireClientCertificate="false"/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 自訂繫結使用服務憑證來驗證傳輸層級上的服務，並在用戶端和服務之間進行傳輸時保護訊息。 這是由 `sslStreamSecurity` 繫結項目所完成。 服務的憑證會使用服務行為設定，如下列範例組態所示。  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata />  
        <serviceDebug includeExceptionDetailInFaults="False" />  
        <serviceCredentials>  
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
        </serviceCredentials>  
    </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 此外，自訂繫結使用 Windows 認證類型 (預設認證類型) 的訊息安全性。 這是由 `security` 繫結項目所完成。 如果可以使用 Kerberos 驗證機制，則會使用訊息層級安全性來驗證用戶端和服務。 如果此範例是執行於 Active Directory 環境，就會發生這種情況。 如果 Kerberos 驗證機制無法使用，則使用 NTLM 驗證。 NTLM 會對服務驗證用戶端，但不會對用戶端驗證服務。 `security`繫結項目設定為使用`SecureConversation``authenticationType`，這會導致用戶端和服務上的安全性工作階段的建立。 若要讓服務的雙工合約能運作，這是必要的。  
  
 當您執行範例時，作業要求和回應會顯示在用戶端的主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 當執行範例時，您會看到訊息在回呼服務所傳送的介面時傳回到用戶端。 完成所有作業時，每個中繼結果都會顯示，並接著顯示整個方程式。 按 ENTER 鍵關閉用戶端。  
  
 這個已包含的 Setup.bat 檔可讓您使用相關的服務憑證設定用戶端與伺服器，以執行需要憑證安全性的自我裝載應用程式。 這個批次檔必須經過修改才能跨電腦運作，或在非裝載的情況下運作。  
  
 下面提供套用至此範例之批次檔的各區段的簡要概觀，讓批次檔得以修改為在適當的組態下執行：  
  
-   建立伺服器憑證。  
  
     下列 Setup.bat 檔中的程式行會建立要使用的伺服器憑證。 `%SERVER_NAME%` 變數會指定伺服器名稱。 您可以變更這個變數來指定自己的伺服器名稱。 這個批次檔的名稱預設為伺服器名稱，localhost。  
  
     憑證會儲存在 Web 裝載服務的 CurrentUser 存放區中。  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   將伺服器憑證安裝至用戶端的受信任憑證存放區中。  
  
     Setup.bat 檔中的下列程式行會將伺服器憑證複製到用戶端受信任人的存放區。 這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。 如果您已經有一個以用戶端信任的根憑證 (例如 Microsoft 所發行的憑證) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證的步驟。  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Setup.bat 批次檔是設計用來從 Visual Studio 2010 命令提示字元執行。 它要求 MSSDK 環境變數指向安裝 SDK 的目錄。 這個環境變數是自動在 Visual Studio 2010 命令提示字元中設定。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>若要在同一部電腦上執行範例  
  
1.  使用系統管理員權限來開啟 Visual Studio 命令提示字元視窗，然後執行範例安裝資料夾中的 Setup.bat。 這會安裝執行範例所需的所有憑證。  
  
    > [!NOTE]
    >  Setup.bat 批次檔是設計用來從 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元執行。 在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元中設定的 PATH 環境變數會指向包含 Setup.bat 指令碼所需之可執行檔的目錄。  
  
2.  從 \service\bin 啟動 Service.exe。  
  
3.  從 \client\bin 啟動 Client.exe。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
4.  如果用戶端和服務能夠進行通訊，請參閱[疑難排解祕訣](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例  
  
1.  在服務電腦上：  
  
    1.  在服務電腦上建立名為 servicemodelsamples 的虛擬目錄。  
  
    2.  將 \inetpub\wwwroot\servicemodelsamples 中的服務程式檔複製至服務電腦上的虛擬目錄中。 確定複製 \bin 子目錄中的檔案。  
  
    3.  將 Setup.bat 和 Cleanup.bat 檔案複製到服務電腦中。  
  
    4.  執行下列命令在 Visual Studio 命令提示字元開啟系統管理員權限： `Setup.bat service`。 這會建立服務憑證，其主體名稱與批次檔執行於其中之電腦的名稱相符。  
  
        > [!NOTE]
        >  Setup.bat 批次檔是設計用來從 Visual Studio 2010 命令提示字元執行。 它要求 path 環境變數指向安裝 SDK 的目錄。 這個環境變數是自動在 Visual Studio 2010 命令提示字元中設定。  
  
    5.  變更[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) Service.exe.config 檔以反映上一個步驟中產生的憑證的主體名稱。  
  
    6.  從命令提示字元執行 Service.exe。  
  
2.  在用戶端電腦上：  
  
    1.  將用戶端程式檔案從 \client\bin\ 資料夾複製到用戶端電腦中。 同時複製 Cleanup.bat 檔。  
  
    2.  執行 Cleanup.bat，移除先前範例的任何舊憑證。  
  
    3.  匯出服務的憑證，方法是使用系統管理權限來開啟 Visual Studio 命令提示字元，然後在服務電腦上執行下列命令 (將 `%SERVER_NAME%` 取代成執行此服務之電腦的完整名稱)：  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  將 %SERVER_NAME%.cer 複製到用戶端電腦 (將 %SERVER_NAME% 取代成執行此服務之電腦的完整名稱)。  
  
    5.  匯入服務的憑證，方法是使用系統管理權限來開啟 Visual Studio 命令提示字元，然後在用戶端電腦上執行下列命令 (將 %SERVER_NAME% 取代成執行此服務之電腦的完整名稱)：  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         如果憑證是由信任的簽發者發行，就不需要執行步驟 c、d 和 e。  
  
    6.  修改用戶端的 App.config 檔，如下所示：  
  
        ```xml  
        <client>  
            <endpoint name="default"  
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"   
                binding="customBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"  
        behaviorConfiguration="CalculatorClientBehavior" />  
        </client>  
        ```  
  
    7.  如果用於執行服務的帳戶有別於網域環境中的 NetworkService 或 LocalSystem 帳戶，您可能需要修改用戶端 App.config 檔中服務端點的端點身分識別，以根據用來執行服務之帳戶設定適當的 UPN 或 SPN。 如需端點身分識別的詳細資訊，請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)主題。  
  
    8.  從命令提示字元執行 Client.exe。  
  
### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
-   當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
  
## <a name="see-also"></a>另請參閱
