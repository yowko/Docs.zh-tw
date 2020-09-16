---
ms.openlocfilehash: 3d29848e12d496d2d53c204e00ef8604831495e1
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024691"
---
### <a name="intptr-and-uintptr-implement-iformattable"></a>IntPtr 和 UIntPtr 實 >iformattable

<xref:System.IntPtr><xref:System.UIntPtr>現在就執行了 <xref:System.IFormattable> 。 檢查支援的函式 <xref:System.IFormattable> 現在可能會針對這些類型傳回不同的結果，因為它們可能會傳入格式規範和文化特性。

#### <a name="change-description"></a>變更描述

在舊版的 .NET 中， <xref:System.IntPtr> 則 <xref:System.UIntPtr> 不會執行 <xref:System.IFormattable> 。 檢查的函式 <xref:System.IFormattable> 可能會改為只呼叫 <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> 或 <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> ，這表示不遵守格式規範和文化特性。

在 .NET 5.0 和更新版本中， <xref:System.IntPtr> 並 <xref:System.UIntPtr> 執行 <xref:System.IFormattable> 。 檢查支援的函式 <xref:System.IFormattable> 現在可能會針對這些類型傳回不同的結果，因為它們可能會傳入格式規範和文化特性。

此變更會影響插入字串之類的案例 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> ，以及其他案例。

#### <a name="reason-for-change"></a>變更的原因

<xref:System.IntPtr><xref:System.UIntPtr>現在透過和關鍵字在 c # 中提供語言支援 `nint` `nuint` 。 支援型別已更新，可提供接近同位 (，盡可能以其他基本類型（例如）公開的功能) <xref:System.Int32?displayProperty=nameWithType> 。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 4

#### <a name="recommended-action"></a>建議的動作

如果您不想要在顯示這些類型的值時使用格式規範或自訂文化特性，您可以呼叫的和多載 <xref:System.IntPtr.ToString?displayProperty=nameWithType> <xref:System.UIntPtr.ToString?displayProperty=nameWithType> `ToString()` 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
