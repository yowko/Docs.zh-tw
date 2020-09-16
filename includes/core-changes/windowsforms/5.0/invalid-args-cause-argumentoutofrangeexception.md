---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702430"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a>WinForms 屬性現在會擲回 ArgumentOutOfRangeException

某些 Windows Forms 屬性現在會 <xref:System.ArgumentOutOfRangeException> 針對不正確引數擲回，但先前未提供這些引數。

#### <a name="change-description"></a>變更描述

先前，這些屬性 <xref:System.NullReferenceException> <xref:System.IndexOutOfRangeException> <xref:System.ArgumentException> 在傳遞超出範圍的引數時，會擲回不同的例外狀況，例如、或。 從 .NET 5.0 開始，這些屬性現在 <xref:System.ArgumentOutOfRangeException> 會在傳遞的引數超出範圍時擲回。

擲回會 <xref:System.ArgumentOutOfRangeException> 符合 .net 執行時間的行為。 它也可清楚地傳達不正確引數，以改善偵錯工具的體驗。

#### <a name="version-introduced"></a>引進的版本

.NET 5。0

#### <a name="recommended-action"></a>建議的動作

- 更新程式碼以防止傳遞不正確引數。
- 如有必要，請 <xref:System.ArgumentOutOfRangeException> 在設定屬性時處理。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

下表列出受影響的屬性和參數：

> [!div class="mx-tdBreakAll"]
> | 屬性 | 參數名稱 | 已新增版本 |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | 5.0 Preview 5 |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | 5.0 Preview 6 |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | 5.0 Preview 6 |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
