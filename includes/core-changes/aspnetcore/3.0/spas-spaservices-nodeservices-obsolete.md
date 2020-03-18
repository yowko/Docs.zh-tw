---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393910"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>Spa 服務：標記為過時的 Spa 服務和節點服務

自 ASP.NET Core 2.1 以來，以下 NuGet 包的內容都是不必要的。 因此，以下包被標記為過時：

- [微軟.AspNetCore.Spa服務](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [微軟.AspNetCore.節點服務](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

出於同樣的原因，以下 npm 模組被標記為棄用：

- [阿斯普內角](https://www.npmjs.com/package/aspnet-angular)
- [阿斯普內特預渲染](https://www.npmjs.com/package/aspnet-prerendering)
- [阿斯普內特網包](https://www.npmjs.com/package/aspnet-webpack)
- [阿斯普內特-網路包-反應](https://www.npmjs.com/package/aspnet-webpack-react)
- [域任務](https://www.npmjs.com/package/domain-task)

前面的包和 npm 模組稍後將在 .NET 5 中刪除。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

棄用的套裝軟體和 npm 模組旨在將 ASP.NET 核心與各種單頁應用 （SPA） 框架組成。 此類框架包括角、回應和與 Redux 的回應。

#### <a name="new-behavior"></a>新的行為

[Microsoft.AspNetCore.SpaServices.擴展](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/)NuGet 包中存在一種新的集成機制。 該包仍然是自ASP.NET Core 2.1 以來的"角"和"反應"專案範本的基礎。

#### <a name="reason-for-change"></a>更改原因

ASP.NET核心支援與各種單頁應用 （SPA） 框架組成，包括角、回應和與 Redux 的回應。 最初，與這些框架的集成是通過ASP.NET核心特定的元件完成的，這些元件處理了伺服器端預呈現和與 Webpack 集成等方案。 隨著時間的流逝，行業標準也發生了變化。 每個 SPA 框架都發佈了自己的標準命令列介面。 例如，角 CLI 和創建-回應應用。

當 ASP.NET Core 2.1 于 2018 年 5 月發佈時，團隊對標準的變化做出了回應。 提供了一種更新和更簡單的與 SPA 框架自己的工具鏈集成的方法。 新的集成機制存在於包`Microsoft.AspNetCore.SpaServices.Extensions`中，並且自ASP.NET Core 2.1 以來，它仍然是角和反應專案範本的基礎。

要澄清舊ASP.NET核心特定元件不相關，不建議：

- 2.1 前集成機制標記為過時。
- 支援的 npm 包被標記為已棄用。

#### <a name="recommended-action"></a>建議的動作

如果您正在使用這些包，請更新應用以使用以下功能：

- 在包`Microsoft.AspNetCore.SpaServices.Extensions`中。
- 由您使用的 SPA 框架提供

要啟用伺服器端預渲染和熱模組重新載入等功能，請參閱相應 SPA 框架的文檔。 中的`Microsoft.AspNetCore.SpaServices.Extensions`功能*未*過時，將繼續受支援。

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
