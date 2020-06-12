---
ms.openlocfilehash: aab7d8538c875e35c832acc2a6c64beb84d4fb47
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702429"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>WinForms 方法現在會擲回 ArgumentException

有些 Windows Forms 方法現在 <xref:System.ArgumentException> 會針對不正確引數擲回，而先前並未提供。

#### <a name="change-description"></a>變更描述

先前，將非預期或不正確類型的引數傳遞至特定 Windows Forms 方法會導致不定狀態。 從 .NET 5.0 開始，這些方法現在會 <xref:System.ArgumentException> 在傳遞的無效引數時擲回。

擲回會 <xref:System.ArgumentException> 符合 .net 執行時間的行為。 它也會藉由清楚地傳達哪個引數無效，來改善偵錯工具的經驗。

下表列出受影響的方法和參數：

| 方法 | 參數名稱 | 條件 | 已新增版本 |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | 引數的類型不是 <xref:System.Windows.Forms.TabPage> 。 | 5.0 Preview 1 |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | 引數是 `null` 、 <xref:System.String.Empty?displayProperty=nameWithType> 或空白字元。 | 5.0 Preview 5 |

#### <a name="version-introduced"></a>引進的版本

.NET 5。0

#### <a name="recommended-action"></a>建議的動作

- 更新程式碼以避免傳遞不正確引數。
- 如有必要，請 <xref:System.ArgumentException> 在呼叫方法時處理。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>
- <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`

-->
