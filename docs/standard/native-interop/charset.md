---
title: 字元集和封送處理 - .NET
description: 了解 CharSet 的不同值如何變更 .NET 將您的資料封送處理為機器碼的方式。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2ff6c485906db481cb5236f83e885ba9fd46450b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "56411360"
---
# <a name="charsets-and-marshalling"></a>字元集和封送處理

`char` 值、`string` 物件與 `System.Text.StringBuilder` 物件的封送處理方式取決於 P/Invoke 或結構上之 `CharSet` 欄位的值。 您可以透過在宣告您的 P/Invoke 時設定 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 欄位，以設定 P/Invoke 的 `CharSet`。 若要為結構設定 `CharSet`，請在您的結構宣告上設定 <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> 欄位。 當這些屬性欄位未設定時，語言編譯器可決定要使用的 `CharSet`。 C# 預設使用 <xref:System.Runtime.InteropServices.CharSet.Ansi> 字元集。

下表說明每個字元集與使用該字元集進行封送處理時，如何代表字元集或字串：

| 字元集 | Windows | Unix | Unix 為 Mono |
|---------|---------|-------|-------|
| Ansi    | `char` (ANSI)  | `char` (macOS 上為 ANSI，Linux 上為 UTF-8) | `char` (UTF-8) |
| Unicode | `wchar_t` (UTF-16) | `char16_t` (UTF-16) | `char16_t` (UTF-16) |
| 自動 | `wchar_t` (UTF-16) | `char16_t` (UTF-16) | `char` (UTF-8) |

選擇您的字元集時，請確定您知道您原生代表的代表應該是什麼樣子。
