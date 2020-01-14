---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937074"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>預設控制字型已變更為 Segoe UI 9 pt

#### <a name="change-description"></a>變更描述

在 .NET Framework 中，<xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> 屬性已設定為 [`Microsoft Sans Serif 8 pt`]。 下圖顯示使用預設字型的視窗。

![.NET Framework 中的預設控制字型](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

從 .NET Core 3.0 開始，預設字型會設定為 `Segoe UI 9 pt` （與 <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>相同的字型）。 由於這項變更的結果，表單和控制項的大小約為27% 以上，以考慮新的預設字型大小。 例如：

![.NET Core 中的預設控制項字型](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

這是為了配合[Windows 使用者經驗（UX）指導方針](/windows/win32/uxguide/vis-fonts#fonts-and-colors)而進行的變更。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

由於表單和控制項的大小變更，請確定您的應用程式正確呈現。

若要保留原始字型，請將表單的預設字型設定為 `Microsoft Sans Serif 8 pt`。 例如：

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a>分類

- Windows 表單

#### <a name="affected-apis"></a>受影響的 API

無。

<!--

### Affected APIs

- Not detectable via API analysis

-->
