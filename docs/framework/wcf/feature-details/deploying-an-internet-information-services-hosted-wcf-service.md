---
title: 部署已裝載網際網路資訊服務的 WCF 服務
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: e46bcec846fcc8f9455c436bb551564e1cb5b5ea
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053306"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>部署已裝載網際網路資訊服務的 WCF 服務

開發和部署裝載于 Internet Information Services （IIS）中的 Windows Communication Foundation （WCF）服務包含下列工作：

- 請確定 IIS、ASP.NET、WCF 和 WCF 啟動元件都已正確安裝及註冊。

- 建立新的 IIS 應用程式，或重複使用現有的 ASP.NET 應用程式。

- 建立 WCF 服務的 .svc 檔案。

- 將服務實作部署到 IIS 應用程式。

- 設定 WCF 服務。

如需建立 IIS 裝載的 WCF 服務的詳細逐步解說，請[參閱如何：在 IIS](how-to-host-a-wcf-service-in-iis.md)中裝載 WCF 服務。

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>確定 IIS、ASP.NET 和 WCF 已正確安裝及註冊

必須安裝 WCF、IIS 和 ASP.NET，IIS 裝載的 WCF 服務才能正常運作。 安裝 WCF （做為 .NET Framework 的一部分）、ASP.NET 和 IIS 的程式會根據您的作業系統而有所不同。 如需安裝 WCF 和 .NET Framework 的詳細資訊，請參閱[安裝適用于開發人員的 .NET Framework](../../install/guide-for-developers.md)。 若要在 Windows 10 上安裝 IIS，請開啟 [**控制台**] 中的 [**程式和功能**]，然後選取 [**開啟或關閉 Windows 功能**]。 在 [ **Windows 功能**] 中，選取**Internet Information Services** ，然後選擇 **[確定]** 。

![已反白顯示 IIS 的 Windows 功能](./media/windows-features-iis.png)

如需在其他作業系統上安裝 IIS 的指示，請參閱在[Windows Vista 和 windows 7 上安裝 iis](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7)和[在 Windows Server 2012 R2 上安裝 iis 8.5](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2)。

如果電腦上已有 IIS，.NET Framework 的安裝程式會自動向 IIS 註冊 WCF。 如果在 .NET Framework 之後安裝 IIS，則需要額外的步驟來向 IIS 和 ASP.NET 註冊 WCF。 請依據您的作業系統，採取下列適當的步驟：

- Windows 7 和 Windows Server 2003：使用 [ [System.servicemodel 註冊工具] （servicemodelreg.exe）](../../../../docs/framework/wcf/servicemodelreg-exe.md)工具向 IIS 註冊 WCF。 若要使用此工具，請在[Visual Studio 的開發人員命令提示字元](../../tools/developer-command-prompt-for-vs.md)中輸入**servicemodelreg.exe/i/x** 。

