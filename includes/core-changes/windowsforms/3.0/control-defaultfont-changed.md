---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937074"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>預設控制字體更改為 Segoe UI 9 pt

#### <a name="change-description"></a>變更描述

在 .NET 框架<xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType>中，屬性設置為`Microsoft Sans Serif 8 pt`。 下圖顯示了使用預設字型的視窗。

![.NET 框架中的預設控制字體](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

從 .NET Core 3.0 開始，預設字型`Segoe UI 9 pt`設置為（與<xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>的字體相同）。 由於此更改，表單和控制項的大小大約大 27%，以考慮到新預設字型的較大大小。 例如：

![.NET 核心中的預設控制項字體](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

進行此更改是為了與[Windows 使用者體驗 （UX） 指南](/windows/win32/uxguide/vis-fonts#fonts-and-colors)保持一致。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

由於表單和控制項的大小發生變化，請確保應用程式呈現正確。

要保留原始字體，請將表單的預設字型設置為`Microsoft Sans Serif 8 pt`。 例如：

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

### Affected APIs

- Not detectable via API analysis

-->
