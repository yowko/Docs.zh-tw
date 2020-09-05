---
ms.openlocfilehash: 0c3876d30a80501a89f3a37ce24e2f71122c1b44
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496531"
---
### <a name="systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a><span data-ttu-id="47cac-101">System.ServiceModel.Web.WebServiceHost 物件不會再新增預設端點</span><span class="sxs-lookup"><span data-stu-id="47cac-101">System.ServiceModel.Web.WebServiceHost object no longer adds a default endpoint</span></span>

#### <a name="details"></a><span data-ttu-id="47cac-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="47cac-102">Details</span></span>

<span data-ttu-id="47cac-103">如果應用程式程式碼加入明確的端點，<xref:System.ServiceModel.Web.WebServiceHost> 物件將不再加入預設端點。</span><span class="sxs-lookup"><span data-stu-id="47cac-103">The <xref:System.ServiceModel.Web.WebServiceHost> object no longer adds a default endpoint if an explicit endpoint has been added by application code.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="47cac-104">建議</span><span class="sxs-lookup"><span data-stu-id="47cac-104">Suggestion</span></span>

<span data-ttu-id="47cac-105">如果使用者希望能夠連線到預設端點，而且 <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName> 已新增其他明確的端點，也應該明確新增預設端點 (使用 <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>)。</span><span class="sxs-lookup"><span data-stu-id="47cac-105">If users will expect to be able to connect to a default endpoint and other explicit endpoints have been added to the <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, default endpoints should also be added explicitly (using <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span></span>

| <span data-ttu-id="47cac-106">名稱</span><span class="sxs-lookup"><span data-stu-id="47cac-106">Name</span></span>    | <span data-ttu-id="47cac-107">值</span><span class="sxs-lookup"><span data-stu-id="47cac-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="47cac-108">範圍</span><span class="sxs-lookup"><span data-stu-id="47cac-108">Scope</span></span>   |<span data-ttu-id="47cac-109">Minor</span><span class="sxs-lookup"><span data-stu-id="47cac-109">Minor</span></span>|
|<span data-ttu-id="47cac-110">版本</span><span class="sxs-lookup"><span data-stu-id="47cac-110">Version</span></span>|<span data-ttu-id="47cac-111">4.5</span><span class="sxs-lookup"><span data-stu-id="47cac-111">4.5</span></span>|
|<span data-ttu-id="47cac-112">類型</span><span class="sxs-lookup"><span data-stu-id="47cac-112">Type</span></span>|<span data-ttu-id="47cac-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="47cac-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="47cac-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="47cac-114">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`

-->
