---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643960"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="d757e-101">資料夾瀏覽器對話的現代化</span><span class="sxs-lookup"><span data-stu-id="d757e-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="d757e-102">在<xref:System.Windows.Forms.FolderBrowserDialog>.NET Core 的 Windows 表單應用程式中，該控制項已更改。</span><span class="sxs-lookup"><span data-stu-id="d757e-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d757e-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="d757e-103">Change description</span></span>

<span data-ttu-id="d757e-104">在 .NET 框架中，Windows 表單對<xref:System.Windows.Forms.FolderBrowserDialog>控制項使用以下對話方塊：</span><span class="sxs-lookup"><span data-stu-id="d757e-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![.NET 框架中的資料夾瀏覽器對話控制](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="d757e-106">在 .NET Core 3.0 中，Windows 表單使用者引入了 Windows Vista 中引入的基於 COM 的較新的控制項：</span><span class="sxs-lookup"><span data-stu-id="d757e-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![.NET 內核中的資料夾瀏覽器對話控制](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="d757e-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="d757e-108">Version introduced</span></span>

<span data-ttu-id="d757e-109">3.0</span><span class="sxs-lookup"><span data-stu-id="d757e-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d757e-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d757e-110">Recommended action</span></span>

<span data-ttu-id="d757e-111">對話方塊將自動升級。</span><span class="sxs-lookup"><span data-stu-id="d757e-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="d757e-112">如果要保留原始對話方塊，請先<xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType>將屬性設置為，`false`然後顯示對話方塊，如下代碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="d757e-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="d757e-113">類別</span><span class="sxs-lookup"><span data-stu-id="d757e-113">Category</span></span>

<span data-ttu-id="d757e-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d757e-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d757e-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d757e-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
