---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643960"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>資料夾瀏覽器對話的現代化

在<xref:System.Windows.Forms.FolderBrowserDialog>.NET Core 的 Windows 表單應用程式中，該控制項已更改。

#### <a name="change-description"></a>變更描述

在 .NET 框架中，Windows 表單對<xref:System.Windows.Forms.FolderBrowserDialog>控制項使用以下對話方塊：

![.NET 框架中的資料夾瀏覽器對話控制](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

在 .NET Core 3.0 中，Windows 表單使用者引入了 Windows Vista 中引入的基於 COM 的較新的控制項：

![.NET 內核中的資料夾瀏覽器對話控制](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

對話方塊將自動升級。

如果要保留原始對話方塊，請先<xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType>將屬性設置為，`false`然後顯示對話方塊，如下代碼片段所示：

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
