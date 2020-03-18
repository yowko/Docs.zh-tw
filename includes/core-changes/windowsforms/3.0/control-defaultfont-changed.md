---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937074"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="7a930-101">預設控制字體更改為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="7a930-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="7a930-102">變更描述</span><span class="sxs-lookup"><span data-stu-id="7a930-102">Change description</span></span>

<span data-ttu-id="7a930-103">在 .NET 框架<xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType>中，屬性設置為`Microsoft Sans Serif 8 pt`。</span><span class="sxs-lookup"><span data-stu-id="7a930-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="7a930-104">下圖顯示了使用預設字型的視窗。</span><span class="sxs-lookup"><span data-stu-id="7a930-104">The following image shows a window that uses the default font.</span></span>

![.NET 框架中的預設控制字體](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="7a930-106">從 .NET Core 3.0 開始，預設字型`Segoe UI 9 pt`設置為（與<xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>的字體相同）。</span><span class="sxs-lookup"><span data-stu-id="7a930-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="7a930-107">由於此更改，表單和控制項的大小大約大 27%，以考慮到新預設字型的較大大小。</span><span class="sxs-lookup"><span data-stu-id="7a930-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="7a930-108">例如：</span><span class="sxs-lookup"><span data-stu-id="7a930-108">For example:</span></span>

![.NET 核心中的預設控制項字體](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="7a930-110">進行此更改是為了與[Windows 使用者體驗 （UX） 指南](/windows/win32/uxguide/vis-fonts#fonts-and-colors)保持一致。</span><span class="sxs-lookup"><span data-stu-id="7a930-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7a930-111">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="7a930-111">Version introduced</span></span>

<span data-ttu-id="7a930-112">3.0</span><span class="sxs-lookup"><span data-stu-id="7a930-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7a930-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7a930-113">Recommended action</span></span>

<span data-ttu-id="7a930-114">由於表單和控制項的大小發生變化，請確保應用程式呈現正確。</span><span class="sxs-lookup"><span data-stu-id="7a930-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="7a930-115">要保留原始字體，請將表單的預設字型設置為`Microsoft Sans Serif 8 pt`。</span><span class="sxs-lookup"><span data-stu-id="7a930-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="7a930-116">例如：</span><span class="sxs-lookup"><span data-stu-id="7a930-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="7a930-117">類別</span><span class="sxs-lookup"><span data-stu-id="7a930-117">Category</span></span>

- <span data-ttu-id="7a930-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a930-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7a930-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7a930-119">Affected APIs</span></span>

<span data-ttu-id="7a930-120">無。</span><span class="sxs-lookup"><span data-stu-id="7a930-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
