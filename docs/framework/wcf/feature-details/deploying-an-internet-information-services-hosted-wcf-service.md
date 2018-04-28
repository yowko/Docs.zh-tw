---
title: 部署已裝載網際網路資訊服務的 WCF 服務
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ca37e8b3f59875ed912c02d0a8237a040bf79518
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>部署已裝載網際網路資訊服務的 WCF 服務
開發與部署由 Internet Information Services (IIS) 裝載的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務包含下列工作：  
  
-   確定 IIS、ASP.NET、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 啟動元件都已正確安裝及註冊。  
  
-   建立新的 IIS 應用程式，或是重複使用現有的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式。  
  
-   建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的 .svc 檔案。  
  
-   將服務實作部署到 IIS 應用程式。  
  
-   設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
 如需如何建立由 IIS 裝載之 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的詳細逐步解說，請參閱 [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>確定 IIS、ASP.NET 和 WCF 已正確安裝及註冊  
 您必須安裝[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]、IIS 和 ASP.NET，才能讓 IIS 裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務正確運作。 安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (屬於 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]一部分)、ASP.NET 和 IIS 的程序可能會因所使用的作業系統版本而異。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 會安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 及 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]，請參閱 [Microsoft .NET Framework 4 Web 安裝程式](http://go.microsoft.com/fwlink/?LinkId=201185)。 您可以參閱 [安裝 IIS](http://go.microsoft.com/fwlink/?LinkId=201188)中的 IIS 安裝指示。  
  
 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 的安裝處理序會將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 自動註冊到 IIS 上 (如果 IIS 已經存在電腦上的話)。 如果 IIS 是在 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]之後才安裝，則您需要採取額外步驟將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 註冊到 IIS 和 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]。 請依據您的作業系統，採取下列適當的步驟：  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]、 Windows 7 和[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]： 使用[ServiceModel 註冊工具 (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md)工具註冊[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]與 IIS： 若要使用此工具，輸入**ServiceModelReg.exe /i /x**中Visual Studio 命令提示字元。 按一下 [開始] 按鈕，並依序選取 [ **所有程式**, **Microsoft Visual Studio 2012**, **Visual Studio Tools**] 和 [ **Visual Studio 命令提示字元**]，您即可開啟這個命令提示字元。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]：安裝 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]的 Windows Communication Foundation 啟動元件子元件。 若要這樣做，請在控制台中按一下**新增或移除程式**然後**新增\/移除 Windows 元件**。 這樣會啟動 [ **Windows 元件精靈**]。  
  
