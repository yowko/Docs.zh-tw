---
title: 重大變更： TextInfo. ListSeparator 值變更
description: 瞭解 .NET 5.0 的重大變更，其中 TextInfo 的預設值是在5.0 和5.0.1 版之間變更。
ms.date: 12/10/2020
ms.openlocfilehash: 720d46c1908bcd70812f575a90f580470dbc7f32
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596484"
---
# <a name="textinfolistseparator-values-changed"></a>TextInfo. ListSeparator 值已變更

不同文化特性的預設 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 值已在所有作業系統上變更。

## <a name="change-description"></a>變更描述

在 .NET 5.0.0 中，做為 [從 NLS 切換至 ICU 程式庫](icu-globalization-api.md)的一部分，在 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> Windows 上變更不同文化特性的預設值。 從 Unicode (ICU) 的國際元件取得的十進位分隔符號值，是用來做為 <xref:System.Globalization.TextInfo.ListSeparator> 值。 在 Linux 和 macOS 上，值沒有變更， <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 也就是說，它們會繼續使用小數分隔符號值。

針對 .NET 5.0.1 和更新版本中的所有作業系統，的值 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 相當於從 NLS 取得的值。 若為 Windows，這表示值相當於它們在 .NET Framework 和 .NET Core 1.0-3.1 中的值。 若為 Linux 和 macOS，這些 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 值現在會與 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> Windows 的值相符。

下表摘要說明值的變更 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 。

| | .NET Framework<br/>.NET Core 1.0-3。1 | .NET 5.0 | .NET 5.0。1 |
-|-|-|-
| **Windows** | 從 NLS 取得 | 來自 ICU 的小數分隔符號。<br/>可以切換回 NLS。 | 相當於 NLS |
| **Linux 與 macOS** | 來自 ICU 的小數分隔符號 | 來自 ICU 的小數分隔符號 | 相當於 NLS |

## <a name="version-introduced"></a>引進的版本

5.0.1

## <a name="reason-for-change"></a>變更的原因

開發人員回報在 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 剖析逗點分隔值 (CSV) 檔案時，他們使用屬性，而新的 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 值會中斷該剖析。

## <a name="recommended-action"></a>建議的動作

如果您的程式碼依賴先前的十進位分隔符號值，您可以將所需的值硬式編碼 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=fullName>

<!--

#### Category

- Globalization

### Affected APIs

- `P:System.Globalization.TextInfo.ListSeparator`

-->
