---
ms.openlocfilehash: 584014572ab799e1e3ab2f02c9fbf4fe6b0c17e7
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804918"
---
### <a name="blazor-updated-browser-support"></a>Blazor：已更新瀏覽器支援

ASP.NET Core 5.0 引進了 [新的 Blazor 功能](https://github.com/dotnet/aspnetcore/issues/21514)，其中有些功能與舊版瀏覽器不相容。 ASP.NET Core 5.0 中的 Blazor 所支援的瀏覽器清單已隨之更新。

如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475)。

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="old-behavior"></a>舊的行為

Blazor Server 支援具有足夠 polyfill 的 Microsoft Internet Explorer 11。 Blazor 伺服器和 Blazor WebAssembly 也可在 [舊版 Microsoft Edge](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)中運作。

#### <a name="new-behavior"></a>新的行為

Microsoft Internet Explorer 11 不支援 ASP.NET Core 5.0 中的 Blazor 伺服器。 Blazor 伺服器和 Blazor WebAssembly 無法在舊版 Microsoft Edge 中完整運作。

#### <a name="reason-for-change"></a>變更的原因

ASP.NET Core 5.0 中的新 Blazor 功能與這些舊版瀏覽器不相容，因此會降低這些舊版瀏覽器的使用。 如需詳細資訊，請參閱下列資源：

* [舊版 Microsoft Edge 的 Windows 支援也會在2021年3月9日結束](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [Microsoft 365 的應用程式和服務將于2021年8月17日結束 Microsoft Internet Explorer 11 的支援](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

#### <a name="recommended-action"></a>建議的動作

從這些舊版瀏覽器升級至 [新的 Chromium 式 Microsoft Edge](https://www.microsoft.com/edge)。 對於需要支援這些舊版瀏覽器的 Blazor 應用程式，請使用 ASP.NET Core 3.1。 ASP.NET Core 3.1 中的 Blazor 支援的瀏覽器清單未變更，並記載于 [支援的平臺](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1)上。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!--

#### Affected APIs

Not detectable via API analysis

-->
