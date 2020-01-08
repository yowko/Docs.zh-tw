---
title: WCF 服務和 ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 0a64e277d3465b77a2553d6b9c3901f09a6e1a52
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544747"
---
# <a name="wcf-services-and-aspnet"></a>WCF 服務和 ASP.NET

本主題討論如何將 Windows Communication Foundation （WCF）服務與 ASP.NET 並存裝載，並以 ASP.NET 相容性模式裝載它們。

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>將 WCF 與 ASP.NET 並存裝載

裝載于 Internet Information Services （IIS）中的 WCF 服務可以使用來找出。單一通用應用程式域內的 ASPX 頁面和 .ASMX Web 服務。 ASP.NET 為 WCF 和 ASP.NET HTTP 執行時間提供一般的基礎結構服務，例如 AppDomain 管理和動態編譯。 WCF 的預設設定與 ASP.NET 並存。

![顯示 WCF 服務和 ASP .NET：共用狀態的螢幕擷取畫面。](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

ASP.NET HTTP 執行時間會處理 ASP.NET 要求，但不會參與處理以 WCF 服務為目標的要求，即使這些服務裝載于與 ASP.NET 內容相同的 AppDomain 中。 相反地，WCF 服務模型會攔截定址至 WCF 服務的訊息，並透過 WCF 傳輸/通道堆疊路由傳送。

並存模型的結果如下：

- ASP.NET 和 WCF 服務可以共用 AppDomain 狀態。 因為這兩個架構可以並存于相同的 AppDomain 中，所以 WCF 也可以與 ASP.NET 共用 AppDomain 狀態（包括靜態變數、事件等等）。

- WCF 服務的行為一致，與裝載環境和傳輸無關。 ASP.NET HTTP 執行階段主要用來與 IIS/ASP.NET 裝載環境和 HTTP 通訊搭配使用。 相反地，WCF 的設計是跨主機環境（WCF 在 IIS 內部和外部都有一致的行為）和跨傳輸（在 IIS 7.0 和更新版本中裝載的服務在其公開的所有端點之間具有一致的行為，即使其中一些端點會使用 HTTP 以外的通訊協定）。

- 在 AppDomain 中，HTTP 執行時間所執行的功能會套用至 ASP.NET 內容，但不適用於 WCF。 ASP.NET 應用程式平臺的許多 HTTP 特定功能並不適用于包含 ASP.NET 內容之 AppDomain 內所裝載的 WCF 服務。 下列為這些功能的範例：

  - 從 WCF 服務存取時，會一律 `null` HttpCoNtext： <xref:System.Web.HttpContext.Current%2A>。 請改用 <xref:System.ServiceModel.Channels.RequestContext> 。

  - 以檔案為基礎的授權：當決定是否授權服務要求時，WCF 安全性模型不允許套用至服務 .svc 檔案的存取控制清單（ACL）。

  - 以設定為基礎的 URL 授權：同樣地，WCF 安全性模型不會遵守在 System.web 的 \<授權 > configuration 元素中指定的任何 URL 型授權規則。 如果服務位於 ASP 所保護的 URL 空間中，則會忽略 WCF 要求的這些設定。NET 的 URL 授權規則。

  - HttpModule 擴充性：當引發 <xref:System.Web.HttpApplication.PostAuthenticateRequest> 事件時，WCF 裝載基礎結構會攔截 WCF 要求，而不會將處理傳回 ASP.NET HTTP 管線。 編碼為在管線稍後的階段攔截要求的模組不會攔截 WCF 要求。

  - ASP.NET 模擬：根據預設，WCF 要求一律以 IIS 進程身分識別來執行，即使 ASP.NET 設為使用 System.web 的 \<identity 模擬 = "true"/> 設定選項來啟用模擬。

這些限制僅適用于裝載于 IIS 應用程式中的 WCF 服務。 ASP.NET 內容的行為不會受到 WCF 的存在影響。

需要傳統由 HTTP 管線提供之功能的 WCF 應用程式，應考慮使用與主機和傳輸無關的 WCF 對應項：

- 以 <xref:System.ServiceModel.OperationContext> 取代 <xref:System.Web.HttpContext>。

- 以 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 取代 ASP.NET 的檔案/URL 授權。

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> 或是自訂層級的通道，以取代 HTTP 模組。

- 使用 WCF （而非 System.web 模擬）來模擬每項作業。

或者，您可以考慮在 WCF 的 ASP.NET 相容性模式中執行您的服務。

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>在 ASP.NET 相容性模式中裝載 WCF 服務

雖然 WCF 模型的設計是要在裝載環境和傳輸之間保持一致的行為，但通常應用程式不需要這麼多的彈性。 WCF 的 ASP.NET 相容性模式適用于不需要在 IIS 外部裝載，或透過 HTTP 以外的通訊協定進行通訊，但卻使用 ASP.NET Web 應用程式平臺所有功能的情況。

不同于預設並存設定，其中 WCF 裝載基礎結構會攔截 WCF 訊息並將其路由傳送至 HTTP 管線，在 ASP.NET 相容性模式中執行的 WCF 服務會完全參與 ASP.NET HTTP 要求生命週期。 在相容性模式中，WCF 服務會透過 <xref:System.Web.IHttpHandler> 的執行方式來使用 HTTP 管線，這類似于處理 ASPX 頁面和 .ASMX Web 服務的要求。 因此，WCF 的行為與與下列 ASP.NET 功能相關的 .ASMX 相同：

- <xref:System.Web.HttpContext>：在 ASP.NET 相容性模式中執行的 WCF 服務可以存取 <xref:System.Web.HttpContext.Current%2A> 和其相關聯的狀態。

- 以檔案為基礎的授權：在 ASP.NET 相容性模式中執行的 WCF 服務，可以藉由將檔系統存取控制清單（Acl）附加至服務的 .svc 檔案來保護其安全。

- 可設定的 URL 授權： ASP。當 WCF 服務在 ASP.NET 相容性模式中執行時，會對 WCF 要求強制執行 NET 的 URL 授權規則。

- <xref:System.Web.HttpModuleCollection> 擴充性：因為在 ASP.NET 相容性模式中執行的 WCF 服務會完全參與 ASP.NET HTTP 要求生命週期，所以 HTTP 管線中設定的任何 HTTP 模組都能夠在服務叫用前後的 WCF 要求上運作。

- ASP.NET 模擬： WCF 服務會使用 ASP.NET 模擬執行緒目前的身分識別來執行，如果應用程式已啟用 ASP.NET 模擬，這可能會與 IIS 進程身分識別不同。 如果已針對特定服務作業啟用 ASP.NET 模擬和 WCF 模擬，則服務執行最後會使用從 WCF 取得的身分識別來執行。

WCF 的 ASP.NET 相容性模式會透過下列設定（位於應用程式的 Web.config 檔案）在應用層級啟用：

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

如果未指定，則此值預設為 `false`。 `false` 的值表示應用程式中執行的所有 WCF 服務都不會在 ASP.NET 的相容性模式中執行。

由於 ASP.NET 相容性模式意指的是與 WCF 預設值截然不同的要求處理語義，因此個別服務實現可以控制是否要在應用程式內執行，其 ASP.NET已啟用相容性模式。 服務可以透過 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 來指出是否支援 ASP.NET 相容性模式。 這個屬性的預設值為 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>。

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

下表說明整個應用程式相容性模式設定如何與個別服務所陳述的支援層級互動：

|整個應用程式的相容性模式設定|[AspNetCompatibilityRequirementsMode]<br /><br /> 設定|觀察結果|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|服務成功啟動。|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|服務成功啟動。|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|當服務接收訊息時，發生啟動錯誤。|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|當服務接收訊息時，發生啟動錯誤。|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|服務成功啟動。|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|服務成功啟動。|

> [!NOTE]
> IIS 7.0 和 WAS 允許 WCF 服務透過 HTTP 以外的通訊協定進行通訊。 不過，在已啟用 ASP.NET 相容性模式的應用程式中執行的 WCF 服務不允許公開非 HTTP 端點。 此類組態會在服務接收其第一則訊息時，產生啟動例外狀況。

如需啟用 WCF 服務之 ASP.NET 相容性模式的詳細資訊，請參閱 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> 和[ASP.NET 相容性](../samples/aspnet-compatibility.md)範例。

## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
