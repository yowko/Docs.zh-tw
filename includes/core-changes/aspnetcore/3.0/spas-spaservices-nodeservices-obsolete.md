---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393910"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>Spa：已標記為過時的 SpaServices 和 NodeServices

下列 NuGet 套件的內容在 ASP.NET Core 2.1 之後都是不必要的。 因此，下列套件會標示為已淘汰：

- [AspNetCore. SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [AspNetCore. NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

基於相同原因，下列 npm 模組會標示為已淘汰：

- [aspnet-角度](https://www.npmjs.com/package/aspnet-angular)
- [aspnet-預先呈現](https://www.npmjs.com/package/aspnet-prerendering)
- [aspnet-webpack](https://www.npmjs.com/package/aspnet-webpack)
- [aspnet-webpack-回應](https://www.npmjs.com/package/aspnet-webpack-react)
- [網域-工作](https://www.npmjs.com/package/domain-task)

先前的套件和 npm 模組稍後會在 .NET 5 中移除。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

已淘汰的封裝和 npm 模組主要是用來整合 ASP.NET Core 與各種單頁應用程式（SPA）架構。 這類架構包含 Redux 的角度、反應和回應。

#### <a name="new-behavior"></a>新的行為

新的整合機制存在於[AspNetCore. SpaServices （擴充](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/)功能） NuGet 套件中。 從 ASP.NET Core 2.1 開始，套件仍然是「角度」和「回應」專案範本的基礎。

#### <a name="reason-for-change"></a>變更的原因

ASP.NET Core 支援與各種單頁應用程式（SPA）架構整合，包括 Redux 的角度、反應和回應。 一開始，與這些架構的整合是透過 ASP.NET Core 特定元件來完成，這些元件會處理案例，例如伺服器端預先呈現和與 Webpack 的整合。 隨著時間進展，產業標準也有所改變。 每個 SPA 架構都會發行自己的標準命令列介面。 例如，「角度」 CLI 和「建立-回應」應用程式。

當 ASP.NET Core 2.1 于5月2018日發行時，小組會回應標準的變更。 提供較新且更簡單的方式來與 SPA 架構本身的工具鏈整合。 新的整合機制存在於套件中 `Microsoft.AspNetCore.SpaServices.Extensions`，而且從 ASP.NET Core 2.1 開始，仍然是「角度」和「回應」專案範本的基礎。

若要闡明舊版 ASP.NET Core 特定的元件是不相關的，而且不建議使用：

- 2\.1 前的整合機制會標示為已淘汰。
- 支援的 npm 封裝會標示為已淘汰。

#### <a name="recommended-action"></a>建議的動作

如果您要使用這些套件，請更新您的應用程式以使用功能：

- 在 `Microsoft.AspNetCore.SpaServices.Extensions` 封裝中。
- 由您所使用的 SPA 架構提供

若要啟用伺服器端預先呈現和經常性模組重載之類的功能，請參閱對應 SPA 架構的檔。 @No__t-0 中的功能*並未*淘汰，而且會繼續受到支援。

#### <a name="category"></a>分類

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
