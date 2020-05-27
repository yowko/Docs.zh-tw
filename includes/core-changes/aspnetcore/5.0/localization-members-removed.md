---
ms.openlocfilehash: 6deeb7debce9b731f3871b7de0ad8df8a8cdafea
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728270"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a>當地語系化：已移除 ResourceManagerWithCultureStringLocalizer 類別和 WithCulture 介面成員

已移除 .NET 5.0 Preview 1 中的[ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)類別和[WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)方法。

如需內容，請參閱[aspnet/公告 # 346](https://github.com/aspnet/Announcements/issues/346)和[dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324)。 如需這種變更的討論，請參閱[dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 1

#### <a name="old-behavior"></a>舊的行為

在 `ResourceManagerWithCultureStringLocalizer` `ResourceManagerStringLocalizer.WithCulture` [.Net Core 3.0 Preview 3 和更新版本中](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)，類別和方法已過時。

#### <a name="new-behavior"></a>新的行為

已 `ResourceManagerWithCultureStringLocalizer` `ResourceManagerStringLocalizer.WithCulture` 移除 .Net 5.0 Preview 1 中的類別和方法。 如需進行變更的清查，請參閱[dotnet/extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files)的提取要求。

#### <a name="reason-for-change"></a>變更的原因

[ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)類別和[ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)方法通常是當地語系化使用者的混淆來源。 建立自訂的執行時，混淆特別高 <xref:Microsoft.Extensions.Localization.IStringLocalizer> 。 此類別和方法可讓取用者認為 `IStringLocalizer` 實例預期會是「每一語言，每個資源」的印象。 實際上，實例應該只是「每個資源」。 在執行時間， <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 屬性會決定要使用的語言。

#### <a name="recommended-action"></a>建議的動作

停止使用 `ResourceManagerWithCultureStringLocalizer` 類別和 `ResourceManagerStringLocalizer.WithCulture` 方法。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
