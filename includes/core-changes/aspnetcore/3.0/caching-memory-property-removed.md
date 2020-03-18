---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901632"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>緩存：已刪除 CompactOn 記憶體壓力屬性

ASP.NET核心 3.0 版本刪除了[過時的記憶體緩存選項 API](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)。

#### <a name="change-description"></a>變更描述

此更改是[aspnet/Caching_221 的](https://github.com/aspnet/Caching/issues/221)後續操作。 有關討論，請參閱[點網/擴展\1062](https://github.com/dotnet/extensions/issues/1062)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`MemoryCacheOptions.CompactOnMemoryPressure`屬性可用。

#### <a name="new-behavior"></a>新的行為

屬性`MemoryCacheOptions.CompactOnMemoryPressure`已被刪除。

#### <a name="reason-for-change"></a>更改原因

自動壓縮緩存會導致問題。 為了避免意外行為，僅在需要時才壓縮緩存。

#### <a name="recommended-action"></a>建議的動作

要壓縮緩存，請向下轉換到`MemoryCache`並在需要時`Compact`調用。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
