---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181706"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>不支援 DoNotLoadLatestRichEditControl 相容性參數

.Net `Switch.System.Windows.Forms.UseLegacyImages` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

在 .NET Framework 4.6.2 和舊版中， <xref:System.Windows.Forms.RichTextBox>控制項會具現化 Win32 RichEdit control v3.0，而對於以 .NET Framework 4.7.1 為目標的應用程式<xref:System.Windows.Forms.RichTextBox> ，控制項會具現化 RichEdit 4.1 （在*msftedit.dll*）。 已`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`引進相容性參數，以允許以 .NET Framework 4.7.1 和更新版本為目標的應用程式退出宣告新的 RichEdit 4.1 控制項，並改為使用舊的 RichEdit v3 控制項。

在 .net Core 中， `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`不支援參數。 只支援新版本的<xref:System.Windows.Forms.RichTextBox>控制項。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>分類

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
