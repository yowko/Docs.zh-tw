---
title: 重大變更： TextFormatFlags。 ModifyString 已淘汰
description: 瞭解 .NET 5.0 中的重大變更，其中 TextFormatFlags. ModifyString 欄位已淘汰為警告。
ms.date: 11/05/2020
ms.openlocfilehash: 83dca65a770ccdcd5ce48bb669f5122dc2d5ad77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760613"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a>TextFormatFlags. ModifyString 已淘汰

此 <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 欄位已淘汰，以警告形式出現，而且可能會在未來的 .net 版本中移除。

## <a name="change-description"></a>變更描述

在先前的 .NET 版本中， <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 列舉欄位未標示為過時。 在 .NET 5.0 和更新版本中，它會標示為「已淘汰」為警告。 這個欄位可能會在未來的 .NET 版本中移除。

## <a name="reason-for-change"></a>變更的原因

在某些情況下，將字串傳遞至會 <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 改變字串。 此行為會中斷字串的永久性保證，且可能會導致嚴重的 .NET 執行時間狀態損毀。

## <a name="version-introduced"></a>引進的版本

.NET 5。0

## <a name="recommended-action"></a>建議的動作

更新依賴的任何程式碼 <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
