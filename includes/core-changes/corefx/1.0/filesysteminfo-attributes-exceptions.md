---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449389"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>FileSystemInfo 擲回的 System.unauthorizedaccessexception

在 .NET Core 中，當呼叫端嘗試設定檔案屬性值但不具有寫入權限時，就會擲回 <xref:System.UnauthorizedAccessException>。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中，當呼叫端嘗試在 <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> 中設定檔案屬性值，但沒有寫入權限時，就會擲回 <xref:System.ArgumentException>。 在 .NET Core 中，會改為擲回 <xref:System.UnauthorizedAccessException>。 （在 .NET Core 中，如果呼叫端嘗試設定不正確檔案屬性，仍然會擲回 <xref:System.ArgumentException>）。

#### <a name="version-introduced"></a>引進的版本

1.0

#### <a name="recommended-action"></a>建議的動作

視需要修改任何 `catch` 語句來攔截 <xref:System.UnauthorizedAccessException>，而不是 <xref:System.ArgumentException>。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
