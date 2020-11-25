---
title: 重大變更： IntPtr 和 UIntPtr 執行 >iformattable
description: 深入瞭解 IntPtr 和 UIntPtr 現在執行 >iformattable 的核心 .NET 程式庫中的 .NET 5.0 重大變更。
ms.date: 11/01/2020
ms.openlocfilehash: 0684652cdc2b8cf1d237074263bf0809082b0dcd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760762"
---
# <a name="intptr-and-uintptr-implement-iformattable"></a>IntPtr 和 UIntPtr 實 >iformattable

<xref:System.IntPtr><xref:System.UIntPtr>現在就執行了 <xref:System.IFormattable> 。 檢查支援的函式 <xref:System.IFormattable> 現在可能會針對這些類型傳回不同的結果，因為它們可能會傳入格式規範和文化特性。

## <a name="change-description"></a>變更描述

在舊版的 .NET 中， <xref:System.IntPtr> 則 <xref:System.UIntPtr> 不會執行 <xref:System.IFormattable> 。 檢查的函式 <xref:System.IFormattable> 可能會改為只呼叫 <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> 或 <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> ，這表示不遵守格式規範和文化特性。

在 .NET 5.0 和更新版本中， <xref:System.IntPtr> 並 <xref:System.UIntPtr> 執行 <xref:System.IFormattable> 。 檢查支援的函式 <xref:System.IFormattable> 現在可能會針對這些類型傳回不同的結果，因為它們可能會傳入格式規範和文化特性。

此變更會影響插入字串之類的案例 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> ，以及其他案例。

## <a name="reason-for-change"></a>變更的原因

<xref:System.IntPtr><xref:System.UIntPtr>現在透過和關鍵字在 c # 中提供語言支援 `nint` `nuint` 。 支援型別已更新，可提供接近同位 (，盡可能以其他基本類型（例如）公開的功能) <xref:System.Int32?displayProperty=nameWithType> 。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

如果您不想要在顯示這些類型的值時使用格式規範或自訂文化特性，您可以呼叫的和多載 <xref:System.IntPtr.ToString?displayProperty=nameWithType> <xref:System.UIntPtr.ToString?displayProperty=nameWithType> `ToString()` 。

## <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

### Category

Core .NET libraries

### Affected APIs

Not detectable via API analysis.

-->
