---
ms.openlocfilehash: 645df8080abd21e4db95903a301a36b79a698858
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888103"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="8ecec-101">資料夾瀏覽器對話的現代化</span><span class="sxs-lookup"><span data-stu-id="8ecec-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="8ecec-102">在<xref:System.Windows.Forms.FolderBrowserDialog>.NET Core 的 Windows 表單應用程式中,該控制項已更改。</span><span class="sxs-lookup"><span data-stu-id="8ecec-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8ecec-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="8ecec-103">Change description</span></span>

<span data-ttu-id="8ecec-104">在 .NET 框架中,Windows<xref:System.Windows.Forms.FolderBrowserDialog>表單對控制項使用以下對話框:</span><span class="sxs-lookup"><span data-stu-id="8ecec-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![.NET 框架中的資料夾瀏覽器對話控制](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="8ecec-106">在 .NET Core 3.0 中,Windows 窗體使用者引入了 Windows Vista 中引入的基於 COM 的較新的控制件:</span><span class="sxs-lookup"><span data-stu-id="8ecec-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![.NET 內核中的資料夾瀏覽器對話控制](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="8ecec-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8ecec-108">Version introduced</span></span>

<span data-ttu-id="8ecec-109">3.0</span><span class="sxs-lookup"><span data-stu-id="8ecec-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8ecec-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="8ecec-110">Recommended action</span></span>

<span data-ttu-id="8ecec-111">對話框將自動升級。</span><span class="sxs-lookup"><span data-stu-id="8ecec-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="8ecec-112">如果要保留原始對話框,請先<xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType>將屬性設定為`false`, 然後顯示對話框,如下代碼片段所示:</span><span class="sxs-lookup"><span data-stu-id="8ecec-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="8ecec-113">類別</span><span class="sxs-lookup"><span data-stu-id="8ecec-113">Category</span></span>

<span data-ttu-id="8ecec-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ecec-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8ecec-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8ecec-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
