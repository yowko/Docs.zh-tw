---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643988"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性參數

在 .NET Framework 4.6.1 中引進的 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 相容性參數，在 .NET Core 3.0 的 Windows Forms 中不受支援。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.6.1 開始，選取<kbd>Ctrl</kbd> + <xref:System.Windows.Forms.TextBox> 控制項中<kbd>的</kbd>快速鍵選取所有文字。 在 .NET Framework 4.6 和舊版中，如果[ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled)和 <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> 屬性都設定為 `true`，則選取<kbd>Ctrl</kbd> <kbd> + 快速鍵</kbd>無法選取所有文字。 .NET Framework 4.6.1 中引進了 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 相容性參數，以保留原始的行為。 如需詳細資訊，請參閱＜<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>＞。

在 .NET Core 中，不支援 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>Category

Windows 表單

#### <a name="affected-apis"></a>受影響的 API

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
