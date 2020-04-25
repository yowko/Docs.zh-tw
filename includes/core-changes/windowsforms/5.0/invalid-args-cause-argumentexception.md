---
ms.openlocfilehash: 5212c5d9513a8ef5f51693857d0ddb60db4e49b9
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158386"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>WinForms 方法現在會擲回 ArgumentException

有些 Windows Forms 方法現在會<xref:System.ArgumentException>針對不正確引數擲回，而先前並未提供。

#### <a name="change-description"></a>變更描述

先前，將非預期或不正確類型的引數傳遞至特定 Windows Forms 方法會導致不定狀態。 從 .NET 5.0 開始，這些方法現在會在<xref:System.ArgumentException>傳遞的無效引數時擲回。

擲回<xref:System.ArgumentException>會符合 .net 執行時間的行為。 它也會藉由清楚地傳達哪個引數無效，來改善偵錯工具的經驗。

下表列出受影響的方法和參數：

| 方法 | 參數名稱 | 狀況 | 已新增版本 |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | 引數的類型<xref:System.Windows.Forms.TabPage>不是。 | 5.0 Preview 1 |

#### <a name="version-introduced"></a>引進的版本

.NET 5.0 Preview 1

#### <a name="recommended-action"></a>建議的動作

- 更新程式碼以避免傳遞不正確引數。
- 如有必要，請<xref:System.ArgumentException>在呼叫方法時處理。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
