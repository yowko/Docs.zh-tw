---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217028"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a><span data-ttu-id="dc4ec-101">`Control.DefaultFont`已變更為`Segoe UI 9pt`</span><span class="sxs-lookup"><span data-stu-id="dc4ec-101">`Control.DefaultFont` changed to `Segoe UI 9pt`</span></span>

#### <a name="change-description"></a><span data-ttu-id="dc4ec-102">變更描述</span><span class="sxs-lookup"><span data-stu-id="dc4ec-102">Change description</span></span>

<span data-ttu-id="dc4ec-103">在 .NET Framework 中， <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType>屬性已設定為。 `Microsoft Sans Serif 8pt`</span><span class="sxs-lookup"><span data-stu-id="dc4ec-103">In the .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="dc4ec-104">下圖顯示使用預設字型的視窗。</span><span class="sxs-lookup"><span data-stu-id="dc4ec-104">The following figure shows a window that uses the default font.</span></span>

![.NET Framework 中的預設控制字型](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="dc4ec-106">從 .net core 3.0 開始，.net core 會將它設定為`Segoe UI 9pt` （與相同的<xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>字型）。</span><span class="sxs-lookup"><span data-stu-id="dc4ec-106">In .NET Core starting with .NET Core 3.0, it is set to `Segoe UI 9pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="dc4ec-107">由於這項變更的結果，表單和控制項將會調整大小約 27%，以因應較大的新預設字型大小。</span><span class="sxs-lookup"><span data-stu-id="dc4ec-107">As a result of this change, forms and controls will be sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="dc4ec-108">例如：</span><span class="sxs-lookup"><span data-stu-id="dc4ec-108">For example:</span></span>

![預設控制項字型-在 .NET Core 中](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="dc4ec-110">這是為了配合[WINDOWS UX 方針](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors)而進行的變更。</span><span class="sxs-lookup"><span data-stu-id="dc4ec-110">This change was made to align with [Windows UX guidelines](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dc4ec-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="dc4ec-111">Version introduced</span></span>

<span data-ttu-id="dc4ec-112">3.0</span><span class="sxs-lookup"><span data-stu-id="dc4ec-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dc4ec-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="dc4ec-113">Recommended action</span></span>

<span data-ttu-id="dc4ec-114">由於表單和控制項的大小變更，請確定您的應用程式正確呈現。</span><span class="sxs-lookup"><span data-stu-id="dc4ec-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="dc4ec-115">若要保留原始字型，請將表單的預設字型`Microsoft Sans Serif 8pt`設定為。</span><span class="sxs-lookup"><span data-stu-id="dc4ec-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="dc4ec-116">例如：</span><span class="sxs-lookup"><span data-stu-id="dc4ec-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="dc4ec-117">分類</span><span class="sxs-lookup"><span data-stu-id="dc4ec-117">Category</span></span>

- <span data-ttu-id="dc4ec-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc4ec-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dc4ec-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="dc4ec-119">Affected APIs</span></span>

<span data-ttu-id="dc4ec-120">無。</span><span class="sxs-lookup"><span data-stu-id="dc4ec-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
