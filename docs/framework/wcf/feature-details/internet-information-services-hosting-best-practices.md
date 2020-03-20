---
title: 網際網路資訊服務裝載最佳做法
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 3be9d4c81f891ad898099ba9041a09b16388b7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184710"
---
# <a name="internet-information-services-hosting-best-practices"></a>網際網路資訊服務裝載最佳做法
本主題概述了託管 Windows 通信基礎 （WCF） 服務的一些最佳做法。  
  
## <a name="implementing-wcf-services-as-dlls"></a>將 WCF 服務實作為 DLL  
 將 WCF 服務作為 DLL 部署到 Web 應用程式的 \bin 目錄，允許您在 Web 應用程式模型之外重用該服務，例如，在可能沒有部署 Internet 資訊服務 （IIS） 的測試環境中重用該服務。  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS 裝載應用程式中的服務主機  
 不要使用命令式自主機 API 來創建新的服務主機，這些主機偵聽 IIS 託管環境不支援的本機傳輸（例如，IIS 6.0 承載 TCP 服務，因為 IIS 6.0 上不支援本機通信）。 我們不建議您使用這個方式。 IIS 裝載環境無法辨識以命令式語法建立的服務主機。 關鍵在於，當 IIS 判斷裝載應用程式集區是否為閒置時，不會考慮透過命令式語法建立的服務所執行的處理作業。 而且內含此類以命令式語法建立之服務主機的應用程式，會透過 IIS 裝載環境強勢地處理 IIS 裝載處理序。  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI 和 IIS 裝載端點  
 IIS 裝載服務的端點應該透過相對的統一資源識別元 (URI)，而不是絕對位址來設定。 這樣可保證端點位址落在屬於裝載應用程式的 URI 位址範圍內，並確保訊息式啟動會如預期般發生。  
  
## <a name="state-management-and-process-recycling"></a>狀態管理與處理序回收  
 IIS 裝載環境已經針對無法在記憶體中保留本機狀態的服務進行最佳化。 IIS 會回收主機處理序以回應一系列不同的外部與內部事件，導致任何唯一存在記憶體中的變動性 (Volatile) 狀態遺失。 IIS 裝載的服務應該會將其狀態儲存到處理序外部 (例如，儲存在資料庫中) 或是儲存到記憶體中的快取，以便在發生應用程式回收事件時可以輕易地重新建立。  
  
> [!NOTE]
> WCF 用於消息層可靠性和安全性的協定利用了易失性記憶體狀態。 由於應用程式回收，WCF 可靠的會話和安全會話可能會意外終止。 使用這些協定的 IIS 託管應用程式應依賴于 WCF 提供的工作階段金鑰以外的內容來關聯應用程式層狀態（例如，應用程式層構造或自訂關聯標頭），或禁用IIS 進程回收託管應用程式。  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>最佳化中介層案例中的效能  
 為了在*中介層方案中*獲得最佳性能（一種回應傳入消息而調用其他服務的服務），將 WCF 服務用戶端具現化到遠端服務一次，並在多個傳入請求中重用它。 相對於對預先存在的用戶端實例進行服務調用，具現化 WCF 服務用戶端是一項昂貴的操作，中介層方案通過跨請求緩存遠端用戶端來產生顯著的性能提升。 WCF 服務用戶端是執行緒安全的，因此不必跨多個執行緒同步對用戶端的訪問。  
  
 中介層案例同時會因為使用 `svcutil /a` 選項所產生的非同步 API 而產生一些效能。 該`/a`選項使[ServiceModel 中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)為每個服務操作生成`BeginXXX/EndXXX`方法，從而允許在後臺執行緒上對遠端服務進行可能長時間運行的調用。  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>多重主目錄系統或多重具名案例中的 WCF  
 可以在 IIS Web 場內部署 WCF 服務，其中一組電腦共用一個公共外部名稱（`http://www.contoso.com`如），但由不同的主機名稱單獨定址（例如，`http://www.contoso.com`可能會將流量定向到兩台名為`http://machine1.internal.contoso.com`和`http://machine2.internal.contoso.com`的電腦。 此部署方案完全支援 WCF，但需要託管 WCF 服務的 IIS 網站的特殊配置才能在服務的中繼資料（Web 服務描述語言）中顯示正確的（外部）主機名稱。  
  
 為確保正確的主機名稱出現在 WCF 生成的服務中繼資料中，請為承載 WCF 服務的 IIS 網站配置預設標識以使用顯式主機名稱。 例如，駐留在`www.contoso.com`伺服器場內的電腦應使用用於 HTTP 的 IIS 網站綁定 ：80：www.contoso.com\*和 ：443：www.contoso.com 用於 HTTPS。  
  
 您可以使用 IIS Microsoft Management Console (MMC) 嵌入式管理單元來設定 IIS 網站繫結。  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>在不同使用者內容中執行的應用程式集區會覆寫來自暫存資料夾裡其他帳戶的組件  
 為了確保在不同使用者上下文中運行的應用程式池不能覆蓋臨時ASP.NET檔資料夾中其他帳戶的程式集，請使用不同應用程式的不同標識和暫存檔案夾。 例如，如果您有兩個虛擬應用程式 (/Application1 和 / Application2)，則可以使用兩個不同的身分識別來建立兩個應用程式集區 (A 和 B)。 應用程式集區 A 可以使用某個使用者身分識別 (user1) 來執行，而應用程式集區 B 則可透過另一個使用者身分識別 (user2) 來執行，同時設定 /Application1 來使用 A 並設定 /Application2 來使用 B。  
  
 在 Web.config 中，您可以使用\<system.web/compilation/@tempFolder>配置暫存檔案夾。 對於 /Application1，它可以是"c：\tempForUser1"，對於應用程式2，它可以是"c：\tempForUser2"。 針對這些資料夾賦予兩個身分識別對應的寫入權限。  
  
 這樣一來，user2 將無法變更 /application2 (位於 c:\tempForUser1 底下) 的程式碼產生資料夾。  
  
