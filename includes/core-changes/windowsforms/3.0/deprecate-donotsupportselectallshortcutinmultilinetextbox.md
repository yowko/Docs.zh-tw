---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937113"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>不支援選擇全選件多行文本盒相容性開關

.NET 框架 4.6.1 中引入的`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。

#### <a name="change-description"></a>變更描述

從 .NET 框架 4.6.1 開始，<xref:System.Windows.Forms.TextBox>在控制項中選擇<kbd>Ctrl</kbd> + <kbd>A</kbd>快速鍵選擇了所有文本。 在 .NET 框架 4.6 和早期版本中，如果[Textbox.快捷方式啟用](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled)<xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType>和屬性都`true`設置為 ，則選擇<kbd>Ctrl</kbd> + <kbd>快捷</kbd>鍵無法選擇所有文本。 在`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.NET 框架 4.6.1 中引入了相容性開關，以保留原始行為。 如需相關資訊，請參閱<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>。

在 .NET 內核`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`中，不支援交換器。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 9

#### <a name="recommended-action"></a>建議的動作

卸下開關。 不支援該開關，並且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
