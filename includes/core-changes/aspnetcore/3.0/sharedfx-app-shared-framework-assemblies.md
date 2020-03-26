---
ms.openlocfilehash: 64e854b06895ca54a9ab9870b85868788a731c00
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549595"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>共用框架：從 Microsoft 中刪除程式集. AspNetCore.App

從 ASP.NET Core 3.0 開始，ASP.NET核心`Microsoft.AspNetCore.App`共用框架 （ ） 僅包含由 Microsoft 完全開發、支援並可維修的第一方程式集。

#### <a name="change-description"></a>變更描述

將更改視為重新定義ASP.NET核心"平臺"的邊界。 共用框架將由[任何人通過 GitHub 進行原始程式碼構建](https://github.com/dotnet/source-build)，並將繼續為您的應用提供 .NET Core 共用框架的現有優勢。 一些優勢包括較小的部署大小、集中式修補和更快的啟動時間。

作為變革的一部分，在 中`Microsoft.AspNetCore.App`引入了一些顯著的重大重大變革。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

通過專案`Microsoft.AspNetCore.App`檔中`<PackageReference>`的元素引用的專案。

此外，`Microsoft.AspNetCore.App`包含以下子元件：

- Json.NET`Newtonsoft.Json`（ ）
- 實體框架核心（與`Microsoft.EntityFrameworkCore.`的預綴程式集。
- 羅斯林`Microsoft.CodeAnalysis`（ ）

#### <a name="new-behavior"></a>新的行為

對`Microsoft.AspNetCore.App`不再需要專案檔案中的元素`<PackageReference>`的引用。 .NET 核心 SDK 支援一個名為`<FrameworkReference>`的新元素，它取代了`<PackageReference>`的使用。

有關詳細資訊，請參閱[點網/阿斯平核心#3612](https://github.com/dotnet/aspnetcore/issues/3612)。

實體框架核心作為 NuGet 包提供。 此更改使發貨模型與 .NET 上的所有其他資料訪問庫對齊。 它為實體框架核心提供了最簡單的路徑，以繼續創新，同時支援各種 .NET 平臺。 實體框架核心從共用框架中移出不會影響其作為 Microsoft 開發、支援和服務庫的狀態。 [.NET 核心支援策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)繼續涵蓋它。

Json.NET和實體框架核心繼續與ASP.NET核心合作。 但是，它們不會包含在共用框架中。

有關詳細資訊，請參閱[.NET 核心 3.0 中的 JSON 的未來](https://github.com/dotnet/announcements/issues/90)。 另請參閱從共用框架中刪除[的二進位檔案的完整清單](https://github.com/dotnet/aspnetcore/issues/3755)。

#### <a name="reason-for-change"></a>更改原因

此更改簡化了 NuGet`Microsoft.AspNetCore.App`包和共用框架之間的使用並減少了重複。

有關此更改的動機的詳細資訊，請參閱[此博客文章](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)。

#### <a name="recommended-action"></a>建議的動作

專案無需`Microsoft.AspNetCore.App`將程式集用作 NuGet 包。 為了簡化ASP.NET核心共用框架的定位和使用，不再生產自ASP.NET Core 1.0 以來發貨的許多 NuGet 包。 這些包提供的 API 仍可用於應用使用`<FrameworkReference>`。 `Microsoft.AspNetCore.App` 常見的 API 示例包括 Kestrel、MVC 和 Razor。

此更改不適用於通過`Microsoft.AspNetCore.App`ASP.NET Core 2.x 中引用的所有二進位檔案。 值得注意的例外包括：

- `Microsoft.Extensions`繼續以 .NET 標準為目標的庫將作為 NuGet 包提供（https://github.com/dotnet/extensions)請參閱 ）。
- 由不屬於 的ASP.NET核心團隊生成的`Microsoft.AspNetCore.App`API。 例如，以下元件可作為 NuGet 包提供：
  - Entity Framework Core
  - 提供協力廠商集成的 API
  - 實驗性功能
  - 具有無法滿足[共用框架中要求](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)的依賴項的 API
- MVC 的擴展，用於維護對Json.NET的支援。 API 將作為 NuGet 包提供，以支援使用Json.NET和 MVC。
- SignalR .NET 用戶端將繼續支援 .NET 標準，並作為 NuGet 包發貨。 它適用于許多 .NET 運行時，如 Xamarin 和 UWP。

有關詳細資訊，請參閱[停止在 3.0 中為共用框架程式集生成包](https://github.com/dotnet/aspnetcore/issues/3756)。 有關討論，請參閱[點網/阿斯平核心#3757](https://github.com/dotnet/aspnetcore/issues/3757)。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
