---
title: 部署已裝載網際網路資訊服務的 WCF 服務
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 67f6877546951bd92b235218f10f6ccc7011ef5c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463860"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>部署已裝載網際網路資訊服務的 WCF 服務

開發並部署在 Internet 資訊服務 (IIS) 中託管的 Windows 通訊基礎 (WCF) 服務包括以下任務:

- 確保正確安裝和註冊 IIS、ASP.NET、WCF 和 WCF 啟動元件。

- 創建新的 IIS 應用程式,或重用現有的 ASP.NET 應用程式。

- 為 WCF 服務創建 .svc 檔案。

- 將服務實作部署到 IIS 應用程式。

- 配置 WCF 服務。

有關創建 IIS 託管的 WCF 服務的詳細演練,請參閱[如何:在 IIS 中託管 WCF 服務](how-to-host-a-wcf-service-in-iis.md)。

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>確定 IIS、ASP.NET 和 WCF 已正確安裝及註冊

必須安裝 WCF、IIS 和ASP.NET才能使 IIS 託管的 WCF 服務正常運行。 安裝 WCF(作為 .NET 框架的一部分)、ASP.NET和 IIS 的過程因作業系統而異。 有關安裝 WCF 和 .NET 框架的詳細資訊,請參閱[為開發人員安裝 .NET 框架](../../install/guide-for-developers.md)。 要在 Windows 10 上安裝 IIS,請在 **「控制面板**」中打開**程式和功能**,然後選擇 **「打開或關閉 Windows 功能**」。 在**Windows 功能**中,選擇**互聯網資訊服務**,然後選擇 **「確定**」。。

![突顯 IIS 的 Windows 功能](./media/windows-features-iis.png)

有關在其他作業系統上安裝 IIS 的說明,請參閱[在 Windows Vista 和 Windows 7 上安裝 IIS,](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7)並在 Windows 伺服器[2012 R2 上安裝 IIS 8.5](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2)。

如果電腦上已存在 IIS,則 .NET 框架的安裝過程會自動將 WCF 註冊到 IIS。 如果在 .NET 框架之後安裝了 IIS,則需要執行其他步驟才能將 WCF 註冊到 IIS 並ASP.NET。 請依據您的作業系統，採取下列適當的步驟：

- Windows 7 和 Windows 伺服器 2003:使用[服務模型註冊工具 (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md)工具向 IIS 註冊 WCF。 要使用此工具,在[視覺化工作室的開發人員指令提示符](../../tools/developer-command-prompt-for-vs.md)中鍵入**ServiceModelReg.exe/i /x** 。

- Windows 7:最後,您必須驗證ASP.NET是否配置為使用 .NET 框架版本 4 或更高版本。 通過運行帶有該`–i`選項ASPNET_Regiis工具來執行此操作。 有關詳細資訊,請參閱[ASP.NET IIS 註冊工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90))。

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>建立新的 IIS 應用程式或是重複使用現有的 ASP.NET 應用程式

IIS 託管的 WCF 服務必須駐留在 IIS 應用程式內。 您可以創建新的 IIS 應用程式來獨佔 WCF 服務。 或者,您可以將 WCF 服務部署到已託管ASP.NET 2.0 內容(如 .aspx 頁和ASP.NET Web 服務 [ASMX])的現有應用程式。 有關這些選項的詳細資訊,請參閱[WCF 服務和 ASP.NET](wcf-services-and-aspnet.md)中的「與 ASP.NET 並排託管 WCF」和「以ASP.NET相容性模式託管 WCF 服務」部分。

