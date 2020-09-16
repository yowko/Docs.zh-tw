---
ms.openlocfilehash: 62a5f56bb7fffc453623a2c3202f288a19110158
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539452"
---
### <a name="localization-pubternal-apis-removed"></a>當地語系化：已移除 "Pubternal" Api

為了更妥善維護 ASP.NET Core 的公用 API 介面，已 :::no-loc text="\"pubternal\""::: 移除部分當地語系化 api。 :::no-loc text="\"pubternal\"":::API 具有 `public` 存取修飾詞，而且是在表示[內部](../../../../docs/csharp/language-reference/keywords/internal.md)意圖的命名空間中定義。

如需討論，請參閱 [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 6

#### <a name="old-behavior"></a>舊的行為

下列 Api 為 `public` ：

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` 接受下列其中一個參數類型的函式多載：
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a>新的行為

下列清單概述這些變更：

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`已成為，現在是 `internal` 。
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`已成為，現在是 `internal` 。
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` 現在接受下列其中一個參數類型的函式多載 `internal` ：
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a>變更的原因

在 [aspnet/公告 # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)上更詳盡地說明， :::no-loc text="\"pubternal\""::: 類型已從 `public` API 介面中移除。 這些變更會將更多類別調整為該設計決策。 有問題的類別是為了團隊內部測試的擴充點。

#### <a name="recommended-action"></a>建議的動作

雖然不太可能，但有些應用程式可能會刻意或意外相依于這些 :::no-loc text="\"pubternal\""::: 類型。 請參閱 [新的行為](#new-behavior) 章節，以判斷如何從類型遷移。

如果您已識別出此變更之前所允許的公用 API，但目前尚未進行的案例，請在 [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)提出問題。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
