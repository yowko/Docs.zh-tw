---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937074"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="ccf4d-101">預設控制字型已變更為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="ccf4d-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="ccf4d-102">變更描述</span><span class="sxs-lookup"><span data-stu-id="ccf4d-102">Change description</span></span>

<span data-ttu-id="ccf4d-103">在 .NET Framework 中，<xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> 屬性已設定為 [`Microsoft Sans Serif 8 pt`]。</span><span class="sxs-lookup"><span data-stu-id="ccf4d-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="ccf4d-104">下圖顯示使用預設字型的視窗。</span><span class="sxs-lookup"><span data-stu-id="ccf4d-104">The following image shows a window that uses the default font.</span></span>

![.NET Framework 中的預設控制字型](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="ccf4d-106">從 .NET Core 3.0 開始，預設字型會設定為 `Segoe UI 9 pt` （與 <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>相同的字型）。</span><span class="sxs-lookup"><span data-stu-id="ccf4d-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="ccf4d-107">由於這項變更的結果，表單和控制項的大小約為27% 以上，以考慮新的預設字型大小。</span><span class="sxs-lookup"><span data-stu-id="ccf4d-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="ccf4d-108">例如：</span><span class="sxs-lookup"><span data-stu-id="ccf4d-108">For example:</span></span>

![.NET Core 中的預設控制項字型](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="ccf4d-110">這是為了配合[Windows 使用者經驗（UX）指導方針](/windows/win32/uxguide/vis-fonts#fonts-and-colors)而進行的變更。</span><span class="sxs-lookup"><span data-stu-id="ccf4d-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ccf4d-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ccf4d-111">Version introduced</span></span>

<span data-ttu-id="ccf4d-112">3.0</span><span class="sxs-lookup"><span data-stu-id="ccf4d-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ccf4d-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ccf4d-113">Recommended action</span></span>

<span data-ttu-id="ccf4d-114">由於表單和控制項的大小變更，請確定您的應用程式正確呈現。</span><span class="sxs-lookup"><span data-stu-id="ccf4d-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="ccf4d-115">若要保留原始字型，請將表單的預設字型設定為 `Microsoft Sans Serif 8 pt`。</span><span class="sxs-lookup"><span data-stu-id="ccf4d-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="ccf4d-116">例如：</span><span class="sxs-lookup"><span data-stu-id="ccf4d-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="ccf4d-117">分類</span><span class="sxs-lookup"><span data-stu-id="ccf4d-117">Category</span></span>

- <span data-ttu-id="ccf4d-118">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="ccf4d-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ccf4d-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ccf4d-119">Affected APIs</span></span>

<span data-ttu-id="ccf4d-120">無。</span><span class="sxs-lookup"><span data-stu-id="ccf4d-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
