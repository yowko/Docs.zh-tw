---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449389"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>檔案系統資訊.屬性引發的未經授權的訪問異常

在 .NET Core<xref:System.UnauthorizedAccessException>中，當調用方嘗試設置檔案屬性值但沒有寫入權限時，將引發 。

#### <a name="change-description"></a>變更描述

在 .NET Framework<xref:System.ArgumentException>中，當調用方嘗試在 中<xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>設置檔案屬性值但沒有寫入權限時，將引發 。 在 .NET 核心<xref:System.UnauthorizedAccessException>中，將改為引發 。 （在 .NET Core<xref:System.ArgumentException>中，如果調用方嘗試設置不正確檔案屬性，仍將引發 。

#### <a name="version-introduced"></a>介紹的版本

1.0

#### <a name="recommended-action"></a>建議的動作

根據需要修改`catch`任何語句以捕獲<xref:System.UnauthorizedAccessException>而不是 或 添加<xref:System.ArgumentException>。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
