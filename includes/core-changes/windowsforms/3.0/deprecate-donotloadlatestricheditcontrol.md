---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643981"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>不支援 DoNotLoadLatestRichEditControl 相容性參數

在 .NET Framework 4.7.1 中引進的 `Switch.System.Windows.Forms.UseLegacyImages` 相容性參數，在 .NET Core 3.0 的 Windows Forms 中不受支援。

#### <a name="change-description"></a>變更描述

在 .NET Framework 4.6.2 和舊版中，<xref:System.Windows.Forms.RichTextBox> 控制項會具現化 Win32 RichEdit control v3.0，而針對以 .NET Framework 4.7.1 為目標的應用程式，<xref:System.Windows.Forms.RichTextBox> 控制項將會具現化 RichEdit 4.1 （在*msftedit.dll .dll*中）。 引進了 `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` 相容性參數，以允許以 .NET Framework 4.7.1 和更新版本為目標的應用程式退出宣告新的 RichEdit 4.1 控制項，並改為使用舊的 RichEdit v3 控制項。

在 .NET Core 中，不支援 `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` 參數。 僅支援新版本的 <xref:System.Windows.Forms.RichTextBox> 控制項。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>Category

Windows 表單

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
