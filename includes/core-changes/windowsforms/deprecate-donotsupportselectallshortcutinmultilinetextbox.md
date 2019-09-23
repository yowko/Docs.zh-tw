---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181719"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性參數

.Net `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.6.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.6.1 開始，選取<xref:System.Windows.Forms.TextBox>控制項<kbd>中的</kbd> <kbd>Ctrl</kbd>  + 鍵，並選取 [所有文字]。 在 .NET Framework 4.6 和之前的版本中，如果[ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled)和<xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType>屬性都設定為`true`，選取 [ <kbd>Ctrl</kbd>  +  <kbd>A</kbd> ] 快速鍵就無法選取所有文字。 .NET Framework `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 4.6.1 中引進了相容性參數，以保留原始的行為。 如需詳細資訊，請參閱<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>。

在 .net Core 中， `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`不支援參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>分類

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
