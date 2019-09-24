---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217028"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a>`Control.DefaultFont`已變更為`Segoe UI 9pt`

#### <a name="change-description"></a>變更描述

在 .NET Framework 中， <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType>屬性已設定為。 `Microsoft Sans Serif 8pt` 下圖顯示使用預設字型的視窗。

![.NET Framework 中的預設控制字型](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

從 .net core 3.0 開始，.net core 會將它設定為`Segoe UI 9pt` （與相同的<xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>字型）。 由於這項變更的結果，表單和控制項將會調整大小約 27%，以因應較大的新預設字型大小。 例如：

![預設控制項字型-在 .NET Core 中](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

這是為了配合[WINDOWS UX 方針](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors)而進行的變更。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

由於表單和控制項的大小變更，請確定您的應用程式正確呈現。

若要保留原始字型，請將表單的預設字型`Microsoft Sans Serif 8pt`設定為。 例如：

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a>分類

- Windows Forms

#### <a name="affected-apis"></a>受影響的 API

無。

<!--

### Affected APIs

- Not detectable via API analysis

-->
