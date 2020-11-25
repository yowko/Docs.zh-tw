---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032004"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a>FileSystemInfo 擲回的 System.unauthorizedaccessexception。屬性

在 .NET Core 中， <xref:System.UnauthorizedAccessException> 當呼叫端嘗試設定檔案屬性值但沒有寫入權限時，就會擲回。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中， <xref:System.ArgumentException> 當呼叫端嘗試在中設定檔案屬性值， <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> 但沒有寫入權限時，就會擲回。 在 .NET Core 中， <xref:System.UnauthorizedAccessException> 會改為擲回。 在 .NET Core 中 (， <xref:System.ArgumentException> 如果呼叫端嘗試設定不正確檔案屬性，仍會擲回。 ) 

#### <a name="version-introduced"></a>引進的版本

1.0

#### <a name="recommended-action"></a>建議的動作

`catch`視需要修改任何語句，以捕捉 <xref:System.UnauthorizedAccessException> instead of 或以外的 <xref:System.ArgumentException> 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
