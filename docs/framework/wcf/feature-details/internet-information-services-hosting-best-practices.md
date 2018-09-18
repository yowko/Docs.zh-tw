---
title: 網際網路資訊服務裝載最佳做法
ms.date: 03/30/2017
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
ms.openlocfilehash: 0ca5e20b846a1b10f5a52748ff06a4af958b2f4c
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009397"
---
# <a name="internet-information-services-hosting-best-practices"></a>網際網路資訊服務裝載最佳做法
本主題概述裝載 Windows Communication Foundation (WCF) 服務的最佳作法。  
  
## <a name="implementing-wcf-services-as-dlls"></a>將 WCF 服務實作為 DLL  
 實作 WCF 服務以部署至 Web 應用程式的 \bin 目錄的 DLL，讓您重複使用 Web 應用程式模型中，外部服務，例如在測試環境中可能沒有安裝 Internet Information Services (IIS) 部署。  
  
## <a name="service-hosts-in-iis-hosted-applications"></a>IIS 裝載應用程式中的服務主機  
 請勿使用命令式自我裝載 API 來建立可接聽網路傳輸 (原本並非由 IIS 裝載環境所支援) 的新服務主機 (例如，請勿使用 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 來裝載 TCP 服務，因為 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 原本並不支援 TCP 通訊)。 我們不建議您使用這個方式。 IIS 裝載環境無法辨識以命令式語法建立的服務主機。 關鍵在於，當 IIS 判斷裝載應用程式集區是否為閒置時，不會考慮透過命令式語法建立的服務所執行的處理作業。 而且內含此類以命令式語法建立之服務主機的應用程式，會透過 IIS 裝載環境強勢地處理 IIS 裝載處理序。  
  
## <a name="uris-and-iis-hosted-endpoints"></a>URI 和 IIS 裝載端點  
 IIS 裝載服務的端點應該透過相對的統一資源識別元 (URI)，而不是絕對位址來設定。 這樣可保證端點位址落在屬於裝載應用程式的 URI 位址範圍內，並確保訊息式啟動會如預期般發生。  
  
## <a name="state-management-and-process-recycling"></a>狀態管理與處理序回收  
 IIS 裝載環境已經針對無法在記憶體中保留本機狀態的服務進行最佳化。 IIS 會回收主機處理序以回應一系列不同的外部與內部事件，導致任何唯一存在記憶體中的變動性 (Volatile) 狀態遺失。 IIS 裝載的服務應該會將其狀態儲存到處理序外部 (例如，儲存在資料庫中) 或是儲存到記憶體中的快取，以便在發生應用程式回收事件時可以輕易地重新建立。  
  
> [!NOTE]
>  WCF 會使用訊息層可靠性和安全性所做的通訊協定使用的變動性記憶體中狀態。 WCF 可靠工作階段與安全性工作階段，則可能會因應用程式回收的緣故而無預警地終止。 IIS 裝載的應用程式，請使用這些通訊協定應該仰賴相互關聯的應用程式層級狀態 （例如，應用程式層級建構或自訂相互關聯標頭） 或停用的 WCF 提供的工作階段金鑰以外的項目IIS 裝載的應用程式回收處理程序。  
  
## <a name="optimizing-performance-in-middle-tier-scenarios"></a>最佳化中介層案例中的效能  
 為了達到最佳效能，在*中介層案例*-呼叫其他服務，以回應傳入訊息的服務，具現化給遠端服務的 WCF 服務用戶端一次，並跨多個連入重複使用要求。 具現化 WCF 服務用戶端是昂貴的作業，相對於服務呼叫的預先存在的用戶端執行個體，在和中介層案例藉由快取要求之間的遠端用戶端產生獨特的效能。 WCF 服務用戶端是安全執行緒，因此不需要跨多個執行緒同步處理到用戶端的存取。  
  
 中介層案例同時會因為使用 `svcutil /a` 選項所產生的非同步 API 而產生一些效能。 `/a`選項會使[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)產生`BeginXXX/EndXXX`每個服務作業中，會允許遠端服務上的長期執行呼叫的方法背景執行緒。  
  
