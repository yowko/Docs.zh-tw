---
ms.openlocfilehash: 11c04441dcec260f0bfb90f6ed2b919b1545b382
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720903"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="c4513-101">FolderBrowserDialog 的現代化</span><span class="sxs-lookup"><span data-stu-id="c4513-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="c4513-102"><xref:System.Windows.Forms.FolderBrowserDialog>控制項已在適用于 .Net Core 的 Windows Forms 應用程式中變更。</span><span class="sxs-lookup"><span data-stu-id="c4513-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c4513-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="c4513-103">Change description</span></span>

<span data-ttu-id="c4513-104">在 .NET Framework 中，Windows forms 會針對控制項使用下列對話方塊 <xref:System.Windows.Forms.FolderBrowserDialog> ：</span><span class="sxs-lookup"><span data-stu-id="c4513-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![.NET Framework 中的 FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="c4513-106">在 .NET Core 3.0 中，Windows Forms 使用者會在 Windows Vista 中引進較新的以 COM 為基礎的控制項：</span><span class="sxs-lookup"><span data-stu-id="c4513-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![.NET Core 中的 FolderBrowserDialogControl](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="c4513-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c4513-108">Version introduced</span></span>

<span data-ttu-id="c4513-109">3.0</span><span class="sxs-lookup"><span data-stu-id="c4513-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c4513-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c4513-110">Recommended action</span></span>

<span data-ttu-id="c4513-111">對話方塊將會自動升級。</span><span class="sxs-lookup"><span data-stu-id="c4513-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="c4513-112">如果您想要保留原始的對話方塊，請在 <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> 顯示對話方塊之前將屬性設定為， `false` 如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="c4513-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="c4513-113">類別</span><span class="sxs-lookup"><span data-stu-id="c4513-113">Category</span></span>

<span data-ttu-id="c4513-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c4513-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c4513-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c4513-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

#### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
