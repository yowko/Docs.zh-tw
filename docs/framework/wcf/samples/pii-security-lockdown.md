---
title: PII 安全性鎖定
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: ad4f4a024b04a028b815faedded58713e001cab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144262"
---
# <a name="pii-security-lockdown"></a>PII 安全性鎖定
此示例演示如何通過以下方式控制 Windows 通信基礎 （WCF） 服務的幾個與安全相關的功能：  
  
- 加密服務組態檔中的敏感性資訊。  
  
- 鎖定組態檔中的項目，讓巢狀服務子目錄無法覆寫設定。  
  
- 控制追蹤和訊息記錄檔中個人可識別資訊 (PII) 的記錄。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>討論區  
 您可以單獨或一起使用這些功能，以控制服務安全性的各個方面。 這不是保護 WCF 服務的明確指南。  
  
 .NET Framework 組態檔中包含敏感性資訊，例如連接至資料庫的連線字串。 在共用的 Web 裝載案例中，可能需要針對服務在組態檔中加密此資訊，因此組態檔所含的資料便不會任意讓人檢視。 .NET Framework 2.0 和更新版本可以使用 Windows Data Protection 應用程式開發介面 (DPAPI) 或 RSA 密碼編譯提供者，加密組態檔的各個部分。 使用 DPAPI 或 RSA 的 aspnet_regiis.exe 可以加密組態檔的選取部分。  
  
 在 Web 裝載的案例中，可能在其他服務的子目錄中還有服務。 判斷組態值的預設語意可允許巢狀目錄中的組態檔複寫上層目錄中的組態值。 在特定情況下，有許多原因都顯示不應該這樣做。 WCF 服務配置支援鎖定配置值，以便在使用重寫的配置值運行嵌套服務時生成異常。  
  
 這個範例示範如何控制在追蹤與訊息記錄檔中的已知個人可識別資訊 (PII) 記錄，例如使用者名稱與密碼。 根據預設，已停用記錄已知 PII，不過在特定情況下，記錄 PII 在偵錯應用程式時相當重要。 此示例基於[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 此外，這個範例會使用追蹤和訊息記錄。 有關詳細資訊，請參閱[跟蹤和消息日誌記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)示例。  
  
## <a name="encrypting-configuration-file-elements"></a>加密組態檔項目  
 針對安全性目的，在共用的 Web 裝載環境中，可能需要加密特定組態項目，例如包含敏感性資訊的資料庫連線字串。 配置元素可以使用 .NET 框架資料夾中的 aspnet_regiis.exe 工具進行加密 例如，%WINDIR%\Microsoft.NET_Framework_v4.0.20728。  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>若要加密範例 Web.config 中 appSettings 區段的值  
  
1. 使用"啟動>運行"打開命令提示。 鍵入並`cmd`按一下 **"確定**"。  
  
2. 發出下列命令，巡覽至目前的 .NET Framework 目錄：`cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`。  
  
3. 發出下列命令，加密 Web.config 資料夾中的 appSettings 組態設定：`aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`。  
  
 有關加密設定檔部分的詳細資訊，請參閱 ASP.NET 配置中的 DPAPI 操作操作（[構建安全ASP.NET應用程式：身份驗證、授權和安全通信](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))）和 ASP.NET 配置中的 RSA 操作（[如何：使用 RSA ASP.NET 2.0 加密配置部分](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))）。  
  
## <a name="locking-configuration-file-elements"></a>鎖定組態檔項目  
 在 Web 裝載的案例中，可能在服務的子目錄中還有服務。 在這些情況中，便會計算子目錄中服務的組態值，方法則是先檢查 Machine.config 中的值，接著合併上層目錄到下層目錄樹狀結構中的 Web.config 檔，最後合併其中包含服務之目錄中的 Web.config 檔。 大多數組態項目的預設行為是允許子目錄中的組態檔覆寫上層目錄中的值組。 在特定情況中，可能會防止子目錄中的組態檔覆寫上層目錄組態的值組。  
  
 .NET Framework 會提供鎖定組態檔項目的方法，因此覆寫已鎖定組態項目的組態會擲回執行階段例外狀況。  
  
 對組態檔中的節點指定 `lockItem` 屬性，即可鎖定組態項目。例如，若要鎖定組態檔中的 CalculatorServiceBehavior 節點，讓巢狀組態檔中的計算機服務無法變更行為，則可以使用下列組態。  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>
          <serviceBehaviors>
             <behavior name="CalculatorServiceBehavior" lockItem="true">
               <serviceMetadata httpGetEnabled="True"/>
               <serviceDebug includeExceptionDetailInFaults="False" />
             </behavior>
          </serviceBehaviors>
       </behaviors>
    </system.serviceModel>  
</configuration>  
```  
  
 鎖定組態項目可以更加特定。 可以指定項目清單做為 `lockElements` 的值，進而鎖定子項目集合內的一組項目。 可以指定屬性清單做為 `lockAttributes` 的值，進而鎖定項目內的一組屬性。 您可以藉由在節點上指定 `lockAllElementsExcept` 或 `lockAllAttributesExcept` 屬性，即可鎖定整個項目或屬性的集合，不過指定的清單則為例外。  
  
## <a name="pii-logging-configuration"></a>PII 記錄組態  
 PII 記錄是由兩個參數所控制：Machine.config 中找到的全電腦設定，可讓電腦系統管理員允許或拒絕記錄 PII。另一樣為應用程式設定，可讓應用程式管理員針對 Web.config 或 App.config 檔案中的每個來源切換 PII 記錄。  
  
 電腦範圍的設置通過在 Machine.config `true` `false`中`machineSettings`的元素中的設置`enableLoggingKnownPii`或 控制。例如，以下允許應用程式打開 PII 的日誌記錄。  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Machine.config 檔的預設位置為：%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG。  
  
 如果 Machine.config 中沒有 `enableLoggingKnownPii` 屬性，則不允許記錄 PII。  
  
 在 Web.config 或 App.config 檔案中將來源項目的 `logKnownPii` 屬性設定為 `true` 或 `false`，即可啟用應用程式的 PII 記錄。 例如，下列各項會針對訊息記錄和追蹤記錄啟用 PII 記錄。  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>
                ...
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 如果未指定 `logKnownPii` 屬性，則不會記錄 PII。  
  
 只有當 `enableLoggingKnownPii` 設定為 `true` 而且 `logKnownPii` 設定為 `true` 時，才會記錄 PII。  
  
> [!NOTE]
> System.Diagnostics 除了組態檔中列出的第一個屬性外，會忽略所有來源上的所有屬性。 將 `logKnownPii` 屬性新增至組態檔的第二個來源也沒有作用。  
  
> [!IMPORTANT]
> 要運行此示例，需要手動修改機器。修改 Machine.config 時應小心謹慎，因為不正確的值或語法可能會阻止所有 .NET 框架應用程式運行。  
  
 也可能使用 DPAPI 和 RSA 加密組態檔項目。 如需詳細資訊，請參閱下列連結：  
  
- [建置安全的 ASP.NET 應用程式：驗證、授權和安全通訊](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))  
  
- [HOW TO：使用 RSA 加密 ASP.NET 2.0 中的組態區段](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要設定、建置及執行範例  
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 編輯 Machine.config 以將 `enableLoggingKnownPii` 屬性設定為 `true`，需要時並新增父節點。  
  
3. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4. 要在單電腦或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
  
#### <a name="to-clean-up-the-sample"></a>若要清除範例  
  
1. 編輯 Machine.config 以將 `enableLoggingKnownPii` 屬性設定為 `false`。  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