## <a name="enabling-asynchronous-processing"></a>啟用非同步處理  
 預設情況下，發送到 IIS 6.0 和更早版本的 WCF 服務的消息以同步方式處理。 ASP.NET在其自己的執行緒（ASP.NET工作執行緒）上調用 WCF，WCF 使用另一個執行緒來處理請求。 WCF 會暫止 ASP.NET 背景工作執行緒，直到其本身完成處理。 這將致使同步處理要求。 非同步處理請求可異地實現更大的可伸縮性，因為它減少了處理請求所需的執行緒數 —WCF 在處理請求時不會保留ASP.NET執行緒。 不建議對運行 IIS 6.0 的電腦使用非同步行為，因為無法限制打開伺服器的傳入請求以拒絕*服務*（DOS） 攻擊。 從 IIS 7.0 開始，則已引進了同時並存要求節流閥：`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`。 有了這個新的節流閥，便能放心地使用非同步處理。  預設在 IIS 7.0 中，非同步處理常式和模組要經過登錄。 如果這已經遭到關閉，您可以在應用程式的 Web.config 檔案中手動啟用非同步處理要求。 應該使用何種設定，取決於您的 `aspNetCompatibilityEnabled` 設定。 若您已將 `aspNetCompatibilityEnabled` 設定為 `false`，請依下列組態程式碼片段所示，設定 `System.ServiceModel.Activation.ServiceHttpModule`。  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="false" />
  </system.serviceModel>  
  <system.webServer>  
    <modules>  
      <remove name="ServiceModel"/>  
      <add name="ServiceModel"
           preCondition="integratedMode,runtimeVersionv2.0"
           type="System.ServiceModel.Activation.ServiceHttpModule, System.ServiceModel,Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
    </modules>  
    </system.webServer>  
```  
  
 若您已將 `aspNetCompatibilityEnabled` 設定為 `true`，請依下列組態程式碼片段所示，設定 `System.ServiceModel.Activation.ServiceHttpHandlerFactory`。  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
  </system.serviceModel>  
  <system.webServer>  
    <handlers>  
          <clear/>  
          <add name="TestAsyncHttpHandler"
               path="*.svc"
               verb="*"
               type="System.ServiceModel.Activation.ServiceHttpHandlerFactory, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
               />  
    </handlers>
  </system.webServer>  
```  
  
## <a name="see-also"></a>另請參閱

- [服務託管示例](../samples/hosting.md)
- [Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
