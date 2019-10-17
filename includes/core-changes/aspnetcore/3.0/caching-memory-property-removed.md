---
ms.openlocfilehash: 7d40324e6b0bc4afab9dd39b236f0909f360cc9b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394149"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Caching： CompactOnMemoryPressure 屬性已移除

ASP.NET Core 3.0 版本已移除[過時的 MemoryCacheOptions api](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)。

#### <a name="change-description"></a>變更描述

這是對[aspnet/Caching # 221](https://github.com/aspnet/Caching/issues/221)的後續變更。 如需討論，請參閱[aspnet/Extensions # 1062](https://github.com/aspnet/Extensions/issues/1062)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`MemoryCacheOptions.CompactOnMemoryPressure` 屬性可用。

#### <a name="new-behavior"></a>新的行為

已移除 `MemoryCacheOptions.CompactOnMemoryPressure` 屬性。

#### <a name="reason-for-change"></a>變更的原因

自動壓縮快取會造成問題。 為避免非預期的行為，只有在需要時才壓縮快取。

#### <a name="recommended-action"></a>建議的動作

若要壓縮快取，請向 `MemoryCache` 的向下轉換，並在需要時呼叫 `Compact`。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
