---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937092"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>不支援不載入最新裡奇編輯控制相容性開關

.NET 框架 4.7.1 中引入的`Switch.System.Windows.Forms.UseLegacyImages`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。

#### <a name="change-description"></a>變更描述

在 .NET 框架 4.6.2 和早期<xref:System.Windows.Forms.RichTextBox>版本中，該控制項將具現化 Win32 RichEdit 控制項 v3.0，對於目標 .NET Framework 4.7.1 的應用程式，<xref:System.Windows.Forms.RichTextBox>該控制項將具現化 RichEdit v4.1（在*msftedit.dll*中）。 引入`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`相容性開關是為了允許目標 .NET Framework 4.7.1 和更高版本的應用程式退出宣告新的 RichEdit v4.1 控制項，轉而使用舊的 RichEdit v3 控制項。

在 .NET 內核`Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`中，不支援交換器。 僅支援<xref:System.Windows.Forms.RichTextBox>控制項的新版本。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 9

#### <a name="recommended-action"></a>建議的動作

卸下開關。 不支援該開關，並且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
