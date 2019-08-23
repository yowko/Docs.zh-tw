---
title: 網際網路資訊服務裝載最佳做法
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: e09a42f0f4a98728e588961425d8b6f5b50e6ccb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957220"
---
# <a name="internet-information-services-hosting-best-practices"></a>網際網路資訊服務裝載最佳做法
本主題將概述裝載 Windows Communication Foundation (WCF) 服務的一些最佳作法。  
  
## <a name="implementing-wcf-services-as-dlls"></a>將 WCF 服務實作為 DLL  
 將 WCF 服務實作為部署至 Web 應用程式之 \bin 目錄的 DLL, 可讓您在 Web 應用程式模型之外重複使用服務, 例如, 在可能未部署 Internet Information Services (IIS) 的測試環境中。  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS 裝載應用程式中的服務主機  
 請勿使用命令式自我裝載 Api 來建立新的服務主機, 以接聽 IIS 裝載環境原本不支援的網路傳輸 (例如, IIS 6.0 來主控 TCP 服務, 因為 IIS 6.0 上原本不支援 TCP 通訊)。 我們不建議您使用這個方式。 IIS 裝載環境無法辨識以命令式語法建立的服務主機。 關鍵在於，當 IIS 判斷裝載應用程式集區是否為閒置時，不會考慮透過命令式語法建立的服務所執行的處理作業。 而且內含此類以命令式語法建立之服務主機的應用程式，會透過 IIS 裝載環境強勢地處理 IIS 裝載處理序。  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI 和 IIS 裝載端點  
 IIS 裝載服務的端點應該透過相對的統一資源識別元 (URI)，而不是絕對位址來設定。 這樣可保證端點位址落在屬於裝載應用程式的 URI 位址範圍內，並確保訊息式啟動會如預期般發生。  
  
## <a name="state-management-and-process-recycling"></a>狀態管理與處理序回收  
 IIS 裝載環境已經針對無法在記憶體中保留本機狀態的服務進行最佳化。 IIS 會回收主機處理序以回應一系列不同的外部與內部事件，導致任何唯一存在記憶體中的變動性 (Volatile) 狀態遺失。 IIS 裝載的服務應該會將其狀態儲存到處理序外部 (例如，儲存在資料庫中) 或是儲存到記憶體中的快取，以便在發生應用程式回收事件時可以輕易地重新建立。  
  