- Windows 7：最後，您必須確認 ASP.NET 已設定為使用 .NET Framework 版本4或更新版本。 您可以使用`–i`選項執行 ASPNET_Regiis 工具來完成這項工作。 如需詳細資訊，請參閱[ASP.NET IIS 註冊工具](https://go.microsoft.com/fwlink/?LinkId=201186)。

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>建立新的 IIS 應用程式或是重複使用現有的 ASP.NET 應用程式

裝載于 IIS 的 WCF 服務必須位於 IIS 應用程式內。 您可以建立新的 IIS 應用程式，以獨佔方式裝載 WCF 服務。 或者，您可以將 WCF 服務部署到已經裝載 ASP.NET 2.0 內容的現有應用程式中（例如 .aspx pages 和 ASP.NET Web services [.ASMX]）。 如需這些選項的詳細資訊，請參閱[Wcf 服務與 ASP.NET](wcf-services-and-aspnet.md)中的 < 在 ASP.NET 相容性模式中裝載 wcf 與 ASP.NET 一節。

請注意，IIS 6.0 和更新版本會定期重新開機隔離的物件導向程式設計應用程式。 預設值為 1740 分鐘。 支援的最大值為 71,582 分鐘。 您可以停用這項重新啟動。 如需此屬性的詳細資訊，請參閱[PeriodicRestartTime](https://go.microsoft.com/fwlink/?LinkId=109968)。

## <a name="create-an-svc-file-for-the-wcf-service"></a>建立 WCF 服務的 .svc 檔案

裝載于 IIS 的 WCF 服務會在 IIS 應用程式內以特殊內容檔案（.svc 檔案）表示。 這個模型與 IIS 應用程式將 ASMX 頁面表示為 .asmx 檔案的方式很類似。 .Svc 檔案包含 wcf 特定的處理指示詞（[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)），可讓 wcf 裝載基礎結構啟動託管服務，以回應傳入訊息。 以下是 .svc 檔案最常見的語法：

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

它是由[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞和單一屬性`Service`所組成。 `Service` 屬性值就是服務實作的 Common Language Runtime (CLR) 型別名稱。 基本上，使用此指示詞與使用下列程式碼來建立服務主機是一樣的：

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

其他的裝載組態，例如建立服務的基底位址清單，也能夠透過此方式來完成。 您也可以使用自訂的 <xref:System.ServiceModel.Activation.ServiceHostFactory> 來延伸指示詞，以便搭配自訂裝載方案來使用。 裝載 WCF 服務的 IIS 應用程式不負責管理<xref:System.ServiceModel.ServiceHost>實例的建立與存留期。 當收到 .svc 檔案的第一個要求<xref:System.ServiceModel.ServiceHost>時，受控 WCF 裝載基礎結構會動態建立必要的實例。 除非程式碼明確地關閉此執行個體，或當應用程式已回收時，才會釋放此執行個體。

如需 .svc 檔案語法的詳細資訊，請參閱[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)。

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>將服務實作部署到 IIS 應用程式

裝載于 IIS 的 WCF 服務會使用與 ASP.NET 2.0 相同的動態編譯模型。 就像使用 ASP.NET 一樣，您可以在不同的位置，以數種方式部署裝載于 IIS 的 WCF 服務的實作為程式碼，如下所示：

- 做為預先編譯的 .dll 檔，位於全域組件快取 (GAC) 或應用程式的 \bin 目錄中。 預先編譯的二進位檔會等到部署了新版本的類別庫之後才會更新。

- 做為未編譯的來源檔案，位於應用程式的 \App_Code 目錄中。 位於此目錄的來源檔會在處理應用程式的第一個要求時動態需要。 在收到下一個要求時，對 \App_Code 目錄中檔案的任何變更都會導致整個應用程式的回收與重新編譯。

- 以未編譯的程式碼直接放在 .svc 檔案中。 您也可以在服務的 .svc 檔案中，以內嵌方式，將執行程式\@代碼放在 ServiceHost 指示詞之後。 在收到下一個要求時，對內嵌程式碼的任何變更都會導致整個應用程式的回收與重新編譯。

如需有關 ASP.NET 2.0 編譯模型的詳細資訊，請參閱[ASP.NET 編譯總覽](https://go.microsoft.com/fwlink/?LinkId=94773)。

## <a name="configure-the-wcf-service"></a>設定 WCF 服務

裝載于 IIS 的 WCF 服務會將其設定儲存在應用程式的 web.config 檔案中。 IIS 裝載的服務會使用與在 IIS 外部裝載的 WCF 服務相同的設定元素和語法。 然而，IIS 裝載環境具備了下列特殊限制：

- IIS 裝載服務的基底位址。

- 在 IIS 外部裝載 WCF 服務的應用程式可以藉由將一組基底位址 uri 傳遞給此<xref:System.ServiceModel.ServiceHost>函式，或在服務的中[ \<提供主機 >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)元素，來控制所裝載之服務的基底位址。配置. IIS 所裝載的服務無法控制自己的基底位址；IIS 裝載服務的基底位址就是所屬 .svc 檔案的位址。

### <a name="endpoint-addresses-for-iis-hosted-services"></a>IIS 裝載服務的端點位址

透過 IIS 裝載時，端點位址一律視為相對於 .svc 檔案 (用來代表服務) 的位址。 例如，如果 WCF 服務`http://localhost/Application1/MyService.svc`的基底位址具有下列端點設定：

```xml
<endpoint address="anotherEndpoint" .../>
```

這會提供可在上`http://localhost/Application1/MyService.svc/anotherEndpoint`觸達的端點。

同樣地，使用空字串做為相對位址的端點設定元素會提供可連線的端點`http://localhost/Application1/MyService.svc`，也就是基底位址。

```xml
<endpoint address="" ... />
```

請務必針對 IIS 裝載服務端點使用相對端點位址。 如果端點位址並未指向裝載服務的 IIS 應用程式`http://localhost/MyService.svc`來公開端點，則提供完整的端點位址（例如，）可能會導致服務部署中發生錯誤。 針對裝載的服務使用相對端點位址可以避免這些潛在的衝突。

### <a name="available-transports"></a>可用的傳輸

裝載于 IIS 5.1 和 IIS 6.0 中的 WCF 服務僅限於使用 HTTP 通訊。 在這些 IIS 平台上，設定裝載的服務來使用非 HTTP 繫結會在服務啟動期間導致錯誤。 針對 IIS 7.0，支援的傳輸包括 HTTP、Net.tcp、Net.pipe、Net.tcp 和 msmq.formatname，以提供與現有 MSMQ 應用程式的回溯相容性。

### <a name="http-transport-security"></a>HTTP 傳輸安全性

IIS 裝載的 WCF 服務可以利用 HTTP 傳輸安全性（例如，HTTPS 和 HTTP 驗證配置，例如基本、摘要式和 Windows 整合式驗證），只要包含服務的 IIS 虛擬目錄支援設置。 裝載端點繫結上的 HTTP 傳輸安全性設定必須符合包含該設定之 IIS 虛擬目錄上的傳輸安全性設定。

例如，設定為使用 HTTP 摘要式驗證的 WCF 端點必須位於同時設定為允許 HTTP 摘要式驗證的 IIS 虛擬目錄中。 不相符的 IIS 設定和 WCF 端點設定組合會導致服務啟用期間發生錯誤。

## <a name="see-also"></a>另請參閱

- [在 Internet Information Services 中裝載](hosting-in-internet-information-services.md)
- [Internet Information Services 裝載最佳做法](internet-information-services-hosting-best-practices.md)
- [Windows Server AppFabric 裝載功能](https://go.microsoft.com/fwlink/?LinkId=201276)
