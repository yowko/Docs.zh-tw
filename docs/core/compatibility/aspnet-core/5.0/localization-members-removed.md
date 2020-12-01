---
title: 重大變更：當地語系化：已移除 ResourceManagerWithCultureStringLocalizer 類別和 WithCulture 介面成員
description: 瞭解 ASP.NET Core 5.0 的重大變更，其標題為當地語系化：已移除 ResourceManagerWithCultureStringLocalizer 類別和 WithCulture 介面成員
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: ac7723cd9b961b34b3f87a55119d421668c87417
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437855"
---
# <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a>當地語系化：已移除 ResourceManagerWithCultureStringLocalizer 類別和 WithCulture 介面成員

[ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)類別和[WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)方法已在 .net 5.0 Preview 1 中移除。

如需相關內容，請參閱 [aspnet/公告 # 346](https://github.com/aspnet/Announcements/issues/346) 和 [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324)。 如需此變更的討論，請參閱 [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756)。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 1

## <a name="old-behavior"></a>舊的行為

`ResourceManagerWithCultureStringLocalizer`類別和 `ResourceManagerStringLocalizer.WithCulture` 方法[在 .Net Core 3.0 Preview 3 和更新版本中已淘汰](../../3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)。

## <a name="new-behavior"></a>新的行為

`ResourceManagerWithCultureStringLocalizer`類別和方法已 `ResourceManagerStringLocalizer.WithCulture` 在 .Net 5.0 Preview 1 中移除。 如需進行變更的清查，請參閱 [dotnet/extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files)的提取要求。

## <a name="reason-for-change"></a>變更的原因

[ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)類別和[ResourceManagerStringLocalizer 的 WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)方法通常是當地語系化使用者的混淆來源。 建立自訂執行時，混淆特別高 <xref:Microsoft.Extensions.Localization.IStringLocalizer> 。 這個類別和方法可讓取用者認為 `IStringLocalizer` 實例應該是「每個語言、每個資源」的印象。 實際上，實例應該只是「每個資源」。 在執行時間， <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 屬性會決定要使用的語言。

## <a name="recommended-action"></a>建議的動作

停止使用 `ResourceManagerWithCultureStringLocalizer` 類別和 `ResourceManagerStringLocalizer.WithCulture` 方法。

## <a name="affected-apis"></a>受影響的 API

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
