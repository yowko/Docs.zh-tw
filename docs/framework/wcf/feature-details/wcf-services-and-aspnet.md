---
title: WCF 服務和 ASP.NET
description: 深入瞭解如何與 ASP.NET 並存裝載 WCF 服務，以及如何以 ASP.NET 的相容性模式來裝載 WCF 服務。
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 765a509f94a0a934cdbbf0212cfc1d4053d29f9c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553313"
---
# <a name="wcf-services-and-aspnet"></a>WCF 服務和 ASP.NET

本主題討論如何與 ASP.NET 並存裝載 Windows Communication Foundation (WCF) 服務，並將其裝載在 ASP.NET 相容性模式中。

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>並行裝載 WCF 與 ASP.NET

裝載于 Internet Information Services (IIS) 的 WCF 服務可以使用來找到。單一、通用應用程式域內的 ASPX 頁面和 .ASMX Web 服務。 ASP.NET 提供一般的基礎結構服務，例如適用于 WCF 和 ASP.NET HTTP runtime 的 AppDomain 管理和動態編譯。 WCF 的預設設定與 ASP.NET 並存。

![顯示 WCF 服務和 ASP .NET：共用狀態的螢幕擷取畫面。](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

ASP.NET HTTP 執行時間會處理 ASP.NET 要求，但不會參與處理 WCF 服務的要求，即使這些服務裝載在與 ASP.NET 內容相同的 AppDomain 中也一樣。 相反地，WCF 服務模型會攔截定址至 WCF 服務的訊息，並透過 WCF 傳輸/通道堆疊路由傳送訊息。

並存模型的結果如下：

- ASP.NET 和 WCF 服務可以共用 AppDomain 狀態。 因為這兩個架構可以並存于相同的 AppDomain 中，所以 WCF 也可以與 ASP.NET (共用 AppDomain 狀態，包括靜態變數、事件等等) 。

- WCF 服務的行為一致，與裝載環境和傳輸無關。 ASP.NET HTTP 執行階段主要用來與 IIS/ASP.NET 裝載環境和 HTTP 通訊搭配使用。 相反地，WCF 的設計是為了一致地在裝載環境中運作， (WCF 在 () IIS 內部和外部都能一致地運作，而在 iis 7.0 和更新版本中裝載的服務，則會在其公開的所有端點之間保持一致的行為，即使某些端點使用 HTTP) 以外的通訊協定也是一樣。

- 在 AppDomain 中，HTTP 執行時間所執行的功能會套用至 ASP.NET 內容，但不適用於 WCF。 ASP.NET 應用程式平臺的許多 HTTP 特定功能，並不適用于裝載于包含 ASP.NET 內容之 AppDomain 內的 WCF 服務。 下列為這些功能的範例：

  - HttpCoNtext： <xref:System.Web.HttpContext.Current%2A> 一律是 `null` 從 WCF 服務中存取時。 請改用 <xref:System.ServiceModel.Channels.RequestContext>。

  - 以檔案為基礎的授權：當您決定是否授權服務要求時，WCF 安全性模型不允許將存取控制清單套用至服務的 .svc 檔案 (ACL) 。

  - 以設定為基礎的 URL 授權：同樣地，WCF 安全性模型不會遵守 System. Web configuration 專案中指定的任何以 URL 為基礎的授權規則 \<authorization> 。 如果服務位於受 ASP 保護的 URL 空間中，則 WCF 要求會忽略這些設定。NET 的 URL 授權規則。

  - HttpModule 擴充性： WCF 裝載基礎結構會在引發事件時攔截 WCF 要求 <xref:System.Web.HttpApplication.PostAuthenticateRequest> ，且不會將處理傳回給 ASP.NET HTTP 管線。 在管線的後續階段中，為了攔截要求而撰寫程式碼的模組不會攔截 WCF 要求。

  - ASP.NET 模擬：根據預設，WCF 要求一律會以 IIS 進程身分識別的形式執行，即使 ASP.NET 設定為使用 System. Web 的 \<identity impersonate="true" /> configuration 選項啟用模擬。

這些限制僅適用于裝載于 IIS 應用程式中的 WCF 服務。 ASP.NET 內容的行為不會受到 WCF 存在的影響。

需要傳統的 HTTP 管線所提供功能的 WCF 應用程式，應該考慮使用與主機和傳輸無關的 WCF 對應專案：

- 以 <xref:System.ServiceModel.OperationContext> 取代 <xref:System.Web.HttpContext>。

- 以 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 取代 ASP.NET 的檔案/URL 授權。

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> 或是自訂層級的通道，以取代 HTTP 模組。

- 使用 WCF 來模擬每項作業，而不是使用 System.object 模擬。

或者，您可以考慮在 WCF 的 ASP.NET 相容性模式中執行您的服務。

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>在 ASP.NET 相容性模式中裝載 WCF 服務

雖然 WCF 模型的設計是要在裝載環境和傳輸之間保持一致，但是在某些情況下，應用程式不需要這種程度的彈性。 WCF 的 ASP.NET 相容性模式適用于不需要在 IIS 外部裝載或透過 HTTP 以外的通訊協定進行通訊的案例，但會使用 ASP.NET Web 應用程式平臺的所有功能。

不同于預設的並存設定，其中 WCF 裝載基礎結構會攔截 WCF 訊息並將其路由傳送至 HTTP 管線，在 ASP.NET 相容性模式中執行的 WCF 服務會完全參與 ASP.NET HTTP 要求生命週期。 在相容性模式中，WCF 服務會透過執行來使用 HTTP 管線 <xref:System.Web.IHttpHandler> ，類似于處理 ASPX 頁面和 .Asmx Web 服務要求的方式。 如此一來，WCF 的運作方式與下列 ASP.NET 功能相同：

- <xref:System.Web.HttpContext>：在 ASP.NET 相容性模式中執行的 WCF 服務可以存取 <xref:System.Web.HttpContext.Current%2A> 和其相關聯的狀態。

- 檔案型授權：在 ASP.NET 相容性模式中執行的 WCF 服務，可以藉由附加檔系統存取控制清單 (Acl) 至服務的 .svc 檔案來保護。

- 可設定的 URL 授權： ASP。當 WCF 服務在 ASP.NET 相容性模式中執行時，會針對 WCF 要求強制執行 NET 的 URL 授權規則。

- <xref:System.Web.HttpModuleCollection> 擴充性：由於在 ASP.NET 相容性模式中執行的 WCF 服務會完全參與 ASP.NET HTTP 要求生命週期，因此在 HTTP 管線中設定的任何 HTTP 模組都能夠在服務叫用前後都能在 WCF 要求上運作。

- ASP.NET 模擬： WCF 服務會使用 ASP.NET 模擬執行緒的目前識別來執行，如果已針對應用程式啟用 ASP.NET 模擬，此執行緒可能會不同于 IIS 進程身分識別。 如果已針對特定服務作業啟用 ASP.NET 模擬和 WCF 模擬，則服務的執行最終會使用從 WCF 取得的身分識別來執行。

WCF 的 ASP.NET 相容性模式是在應用層級啟用，可透過下列設定 (位於應用程式的 Web.config 檔) 中：

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

如果未指定，此值會預設為 `false` 。 的值 `false` 表示在應用程式中執行的所有 WCF 服務都不會在 ASP.NET 相容性模式中執行。

由於 ASP.NET 相容性模式意指的要求處理語義與 WCF 預設值截然不同，因此個別的服務執行可以控制是否在已啟用 ASP.NET 相容性模式的應用程式內執行。 服務可以透過 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 來指出是否支援 ASP.NET 相容性模式。 這個屬性的預設值為 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>。

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

下表說明整個應用程式相容性模式設定如何與個別服務所陳述的支援層級互動：

|整個應用程式的相容性模式設定|[AspNetCompatibilityRequirementsMode]<br /><br /> 設定|觀察結果|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|服務成功啟動。|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|服務成功啟動。|
|aspNetCompatibilityEnabled = " `true` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|當服務接收訊息時，發生啟動錯誤。|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|當服務接收訊息時，發生啟動錯誤。|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|服務成功啟動。|
|aspNetCompatibilityEnabled = " `false` "|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|服務成功啟動。|

> [!NOTE]
> IIS 7.0 和 WAS 可讓 WCF 服務透過 HTTP 以外的通訊協定進行通訊。 不過，在已啟用 ASP.NET 相容性模式的應用程式中執行的 WCF 服務不允許公開非 HTTP 端點。 此類組態會在服務接收其第一則訊息時，產生啟動例外狀況。

如需有關為 WCF 服務啟用 ASP.NET 相容性模式的詳細資訊，請參閱 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> 和 [ASP.NET 相容性](../samples/aspnet-compatibility.md) 範例。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Windows Server AppFabric 裝載功能](/previous-versions/appfabric/ee677189(v=azure.10))