> [!NOTE]
> WCF 用來進行訊息層可靠性和安全性的通訊協定會使用 volatile 記憶體內部狀態。 WCF 可靠會話和安全性會話可能會因為應用程式回收而非預期地終止。 使用這些通訊協定的 IIS 裝載應用程式, 應該取決於 WCF 提供的工作階段金鑰, 以關聯應用層狀態 (例如, 應用層結構或自訂相互關聯標頭) 或停用。裝載應用程式的 IIS 進程回收。  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>最佳化中介層案例中的效能  
 為了取得仲介*層案例*中的最佳效能, 這項服務會呼叫其他服務來回應內送訊息, 將 WCF 服務用戶端具現化一次, 並在多個傳入要求中重複使用它。 具現化 WCF 服務用戶端是一項昂貴的作業, 相對於在預先存在的用戶端實例上進行服務呼叫, 而仲介層案例會藉由快取跨要求的遠端用戶端, 而產生明顯的效能提升。 WCF 服務用戶端是安全線程, 因此不需要跨多個執行緒同步處理對用戶端的存取。  
  
 中介層案例同時會因為使用 `svcutil /a` 選項所產生的非同步 API 而產生一些效能。 選項會使「 [system.servicemodel 中繼資料公用程式」工具 (Svcutil)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)為`BeginXXX/EndXXX`每項服務作業產生方法, 這可讓您在背景執行緒上進行遠端服務的長時間執行呼叫。 `/a`  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>多重主目錄系統或多重具名案例中的 WCF  
 您可以在 IIS Web 伺服陣列內部部署 WCF 服務, 其中一組電腦共用通用的外部名稱 (例如`http://www.contoso.com`), 但由不同的主機名稱個別定址 (例如, `http://www.contoso.com`可能會將流量導向至兩部不同的電腦命名`http://machine1.internal.contoso.com`為`http://machine2.internal.contoso.com`和)。 WCF 完全支援此部署案例, 但需要特殊的 IIS 網站設定, 以裝載 WCF 服務, 以便在服務的中繼資料 (Web 服務描述語言) 中顯示正確的 (外部) 主機名稱。  
  
 為確保 WCF 產生的服務中繼資料中出現正確的主機名稱, 請設定裝載 WCF 服務之 IIS 網站的預設識別, 以使用明確的主機名稱。 例如, 位於伺服陣列內部`www.contoso.com`的電腦應使用 *:80: www. .com 的 IIS 網站系結, 針對 HTTP 和\*: 443: www. .com (適用于 HTTPS)。  
  
 您可以使用 IIS Microsoft Management Console (MMC) 嵌入式管理單元來設定 IIS 網站繫結。  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>在不同使用者內容中執行的應用程式集區會覆寫來自暫存資料夾裡其他帳戶的組件  
 若要確保在不同使用者內容中執行的應用程式集區無法覆寫暫存 ASP.NET files 資料夾中其他帳戶的元件, 請針對不同的應用程式使用不同的身分識別和暫存資料夾。 例如，如果您有兩個虛擬應用程式 (/Application1 和 / Application2)，則可以使用兩個不同的身分識別來建立兩個應用程式集區 (A 和 B)。 應用程式集區 A 可以使用某個使用者身分識別 (user1) 來執行，而應用程式集區 B 則可透過另一個使用者身分識別 (user2) 來執行，同時設定 /Application1 來使用 A 並設定 /Application2 來使用 B。  
  
 在 Web.config 中，您可以設定暫存資料夾，請使用 \<system.web/compilation/@tempFolder>。 為 application1，它可以是"c:\tempForUser1 ，並對於應用程式 2 中，這可能是 c:\tempForUser2"。 針對這些資料夾賦予兩個身分識別對應的寫入權限。  
  
 這樣一來，user2 將無法變更 /application2 (位於 c:\tempForUser1 底下) 的程式碼產生資料夾。  
  
## <a name="enabling-asynchronous-processing"></a>啟用非同步處理  
 根據預設, 傳送至裝載于 IIS 6.0 和更早版本之 WCF 服務的訊息會以同步方式處理。 ASP.NET 在自己的執行緒上呼叫 WCF (ASP.NET worker 執行緒), 而 WCF 則使用另一個執行緒來處理要求。 WCF 會暫止 ASP.NET 背景工作執行緒，直到其本身完成處理。 這將致使同步處理要求。 非同步處理要求可提供更高的擴充性, 因為它會減少處理要求所需的執行緒數目– WCF 不會在處理要求時保留 ASP.NET 執行緒。 不建議在執行 IIS 6.0 的電腦上使用非同步行為, 因為無法節流傳入要求, 而*導致伺服器拒絕服務*(DOS) 攻擊。 從 IIS 7.0 開始，則已引進了同時並存要求節流閥：`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`。 有了這個新的節流閥，便能放心地使用非同步處理。  預設在 IIS 7.0 中，非同步處理常式和模組要經過登錄。 如果這已經遭到關閉，您可以在應用程式的 Web.config 檔案中手動啟用非同步處理要求。 應該使用何種設定，取決於您的 `aspNetCompatibilityEnabled` 設定。 若您已將 `aspNetCompatibilityEnabled` 設定為 `false`，請依下列組態程式碼片段所示，設定 `System.ServiceModel.Activation.ServiceHttpModule`。  
  
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

- [服務裝載範例](../samples/hosting.md)
- [Windows Server AppFabric 裝載功能](https://go.microsoft.com/fwlink/?LinkId=201276)
