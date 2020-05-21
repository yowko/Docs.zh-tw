---
ms.openlocfilehash: 0b2d3c1383246d4259c6d906ecf9dab927f4bdb1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721703"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>預設控制字型已變更為 Segoe UI 9 pt

#### <a name="change-description"></a>變更描述

在 .NET Framework 中， <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> 屬性已設定為 `Microsoft Sans Serif 8 pt` 。 下圖顯示使用預設字型的視窗。

![.NET Framework 中的預設控制字型](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

從 .NET Core 3.0 開始，預設字型會設定為 `Segoe UI 9 pt` （與相同的字型 <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType> ）。 由於這項變更的結果，表單和控制項的大小約為27% 以上，以考慮新的預設字型大小。 例如：

![.NET Core 中的預設控制項字型](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

這是為了配合[Windows 使用者經驗（UX）指導方針](/windows/win32/uxguide/vis-fonts#fonts-and-colors)而進行的變更。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

由於表單和控制項的大小變更，請確定您的應用程式正確呈現。

若要保留原始字型，請將表單的預設字型設定為 `Microsoft Sans Serif 8 pt` 。 例如：

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a>類別

- Windows Forms

#### <a name="affected-apis"></a>受影響的 API

無。

<!--

#### Affected APIs

- Not detectable via API analysis

-->
