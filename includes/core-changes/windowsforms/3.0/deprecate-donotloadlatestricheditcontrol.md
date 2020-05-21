---
ms.openlocfilehash: cb8c0532bb2bcfbcd619cd382f3d236b431c3480
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721534"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>不支援 DoNotLoadLatestRichEditControl 相容性切換

`Switch.System.Windows.Forms.UseLegacyImages`.Net Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

在 .NET Framework 4.6.2 和舊版中， <xref:System.Windows.Forms.RichTextBox> 控制項會具現化 Win32 RichEdit control v3.0，而對於以 .NET Framework 4.7.1 為目標的應用程式， <xref:System.Windows.Forms.RichTextBox> 控制項會將 RichEdit 4.1 （在*msftedit.dll*中）具現化。 `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`已引進相容性參數，以允許以 .NET Framework 4.7.1 和更新版本為目標的應用程式退出宣告新的 RichEdit 4.1 控制項，並改為使用舊的 RichEdit v3 控制項。

在 .NET Core 中， `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` 不支援參數。 只支援新版本的 <xref:System.Windows.Forms.RichTextBox> 控制項。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

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
