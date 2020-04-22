---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021802"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>檔案系統資訊.屬性引發的未經授權的存取異常

在 .NET<xref:System.UnauthorizedAccessException>Core 中,當呼叫者嘗試設定檔屬性值但沒有寫入權限時,將引發 。

#### <a name="change-description"></a>變更描述

在 .NET Framework<xref:System.ArgumentException>中,當呼叫者<xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>嘗試在 中設定檔屬性值但沒有寫入權限時,將引發 。 在 .NET<xref:System.UnauthorizedAccessException>核心 中,將改為引發 。 (在 .NET<xref:System.ArgumentException>Core 中,如果呼叫者嘗試設定無效的檔案屬性,仍將引發 。

#### <a name="version-introduced"></a>介紹的版本

1.0

#### <a name="recommended-action"></a>建議的動作

根據需要修改`catch`任何敘述以捕捉<xref:System.UnauthorizedAccessException>而不是或<xref:System.ArgumentException>新增 。

#### <a name="category"></a>類別

核心 .NET 函式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
