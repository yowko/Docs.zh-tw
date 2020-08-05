---
ms.openlocfilehash: 3fb8807a9b6f0bb0d2bc746f5e89eaa8a81d6aa8
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556148"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性切換

`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.Net Core 和 .net 5.0 和更新版本的 Windows Forms 不支援 .NET Framework 4.6.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.6.1 開始，選取控制項中的<kbd>Ctrl</kbd>  +  <kbd>A</kbd>鍵，並 <xref:System.Windows.Forms.TextBox> 選取 [所有文字]。 在 .NET Framework 4.6 和之前的版本中， <kbd>Ctrl</kbd>  +  <kbd>A</kbd>如果[ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled)和 <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> 屬性都設定為，選取 [Ctrl A] 快速鍵就無法選取所有文字 `true` 。 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.NET Framework 4.6.1 中引進了相容性參數，以保留原始的行為。 如需相關資訊，請參閱<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>。

在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 不支援參數。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- 無

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
