---
title: WCF 服務與 ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 80f4f9a473f223928981ee3f0c2e9f2464cbafaf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935563"
---
# <a name="wcf-services-and-aspnet"></a>WCF 服務與 ASP.NET

本主題討論裝載 Windows Communication Foundation (WCF) 服務的並行使用 ASP.NET 和裝載在 ASP.NET 相容性模式中。

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>裝載 WCF-並存使用 ASP.NET

裝載在網際網路資訊服務 (IIS) 中的 WCF 服務可以位於與。ASPX 頁面和 ASMX Web 服務位於單一、 共同的應用程式定義域。 ASP.NET 提供通用的基礎結構服務，例如 AppDomain 管理與 WCF 和 ASP.NET HTTP 執行階段動態編譯。 WCF 的預設組態會並排顯示使用 ASP.NET。

![螢幕擷取畫面顯示 WCF 服務與 ASP.NET： 共用狀態。](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

ASP.NET HTTP 執行階段會處理 ASP.NET 要求，但不會參與處理要求目的地的 WCF 服務，即使這些服務裝載於相同的 AppDomain，與是 ASP.NET 的內容。 相反地，WCF 服務模型會攔截訊息定址到 WCF 服務，並透過 WCF 傳輸/通道堆疊路由傳送。

並存模型的結果如下：

- ASP.NET 和 WCF 服務可以共用 AppDomain 狀態。 因為這兩個架構可以共存於相同的 AppDomain 中，WCF 也可以使用 （包括靜態變數、 事件等等） 的 ASP.NET 共用 AppDomain 狀態。

- WCF 服務的行為一致、 獨立的裝載環境和傳輸。 ASP.NET HTTP 執行階段主要用來與 IIS/ASP.NET 裝載環境和 HTTP 通訊搭配使用。 相反地，WCF 設計來跨裝載環境有一致的行為 (WCF 採取一致的行為 IIS 內部與外部) 與各種傳輸 (裝載於 IIS 7.0 和更新版本的服務有一致的行為，公開的所有端點即使這些端點的一些使用 HTTP 以外的通訊協定）。

- 在 AppDomain 中，HTTP 執行階段所實作的功能會套用到 ASP.NET 內容，而非 WCF。 ASP.NET 應用程式平台的許多 HTTP 特定功能並不適用於在 AppDomain，其中包含 ASP.NET 內容內裝載的 WCF 服務。 下列為這些功能的範例：

    - HttpContext:<xref:System.Web.HttpContext.Current%2A>總是`null`時從 WCF 服務內存取。 請改用 <xref:System.ServiceModel.Channels.RequestContext>。

    - 檔案為基礎的授權：WCF 安全性模型不允許套用至服務的.svc 檔案，決定是否被授權服務要求時存取控制清單 (ACL)。

    - 以組態為基礎的 URL 授權：同樣地，WCF 安全性模型不會遵守任何在 System.Web 之指定的 URL 架構授權規則\<授權 > 組態項目。 如果服務駐留在受到 ASP 的 URL 空間 WCF 要求會忽略這些設定。NET 的 URL 授權規則。

    - HttpModule 擴充性：WCF 的裝載基礎結構會攔截 WCF 要求時<xref:System.Web.HttpApplication.PostAuthenticateRequest>，就會引發事件，並不會傳回處理 ASP.NET HTTP 管線。 已編碼成要在管線的後續階段攔截要求的模組不會攔截 WCF 要求。

    - ASP.NET 模擬：根據預設，WCF 要求一律執行以 IIS 處理序身分識別，即使 ASP.NET 設定為啟用模擬使用 System.Web 的\<identity impersonate ="true"/ > 組態選項。

這些限制僅適用於 IIS 應用程式中裝載的 WCF 服務。 ASP.NET 內容行為不會受到 WCF 存在。

需要傳統上由 HTTP 管線提供功能的 WCF 應用程式應該考慮使用 WCF 對等，此項目會受到主機與傳輸影響：

- 以 <xref:System.ServiceModel.OperationContext> 取代 <xref:System.Web.HttpContext>。

- 以 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 取代 ASP.NET 的檔案/URL 授權。

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> 或是自訂層級的通道，以取代 HTTP 模組。

- 每個作業取代 System.Web 模擬使用 WCF 模擬。

或者，您可以考慮在 WCF 的 ASP.NET 相容性模式中執行您的服務。

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>在 ASP.NET 相容性模式中裝載 WCF 服務

雖然 WCF 模型設計成各種裝載環境與傳輸有一致的行為，是彈性的通常應用程式不需要這麼大的案例。 WCF 的 ASP.NET 相容性模式是適用於不需要主機 IIS 外部或透過 HTTP 以外的通訊協定進行通訊的能力，但使用的所有 ASP.NET Web 應用程式平台功能的案例。

不同於預設並排顯示設定，其中 WCF 裝載基礎結構會攔截 WCF 訊息，並將它們路由傳送至 HTTP 管線外，在 ASP.NET 相容性模式中執行的 WCF 服務充分參與 ASP.NET HTTP 要求的生命週期。 在相容性模式中，WCF 服務會使用透過 HTTP 管線<xref:System.Web.IHttpHandler>實作，如處理 ASPX 頁面和 ASMX Web 服務的類似方式要求。 如此一來，WCF 行為與相同 ASMX 對於下列的 ASP.NET 功能：

- <xref:System.Web.HttpContext>：在 ASP.NET 相容性模式中執行的 WCF 服務可以存取<xref:System.Web.HttpContext.Current%2A>和其相關聯的狀態。

- 檔案為基礎的授權：藉由附加至服務的.svc 檔案的檔案系統存取控制清單 (Acl)，在 ASP.NET 相容性模式中執行的 WCF 服務可以是安全的。

- 可設定的 URL 授權：ASP。在 ASP.NET 相容性模式中執行 WCF 服務時，NET 的 URL 授權規則會強制執行的 WCF 要求。

- <xref:System.Web.HttpModuleCollection> 擴充性：由於 ASP.NET 相容性模式中執行的 WCF 服務完全參與 ASP.NET HTTP 要求的生命週期中，設定 HTTP 管線中的任何 HTTP 模組可對 WCF 要求之前和之後服務引動過程。

- ASP.NET 模擬：WCF 服務執行使用目前的身分識別的 ASP.NET 模擬執行緒，可能會不同於 IIS 處理序身分識別，如果應用程式啟用 ASP.NET 模擬。 如果 ASP.NET 模擬與 WCF 模擬同時啟用特定服務作業，服務實作最終會執行使用取自 WCF 的身分識別。

WCF 的 ASP.NET 相容性模式啟用應用程式層級透過下列組態 （位於應用程式的 Web.config 檔案中）：

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

這個值預設為"`true`"若未指定。 此值設定為"`false`"表示所有應用程式中執行的 WCF 服務會在 ASP.NET 相容性模式中執行。

個別的服務實作 ASP.NET 相容性模式所隱含的要求處理語意在本質上不同於 WCF 預設值，因為有控制能力，無論是哪一個 asp.net 應用程式內執行已啟用相容性模式。 服務可以透過 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 來指出是否支援 ASP.NET 相容性模式。 這個屬性的預設值為 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>。

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
> IIS 7.0 和 WAS 允許透過 HTTP 以外的通訊協定進行通訊的 WCF 服務。 不過，在已啟用 ASP.NET 相容性模式的應用程式中執行的 WCF 服務不允許公開非 HTTP 端點。 此類組態會在服務接收其第一則訊息時，產生啟動例外狀況。

如需啟用 WCF 服務的 ASP.NET 相容性模式的詳細資訊，請參閱 <<c0> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> 而[ASP.NET 相容性](../samples/aspnet-compatibility.md)範例。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))