## <a name="wcf-in-multi-homed-or-multi-named-scenarios"></a>多重主目錄系統或多重具名案例中的 WCF  
 您可以部署 WCF 服務內的 IIS Web 伺服陣列，其中的一組電腦共用通用外部名稱 (例如 http://www.contoso.com) 但會個別定址依不同的主機名稱 (比方說， http://www.contoso.com 可能會將流量導向至兩個不同的電腦名為 http://machine1.internal.contoso.com 和 http://machine2.internal.contoso.com)。 此部署案例中透過 WCF，完全支援，但需要特殊組態的裝載服務的中繼資料 （Web 服務描述語言） 中顯示正確的 （外部） 主機名稱的 WCF 服務的 IIS 網站。  
  
 若要確保正確的主機名稱會出現在產生 WCF 服務中繼資料，請設定裝載 WCF 服務來使用明確的主機名稱的 IIS 網站的預設身分識別。 例如，駐留在 www.contoso.com 伺服器陣列的電腦應該使用的 IIS 網站繫結 *:80:www.contoso.com 適用於 HTTP 和\*: 443:www.contoso.com https。  
  
 您可以使用 IIS Microsoft Management Console (MMC) 嵌入式管理單元來設定 IIS 網站繫結。  
  
## <a name="application-pools-running-in-different-user-contexts-overwrite-assemblies-from-other-accounts-in-the-temporary-folder"></a>在不同使用者內容中執行的應用程式集區會覆寫來自暫存資料夾裡其他帳戶的組件  
 為了確保在不同使用者內容中執行的應用程式集區無法覆寫來自 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 暫存檔案資料夾中其他帳戶的組件，請針對不同的應用程式使用不同的身分識別與暫存資料夾。 例如，如果您有兩個虛擬應用程式 (/Application1 和 / Application2)，則可以使用兩個不同的身分識別來建立兩個應用程式集區 (A 和 B)。 應用程式集區 A 可以使用某個使用者身分識別 (user1) 來執行，而應用程式集區 B 則可透過另一個使用者身分識別 (user2) 來執行，同時設定 /Application1 來使用 A 並設定 /Application2 來使用 B。  
  
 在 Web.config 中，您可以設定暫存資料夾，請使用 \< system.web/compilation/@tempFolder>。 為 application1，它可以是"c:\tempForUser1 ，並對於應用程式 2 中，這可能是 c:\tempForUser2"。 針對這些資料夾賦予兩個身分識別對應的寫入權限。  
  
 這樣一來，user2 將無法變更 /application2 (位於 c:\tempForUser1 底下) 的程式碼產生資料夾。  
  
## <a name="enabling-asynchronous-processing"></a>啟用非同步處理  
 依預設訊息傳送至裝載在 IIS 6.0 和更早版本的 WCF 服務會以同步方式處理。 ASP.NET 在自己的執行緒 （ASP.NET 背景工作執行緒） 上呼叫 WCF 及 WCF 使用另一個執行緒來處理要求。 WCF 會暫止 ASP.NET 背景工作執行緒，直到其本身完成處理。 這將致使同步處理要求。 以非同步方式處理要求可提高延展性，因為它可以減少處理的要求 – WCF 不會暫止 ASP.NET 執行緒處理要求時所需的執行緒數目。 執行 IIS 6.0，因為沒有任何方法可以開啟伺服器的連入要求進行節流的電腦不建議採用非同步*阻絕服務*(DOS) 攻擊。 從 IIS 7.0 開始，則已引進了同時並存要求節流閥：`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]"MaxConcurrentRequestsPerCpu`。 有了這個新的節流閥，便能放心地使用非同步處理。  預設在 IIS 7.0 中，非同步處理常式和模組要經過登錄。 如果這已經遭到關閉，您可以在應用程式的 Web.config 檔案中手動啟用非同步處理要求。 應該使用何種設定，取決於您的 `aspNetCompatibilityEnabled` 設定。 若您已將 `aspNetCompatibilityEnabled` 設定為 `false`，請依下列組態程式碼片段所示，設定 `System.ServiceModel.Activation.ServiceHttpModule`。  
  
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
 [服務裝載範例](https://msdn.microsoft.com/library/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)  
 [Windows Server App Fabric 主控功能](https://go.microsoft.com/fwlink/?LinkId=201276)
