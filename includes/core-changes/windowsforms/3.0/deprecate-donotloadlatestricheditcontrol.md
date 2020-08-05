---
ms.openlocfilehash: e10b5168d59edd56ff549a3a1e3a09d023fe5e28
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556143"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>不支援 DoNotLoadLatestRichEditControl 相容性切換

`Switch.System.Windows.Forms.UseLegacyImages`.Net Core 或 .net 5.0 和更新版本的 Windows Forms 不支援 .NET Framework 4.7.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

在 .NET Framework 4.6.2 和舊版中，控制項會具現 <xref:System.Windows.Forms.RichTextBox> 化 Win32 RichEdit control v3.0，而針對以 .NET Framework 4.7.1 為目標的應用程式， <xref:System.Windows.Forms.RichTextBox> 控制項會在*msftedit.dll*) 中具現化 RichEdit 4.1 (。 `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`已引進相容性參數，以允許以 .NET Framework 4.7.1 和更新版本為目標的應用程式退出宣告新的 RichEdit 4.1 控制項，並改為使用舊的 RichEdit v3 控制項。

在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` 不支援參數。 只支援新版本的 <xref:System.Windows.Forms.RichTextBox> 控制項。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
