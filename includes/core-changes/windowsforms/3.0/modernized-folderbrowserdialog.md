---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643960"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>FolderBrowserDialog 的現代化

.NET Core Windows Forms 應用程式中的 <xref:System.Windows.Forms.FolderBrowserDialog> 控制項已變更。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中，Windows forms 會針對 <xref:System.Windows.Forms.FolderBrowserDialog> 控制項使用下列對話方塊：

![.NET Framework 中的 FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

在 .NET Core 3.0 中，Windows Forms 使用者會在 Windows Vista 中引進較新的以 COM 為基礎的控制項：

![.NET Core 中的 FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

對話方塊將會自動升級。

如果您想要保留原始的對話方塊，請在顯示對話方塊之前，將 <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> 屬性設為 `false`，如下列程式碼片段所示：

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a>Category

Windows 表單

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
