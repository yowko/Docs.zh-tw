---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393910"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>Spa： SpaServices 和 NodeServices 已標示為過時

從 ASP.NET Core 2.1 開始，下列 NuGet 套件的內容都是不必要的。 因此，下列封裝會標示為已淘汰：

- [AspNetCore. SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [AspNetCore. NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

基於相同的原因，下列 npm 模組會標示為已淘汰：

- [aspnet-角度](https://www.npmjs.com/package/aspnet-angular)
- [aspnet-預先呈現](https://www.npmjs.com/package/aspnet-prerendering)
- [aspnet-webpack](https://www.npmjs.com/package/aspnet-webpack)
- [aspnet-webpack-回應](https://www.npmjs.com/package/aspnet-webpack-react)
- [網域-工作](https://www.npmjs.com/package/domain-task)

上述封裝和 npm 模組稍後會在 .NET 5 中移除。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

已淘汰的封裝和 npm 模組旨在將 ASP.NET Core 與各種單一頁面應用程式整合 (SPA) 架構。 這類架構包含了 Redux 的角度、反應和反應。

#### <a name="new-behavior"></a>新的行為

新的整合機制存在於 [AspNetCore. SpaServices. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet 套件中。 從 ASP.NET Core 2.1 開始，此套件仍是角度和反應專案範本的基礎。

#### <a name="reason-for-change"></a>變更的原因

ASP.NET Core 支援與各種單一頁面應用程式整合 (SPA) 架構，包括 Redux 的角度、反應和反應。 一開始，與這些架構的整合是透過處理案例的 ASP.NET Core 特定元件來完成，例如伺服器端預先呈現和與 Webpack 的整合。 隨著時間的進展，產業標準也有所改變。 每個 SPA 架構都會發行自己的標準命令列介面。 例如，「角度」 CLI 和「建立-回應」應用程式。

當 ASP.NET Core 2.1 在5月2018日發行時，小組會回應標準的變更。 提供更簡單且更簡單的方法來與 SPA 架構本身的工具鏈整合。 新的整合機制存在於封裝中 `Microsoft.AspNetCore.SpaServices.Extensions` ，並會在 ASP.NET Core 2.1 之後，保持角度和回應專案範本的基礎。

為了說明舊版 ASP.NET Core 特定的元件是不相關的，而且不建議使用：

- 2.1 之前的整合機制會標示為已淘汰。
- 支援的 npm 套件會標示為已淘汰。

#### <a name="recommended-action"></a>建議的動作

如果您要使用這些套件，請更新您的應用程式以使用此功能：

- 在 `Microsoft.AspNetCore.SpaServices.Extensions` 封裝中。
- 由您所使用的 SPA 架構提供

若要啟用伺服器端預先呈現和熱模組重載等功能，請參閱對應 SPA 架構的檔。 中的功能 `Microsoft.AspNetCore.SpaServices.Extensions` *尚未* 淘汰，而且會繼續受到支援。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
