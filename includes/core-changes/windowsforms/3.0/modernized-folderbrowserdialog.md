---
ms.openlocfilehash: 27c6353f8f71254a505b434921f4b1e61e64cdda
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2021
ms.locfileid: "98758160"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>FolderBrowserDialog 的現代化

<xref:System.Windows.Forms.FolderBrowserDialog>控制項已在 .Net Core 的 Windows Forms 應用程式中變更。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中，Windows forms 會針對控制項使用下列對話方塊 <xref:System.Windows.Forms.FolderBrowserDialog> ：

![.NET Framework 中的 FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

在 .NET Core 3.0 中，Windows Forms 會使用 Windows Vista 中引進的較新 COM 控制項：

![.NET Core 中的 FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

對話方塊將會自動升級。

如果您想要保留原始的對話，請在 <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> 顯示對話方塊之前將屬性設定為， `false` 如下列程式碼片段所示：

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

#### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