請注意,IIS 6.0 和更高版本會定期重新啟動隔離的面向對象的程式設計應用程式。 預設值為 1740 分鐘。 支援的最大值為 71,582 分鐘。 您可以停用這項重新啟動。 關於此屬性的詳細資訊,請參閱[定期重新啟動時間](https://docs.microsoft.com/previous-versions/iis/6.0-sdk/ms525914(v=vs.90))。

## <a name="create-an-svc-file-for-the-wcf-service"></a>建立 WCF 服務的 .svc 檔案

IIS 中託管的 WCF 服務表示為 IIS 應用程式中的特殊內容檔 (.svc 檔)。 這個模型與 IIS 應用程式將 ASMX 頁面表示為 .asmx 檔案的方式很類似。 .svc 檔包含特定於 WCF 的處理指令[\@(ServiceHost),](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)允許 WCF 託管基礎結構啟動託管服務以回應傳入的消息。 以下是 .svc 檔案最常見的語法：

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

它由[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令和單`Service`個屬性 組成。 `Service` 屬性值就是服務實作的 Common Language Runtime (CLR) 型別名稱。 基本上，使用此指示詞與使用下列程式碼來建立服務主機是一樣的：

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

其他的裝載組態，例如建立服務的基底位址清單，也能夠透過此方式來完成。 您也可以使用自訂的 <xref:System.ServiceModel.Activation.ServiceHostFactory> 來延伸指示詞，以便搭配自訂裝載方案來使用。 託管 WCF 服務的 IIS 應用程式不負責管理<xref:System.ServiceModel.ServiceHost>實例的 創建和存留期。 當收到 .svc<xref:System.ServiceModel.ServiceHost>檔案的第 一個請求時,託管的 WCF 託管基礎結構會動態創建必要的實例。 除非程式碼明確地關閉此執行個體，或當應用程式已回收時，才會釋放此執行個體。

有關 .svc 檔案的語法的詳細資訊,請參閱[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)。

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>將服務實作部署到 IIS 應用程式

IIS 中託管的 WCF 服務使用與 ASP.NET 2.0 相同的動態編譯模型。 與ASP.NET一樣,您可以通過多種方式在不同位置部署IIS託管的WCF服務的實現代碼,如下所示:

- 做為預先編譯的 .dll 檔，位於全域組件快取 (GAC) 或應用程式的 \bin 目錄中。 預先編譯的二進位檔會等到部署了新版本的類別庫之後才會更新。

- 作為位於應用程式的_App_Code目錄中的未編譯源檔。 位於此目錄的來源檔會在處理應用程式的第一個要求時動態需要。 在收到下一個要求時，對 \App_Code 目錄中檔案的任何變更都會導致整個應用程式的回收與重新編譯。

- 作為直接放置在 .svc 檔中的未編譯代碼。 實現代碼也可以位於\@服務的 .svc 檔中,在 ServiceHost 指令之後。 在收到下一個要求時，對內嵌程式碼的任何變更都會導致整個應用程式的回收與重新編譯。

有關ASP.NET 2.0 編譯模型的詳細資訊,請參閱[ASP.NET 編譯概述](https://docs.microsoft.com/previous-versions/aspnet/ms178466(v=vs.100))。

## <a name="configure-the-wcf-service"></a>設定 WCF 服務

IIS 託管的 WCF 服務將其設定儲存在應用程式 Web.config 檔中。 IIS 託管的服務使用與IIS外部託管的WCF服務相同的配置元素和語法。 然而，IIS 裝載環境具備了下列特殊限制：

- IIS 裝載服務的基底位址。

- 在IIS之外託管 WCF 服務的應用程式可以通過將一組基本位址URI<xref:System.ServiceModel.ServiceHost>傳遞給建構函數或在服務配置中提供[\<主機>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)元素來控制其託管服務的基本位址。 IIS 所裝載的服務無法控制自己的基底位址；IIS 裝載服務的基底位址就是所屬 .svc 檔案的位址。

### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS 裝載服務的端點位址

透過 IIS 裝載時，端點位址一律視為相對於 .svc 檔案 (用來代表服務) 的位址。 例如,如果 WCF 服務的基本`http://localhost/Application1/MyService.svc`位址具有 以下終結點配置:

```xml
<endpoint address="anotherEndpoint" />
```

這提供了可在 處`http://localhost/Application1/MyService.svc/anotherEndpoint`到達的終結點。

同樣,使用空字串作為相對位址的終結點配置元素提供可在 處`http://localhost/Application1/MyService.svc`訪問的終結點,該終結點是基本位址。

```xml
<endpoint address="" />
```

請務必針對 IIS 裝載服務端點使用相對端點位址。 如果終結點位址未指向承載公開終結點的服務的`http://localhost/MyService.svc`IIS 應用程式,則提供完全限定的終結點位址(例如),可能會導致服務部署中的錯誤。 針對裝載的服務使用相對端點位址可以避免這些潛在的衝突。

### <a name="available-transports"></a>可用的傳輸

IIS 5.1 和 IIS 6.0 中託管的 WCF 服務僅限於使用基於 HTTP 的通信。 在這些 IIS 平台上，設定裝載的服務來使用非 HTTP 繫結會在服務啟動期間導致錯誤。 對於 IIS 7.0,支援的傳輸包括 HTTP、Net.TCP、Net.Pipe、Net.MSMQ 和 msmq.formatname,用於向後與現有 MSMQ 應用程式相容。

### <a name="http-transport-security"></a>HTTP 傳輸安全性

IIS 託管的 WCF 服務可以使用 HTTP 傳輸安全性(例如,HTTPS 和 HTTP 身份驗證方案(如基本、摘要和 Windows 整合身份驗證),只要包含該服務的 IIS 虛擬目錄支援這些設置。 裝載端點繫結上的 HTTP 傳輸安全性設定必須符合包含該設定之 IIS 虛擬目錄上的傳輸安全性設定。

例如,配置為使用 HTTP 摘要身份驗證的 WCF 終結點必須駐留在 IIS 虛擬目錄中,該虛擬目錄也配置為允許 HTTP 摘要身份驗證。 IIS 設置和 WCF 終結點設置的不匹配組合會導致服務啟動期間出錯。

## <a name="see-also"></a>另請參閱

- [在網際網路資訊服務中裝載](hosting-in-internet-information-services.md)
- [Internet Information Services 裝載最佳做法](internet-information-services-hosting-best-practices.md)
- [Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