-   Windows 7：  
  
 最後，您必須確認 ASP.NET 設定成使用 .NET Framework 4 版。 您可以使用 -i 選項來執行 ASPNET_Regiis 工具，藉以達成此目的。 如需詳細資訊，請參閱[ASP.NET IIS 註冊工具](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>建立新的 IIS 應用程式或是重複使用現有的 ASP.NET 應用程式  
 IIS 裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務必須駐留在 IIS 應用程式裡面。 您可以建立新的 IIS 應用程式來專門裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。 或者，您可以將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務部署到已經裝載 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 內容 (例如 .aspx 網頁和 ASP.NET Web 服務 [ASMX]) 的現有應用程式上。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 這些選項的詳細資訊，請參閱 [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。  
  
 請注意， [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 及更新版本會定期重新啟動獨立的物件導向程式設計應用程式。 預設值為 1740 分鐘。 支援的最大值為 71,582 分鐘。 您可以停用這項重新啟動。 如需[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 這項屬性的詳細資訊，請參閱 [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968)。  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>建立 WCF 服務的 .svc 檔案  
 裝載在 IIS 的[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務會於 IIS 應用程式中以特殊內容檔 (.svc 檔) 形式表示。 這個模型與 IIS 應用程式將 ASMX 頁面表示為 .asmx 檔案的方式很類似。 .svc 檔案包含 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]的專用處理指示詞 ([@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md))，可允許 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 裝載基礎結構啟動裝載的服務來因應傳入的訊息。 以下是 .svc 檔案最常見的語法：  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 此語法包含 [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) 指示詞與一個屬性 `Service`。 `Service` 屬性值就是服務實作的 Common Language Runtime (CLR) 型別名稱。 基本上，使用此指示詞與使用下列程式碼來建立服務主機是一樣的：  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 其他的裝載組態，例如建立服務的基底位址清單，也能夠透過此方式來完成。 您也可以使用自訂的 <xref:System.ServiceModel.Activation.ServiceHostFactory> 來延伸指示詞，以便搭配自訂裝載方案來使用。 裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的 IIS 應用程式不負責管理 <xref:System.ServiceModel.ServiceHost> 執行個體的建立與存留期。 Managed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 裝載基礎結構會在第一次收到 .svc 檔案要求時，動態建立必要的 <xref:System.ServiceModel.ServiceHost> 執行個體。 除非程式碼明確地關閉此執行個體，或當應用程式已回收時，才會釋放此執行個體。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 之 .svc 檔案語法的詳細資訊，請參閱 [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)。  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>將服務實作部署到 IIS 應用程式  
 裝載在 IIS 中的[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務會使用與 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]相同的動態編譯模型。 就像 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]，您可以透過好幾種方式，將 IIS 裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的實作程式碼部署到幾個不同的位置，如下所示：  
  
-   做為預先編譯的 .dll 檔，位於全域組件快取 (GAC) 或應用程式的 \bin 目錄中。 預先編譯的二進位檔會等到部署了新版本的類別庫之後才會更新。  
  
-   成為未編譯的來源檔，位於應用程式的 \App_Code 目錄中。 位於此目錄的來源檔會在處理應用程式的第一個要求時動態需要。 在收到下一個要求時，對 \App_Code 目錄中檔案的任何變更都會導致整個應用程式的回收與重新編譯。  
  
-   成為未編譯的程式碼，直接位於 .svc 檔案中。 實作程式碼也可以內嵌在服務的.svc 檔案中，位於後@ServiceHost指示詞。 在收到下一個要求時，對內嵌程式碼的任何變更都會導致整個應用程式的回收與重新編譯。  
  
 如需[!INCLUDE[crabout](../../../../includes/crabout-md.md)]  [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 編譯模型的詳細資訊，請參閱 [ASP.NET 編譯概觀](http://go.microsoft.com/fwlink/?LinkId=94773)。  
  
## <a name="configure-the-wcf-service"></a>設定 WCF 服務  
 IIS 裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務會將其組態儲存在應用程式的 Web.config 檔案中。 IIS 裝載的服務會使用與在 IIS 外部裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務相同的組態項目與語法。 然而，IIS 裝載環境具備了下列特殊限制：  
  
-   IIS 裝載服務的基底位址。  
  
-   主控應用程式[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]IIS 外部的服務可以控制所傳遞的基底的一組位址的 Uri 來裝載的服務的基底位址<xref:System.ServiceModel.ServiceHost>建構函式或藉由提供[\<主機 >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)服務組態中的項目。 IIS 所裝載的服務無法控制自己的基底位址；IIS 裝載服務的基底位址就是所屬 .svc 檔案的位址。  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS 裝載服務的端點位址  
 透過 IIS 裝載時，端點位址一律視為相對於 .svc 檔案 (用來代表服務) 的位址。 例如，如果的基底位址[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務http://localhost/Application1/MyService.svc使用下列端點組態。  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 這會提供的端點，可以在達到 「http://localhost/Application1/MyService.svc/anotherEndpoint"。  
  
 同樣地，端點組態項目，其使用空字串，與相對位址會提供可在連線的端點http://localhost/Application1/MyService.svc，這是基底地址。  
  
```xml  
<endpoint address="" ... />  
```  
  
 請務必針對 IIS 裝載服務端點使用相對端點位址。 提供完整的端點位址 (例如，http://localhost/MyService.svc)如果端點位址並未指向 IIS 應用程式裝載服務公開的端點可能導致服務部署中的錯誤。 針對裝載的服務使用相對端點位址可以避免這些潛在的衝突。  
  
### <a name="available-transports"></a>可用的傳輸  
 IIS 5.1 和[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所裝載的 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 服務僅限於使用 HTTP 通訊。 在這些 IIS 平台上，設定裝載的服務來使用非 HTTP 繫結會在服務啟動期間導致錯誤。 在 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]上，支援的傳輸包括 HTTP、Net.TCP、Net.Pipe、Net.MSMQ，和 msmq.formatname，以便提供與現有 MSMQ 應用程式的回溯相容性。  
  
### <a name="http-transport-security"></a>HTTP 傳輸安全性  
 IIS 裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務可以利用 HTTP 傳輸安全性 (例如，使用基本、摘要式與 Windows 整合式驗證的 HTTPS 和 HTTP 驗證配置)，只要包含服務的 IIS 虛擬目錄支援這些設定即可。 裝載端點繫結上的 HTTP 傳輸安全性設定必須符合包含該設定之 IIS 虛擬目錄上的傳輸安全性設定。  
  
 例如，設定為使用 HTTP 摘要式驗證的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 端點必須駐留在同時設定為允許使用 HTTP 摘要式驗證的 IIS 虛擬目錄中。 如果 IIS 設定與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 端點設定組合不相符，會在服務啟動期間導致錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [在 Internet Information Services 中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Internet Information Services 裝載最佳做法](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Server App Fabric 裝載功能](http://go.microsoft.com/fwlink/?LinkId=201276)
