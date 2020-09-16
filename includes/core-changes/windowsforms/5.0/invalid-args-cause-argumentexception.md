---
ms.openlocfilehash: 9f6703c77e17ac9376aee944b891f4635dc7632e
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309133"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>WinForms 方法現在會擲回 ArgumentException

某些 Windows Forms 方法現在會 <xref:System.ArgumentException> 針對不正確引數擲回，但先前未提供這些引數。

#### <a name="change-description"></a>變更描述

先前，將非預期或不正確類型的引數傳遞至特定的 Windows Forms 方法會導致不定的狀態。 從 .NET 5.0 開始，這些方法現在會 <xref:System.ArgumentException> 在傳遞無效引數時擲回。

擲回會 <xref:System.ArgumentException> 符合 .net 執行時間的行為。 它也可清楚地傳達不正確引數，以改善偵錯工具的體驗。

#### <a name="version-introduced"></a>引進的版本

.NET 5。0

#### <a name="recommended-action"></a>建議的動作

- 更新程式碼以防止傳遞不正確引數。
- 如有必要，請 <xref:System.ArgumentException> 在呼叫方法時處理。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

下表列出受影響的方法和參數：

| 方法 | 參數名稱 | 條件 | 已新增版本 |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | 引數的類型不是 <xref:System.Windows.Forms.TabPage> 。 | Preview 1 |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | 引數是 `null` 、 <xref:System.String.Empty?displayProperty=nameWithType> 或空白字元。 | Preview 5 |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | 無法取得 `InputLanguage` 指定文化特性的。 | Preview 7 |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

-->
