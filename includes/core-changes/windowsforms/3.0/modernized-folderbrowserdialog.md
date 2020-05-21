---
ms.openlocfilehash: 11c04441dcec260f0bfb90f6ed2b919b1545b382
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720903"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>FolderBrowserDialog 的現代化

<xref:System.Windows.Forms.FolderBrowserDialog>控制項已在適用于 .Net Core 的 Windows Forms 應用程式中變更。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中，Windows forms 會針對控制項使用下列對話方塊 <xref:System.Windows.Forms.FolderBrowserDialog> ：

![.NET Framework 中的 FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

在 .NET Core 3.0 中，Windows Forms 使用者會在 Windows Vista 中引進較新的以 COM 為基礎的控制項：

![.NET Core 中的 FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

對話方塊將會自動升級。

如果您想要保留原始的對話方塊，請在 <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> 顯示對話方塊之前將屬性設定為， `false` 如下列程式碼片段所示：

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
