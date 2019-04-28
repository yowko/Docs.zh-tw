---
title: 部署已裝載網際網路資訊服務的 WCF 服務
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 99ed9ce5304717073057f6712a2b96d910d43bea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858311"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>部署已裝載網際網路資訊服務的 WCF 服務

開發和部署裝載在網際網路資訊服務 (IIS) 中的 Windows Communication Foundation (WCF) 服務包含下列工作：

- 確定，IIS、 ASP.NET、 WCF 及 WCF 啟用元件已正確安裝並註冊。

- 建立新的 IIS 應用程式，或重複使用現有的 ASP.NET 應用程式。

- 建立 WCF 服務.svc 檔案。

- 將服務實作部署到 IIS 應用程式。

- 設定 WCF 服務。

建立 IIS 裝載的 WCF 服務的詳細逐步解說，請參閱[How to:將 WCF 服務裝載於 IIS](how-to-host-a-wcf-service-in-iis.md)。

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>確定 IIS、ASP.NET 和 WCF 已正確安裝及註冊

WCF、 IIS 和 ASP.NET 必須安裝 IIS 裝載的 WCF 服務，才能正確運作。 安裝 （如.NET Framework 的一部分） 的 WCF、 ASP.NET 和 IIS 的程序需視您的作業系統而有所不同。 如需有關如何安裝 WCF 和.NET Framework 的詳細資訊，請參閱 <<c0> [ 安裝適用於開發人員的.NET Framework](../../install/guide-for-developers.md)。 若要在 Windows 10 上安裝 IIS，請開啟**程式和功能**中**控制台**，然後選取**開啟或關閉開啟的 Windows 功能**。 在  **Windows 功能**，選取**Internet Information Services** ，然後選擇**確定**。

![與 IIS，反白顯示的 Windows 功能](media/windows-features-iis.png)

在其他作業系統上安裝 IIS 的指示位於[安裝在 Windows Vista 和 Windows 7 上的 IIS](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7)並[Windows Server 2012 R2 上安裝 IIS 8.5](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2)。

如果 IIS 已經存在於電腦上.NET Framework 的安裝程序會自動向 IIS 註冊 WCF。 如果 IIS 已安裝.NET Framework 之後，額外的步驟，才能向 IIS 和 ASP.NET 的 WCF。 請依據您的作業系統，採取下列適當的步驟：

