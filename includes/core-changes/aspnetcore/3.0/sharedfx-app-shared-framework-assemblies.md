---
ms.openlocfilehash: d598d8d3203e804e5e935c3564b0053f9fc2e9a6
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144958"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>共用架構：已從 AspNetCore 移除元件

從 ASP.NET Core 3.0 開始，ASP.NET Core 共用架構 (`Microsoft.AspNetCore.App`) 僅包含由 Microsoft 完全開發、支援和維護的第一方元件。

#### <a name="change-description"></a>變更描述

重新定義 ASP.NET Core 「平臺」的界限時，請考慮變更。 共用架構會 [由任何人透過 GitHub 進行來源可建置](https://github.com/dotnet/source-build) ，並且將繼續為您的應用程式提供 .net Core 共用架構的現有優點。 某些優點包括較小的部署大小、集中式修補，以及更快速的啟動時間。

在變更過程中，會介紹一些值得注意的重大變更 `Microsoft.AspNetCore.App` 。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

透過專案檔中的專案所參考的專案 `Microsoft.AspNetCore.App` `<PackageReference>` 。

此外，也 `Microsoft.AspNetCore.App` 包含下列子元件：

- Json.NET (`Newtonsoft.Json`) 
- Entity Framework Core (前面加上 `Microsoft.EntityFrameworkCore.`) 的元件
- Roslyn (`Microsoft.CodeAnalysis`) 

#### <a name="new-behavior"></a>新的行為

參考 `Microsoft.AspNetCore.App` 不再需要專案檔中的 `<PackageReference>` 元素。 .NET Core SDK 支援名為的新專案 `<FrameworkReference>` ，此專案會取代的使用 `<PackageReference>` 。

如需詳細資訊，請參閱 [dotnet/aspnetcore # 3612](https://github.com/dotnet/aspnetcore/issues/3612)。

Entity Framework Core 隨附于 NuGet 套件。 此變更會將出貨模型與 .NET 上的所有其他資料存取程式庫對齊。 它提供 Entity Framework Core 最簡單的路徑，以繼續進行創新，同時支援各種不同的 .NET 平臺。 將 Entity Framework Core 移出共用架構並不會影響其狀態，因為它是由 Microsoft 開發、支援和可以維修的程式庫。 [.Net Core 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)會持續涵蓋此原則。

Json.NET 和 Entity Framework Core 繼續使用 ASP.NET Core。 不過，它們不會包含在共用架構中。

如需詳細資訊，請參閱 [.Net Core 3.0 中的 JSON 未來](https://github.com/dotnet/announcements/issues/90)。 另請參閱從共用架構移除 [之二進位檔的完整清單](https://github.com/dotnet/aspnetcore/issues/3755) 。

#### <a name="reason-for-change"></a>變更的原因

這項變更可簡化 `Microsoft.AspNetCore.App` NuGet 套件與共享架構之間的耗用量，並減少重複的使用。

如需此變更動機的詳細資訊，請參閱 [這篇 blog 文章](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)。

#### <a name="recommended-action"></a>建議的動作

專案不需要在中使用元件 `Microsoft.AspNetCore.App` 做為 NuGet 套件。 為了簡化 ASP.NET Core 共用架構的目標和使用方式，自 ASP.NET Core 1.0 以來出貨的許多 NuGet 套件都不再產生。 這些套件提供的 Api 仍可使用到應用程式 `<FrameworkReference>` `Microsoft.AspNetCore.App` 。 常見的 API 範例包括 Kestrel、MVC 和 Razor。

這項變更不適用於在 ASP.NET Core 2.x 中參考的所有二進位檔 `Microsoft.AspNetCore.App` 。 值得注意的例外狀況包括：

- `Microsoft.Extensions` 繼續以 .NET Standard 為目標的程式庫會以 NuGet 套件的形式提供， (請參閱 <https://github.com/dotnet/extensions>) 。
- 不屬於的 ASP.NET Core 團隊所產生的 Api `Microsoft.AspNetCore.App` 。 例如，下列元件可作為 NuGet 套件：
  - Entity Framework Core
  - 提供協力廠商整合的 Api
  - 實驗性功能
  - 具有相依性的 Api 無法 [滿足在共用架構中的需求](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- 維護 Json.NET 支援的 MVC 延伸模組。 API 將會以 NuGet 套件的形式提供，以支援使用 Json.NET 和 MVC。
- SignalR .NET 用戶端將繼續支援 .NET Standard，並以 NuGet 套件的形式寄出。 它的目的是要在許多 .NET 執行時間（例如 Xamarin 和 UWP）上使用。

如需詳細資訊，請參閱 [在3.0 中停止產生共用架構元件的封裝](https://github.com/dotnet/aspnetcore/issues/3756)。 如需討論，請參閱 [dotnet/aspnetcore # 3757](https://github.com/dotnet/aspnetcore/issues/3757)。

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