- Windows 7 和 Windows Server 2003:使用[ServiceModel 註冊工具 (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md)向 IIS 註冊 WCF 的工具。 若要使用此工具，輸入**ServiceModelReg.exe /i /x**中[Visual Studio 的開發人員命令提示字元](../../tools/developer-command-prompt-for-vs.md)。

- Windows 7：最後，您必須確認 ASP.NET 已設定為使用.NET Framework 4 或更新版本的版本。 您可以執行 ASPNET_Regiis 工具，搭配`–i`選項。 如需詳細資訊，請參閱 < [ASP.NET IIS 註冊工具](https://go.microsoft.com/fwlink/?LinkId=201186)。

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>建立新的 IIS 應用程式或是重複使用現有的 ASP.NET 應用程式

IIS 裝載的 WCF 服務必須駐留的 IIS 應用程式。 您可以只建立新的 IIS 應用程式裝載 WCF 服務。 或者，您可以部署到現有的應用程式已經裝載的 WCF 服務[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]內容 （例如.aspx 頁面和 ASP.NET Web 服務 [ASMX]）。 如需這些選項的詳細資訊，請參閱 「 主控 WCF-並存使用 ASP.NET"及"裝載 ASP.NET 相容性模式中的 WCF 服務 > 章節中[WCF 服務與 ASP.NET](wcf-services-and-aspnet.md)。

請注意， [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 及更新版本會定期重新啟動獨立的物件導向程式設計應用程式。 預設值為 1740 分鐘。 支援的最大值為 71,582 分鐘。 您可以停用這項重新啟動。 如需有關這個屬性的詳細資訊，請參閱 < [PeriodicRestartTime](https://go.microsoft.com/fwlink/?LinkId=109968)。

## <a name="create-an-svc-file-for-the-wcf-service"></a>建立 WCF 服務的 .svc 檔案

在 IIS 中裝載的 WCF 服務會以特殊內容檔 （.svc 檔案） 在 IIS 應用程式內部表示。 這個模型與 IIS 應用程式將 ASMX 頁面表示為 .asmx 檔案的方式很類似。 .Svc 檔案包含 WCF 特定的處理指示詞 ([\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md))，可讓 WCF，裝載基礎結構啟動裝載的服務，以回應傳入的訊息。 以下是 .svc 檔案最常見的語法：

```
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>
```

它是組成[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞與一個屬性， `Service`。 `Service` 屬性值就是服務實作的 Common Language Runtime (CLR) 型別名稱。 基本上，使用此指示詞與使用下列程式碼來建立服務主機是一樣的：

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

其他的裝載組態，例如建立服務的基底位址清單，也能夠透過此方式來完成。 您也可以使用自訂的 <xref:System.ServiceModel.Activation.ServiceHostFactory> 來延伸指示詞，以便搭配自訂裝載方案來使用。 裝載 WCF 服務的 IIS 應用程式不負責管理建立和存留期<xref:System.ServiceModel.ServiceHost>執行個體。 受管理的 WCF 裝載基礎結構會建立必要<xref:System.ServiceModel.ServiceHost>收到.svc 檔案的第一個要求時動態執行個體。 除非程式碼明確地關閉此執行個體，或當應用程式已回收時，才會釋放此執行個體。

如需.svc 檔案語法的詳細資訊，請參閱 < [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)。

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>將服務實作部署到 IIS 應用程式

在 IIS 中裝載的 WCF 服務使用相同的動態編譯模型[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]。 如同 ASP.NET 中，您可以部署在不同位置的數種方式裝載於 IIS 的 WCF 服務的實作程式碼，如下所示：

- 做為預先編譯的 .dll 檔，位於全域組件快取 (GAC) 或應用程式的 \bin 目錄中。 預先編譯的二進位檔會等到部署了新版本的類別庫之後才會更新。

- 因為未編譯的原始程式檔會位於應用程式的 \App_Code 目錄中。 位於此目錄的來源檔會在處理應用程式的第一個要求時動態需要。 在收到下一個要求時，對 \App_Code 目錄中檔案的任何變更都會導致整個應用程式的回收與重新編譯。

- 因為未編譯的程式碼直接置於.svc 檔案。 實作程式碼也可以在服務的.svc 檔案中，位於的內嵌之後\@ServiceHost 指示詞。 在收到下一個要求時，對內嵌程式碼的任何變更都會導致整個應用程式的回收與重新編譯。

如需詳細資訊[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]編譯模型，請參閱 < [ASP.NET 編譯概觀](https://go.microsoft.com/fwlink/?LinkId=94773)。

## <a name="configure-the-wcf-service"></a>設定 WCF 服務

IIS 裝載的 WCF 服務會將其組態儲存在應用程式 Web.config 檔案中。 IIS 裝載的服務會為 IIS 外部所裝載的 WCF 服務使用相同的組態項目和語法。 然而，IIS 裝載環境具備了下列特殊限制：

- IIS 裝載服務的基底位址。

- IIS 外部裝載的 WCF 服務可以控制其所傳遞的基底的一組裝載的服務基底位址的應用程式位址 Uri<xref:System.ServiceModel.ServiceHost>建構函式或藉由提供[\<主機 >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)中的項目服務的組態。 IIS 所裝載的服務無法控制自己的基底位址；IIS 裝載服務的基底位址就是所屬 .svc 檔案的位址。

### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS 裝載服務的端點位址

透過 IIS 裝載時，端點位址一律視為相對於 .svc 檔案 (用來代表服務) 的位址。 例如，如果 WCF 服務的基底位址是`http://localhost/Application1/MyService.svc`使用下列的端點組態：

```xml
<endpoint address="anotherEndpoint" .../>
```

這會提供可在端點`http://localhost/Application1/MyService.svc/anotherEndpoint`。

同樣地，端點組態項目，會使用空字串，因為相對位址提供可在端點`http://localhost/Application1/MyService.svc`，這是基底地址。

```xml
<endpoint address="" ... />
```

請務必針對 IIS 裝載服務端點使用相對端點位址。 提供完整的端點位址 (例如`http://localhost/MyService.svc`) 可能會導致服務的部署中的錯誤如果端點位址並未指向 IIS 應用程式裝載服務公開的端點。 針對裝載的服務使用相對端點位址可以避免這些潛在的衝突。

### <a name="available-transports"></a>可用的傳輸

WCF 服務裝載於 IIS 5.1 和[!INCLUDE[iis601](../../../../includes/iis601-md.md)]受限於只能使用 HTTP 通訊。 在這些 IIS 平台上，設定裝載的服務來使用非 HTTP 繫結會在服務啟動期間導致錯誤。 在 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]上，支援的傳輸包括 HTTP、Net.TCP、Net.Pipe、Net.MSMQ，和 msmq.formatname，以便提供與現有 MSMQ 應用程式的回溯相容性。

### <a name="http-transport-security"></a>HTTP 傳輸安全性

IIS 裝載的 WCF 服務可以利用 HTTP 傳輸安全性 （例如，HTTPS 和 HTTP 驗證配置例如基本、 摘要式與 Windows 整合式驗證），只要包含服務的 IIS 虛擬目錄支援這些設定。 裝載端點繫結上的 HTTP 傳輸安全性設定必須符合包含該設定之 IIS 虛擬目錄上的傳輸安全性設定。

例如，設定為使用 HTTP 摘要式驗證的 WCF 端點必須位於也會設定為允許 HTTP 摘要式驗證的 IIS 虛擬目錄。 IIS 設定與 WCF 端點設定的組合不相符會導致在服務啟動期間的錯誤。

## <a name="see-also"></a>另請參閱

- [在 Internet Information Services 中裝載](hosting-in-internet-information-services.md)
- [Internet Information Services 裝載最佳做法](internet-information-services-hosting-best-practices.md)
- [Windows Server AppFabric 裝載功能](https://go.microsoft.com/fwlink/?LinkId=201276)
