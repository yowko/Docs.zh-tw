---
ms.openlocfilehash: b6cb7c4b479551ff4563998f310ff518d935f48a
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656329"
---
### <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a><span data-ttu-id="059bc-101">DataGridView 相關的 Api 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="059bc-101">DataGridView-related APIs now throw InvalidOperationException</span></span>

<span data-ttu-id="059bc-102"><xref:System.Windows.Forms.DataGridView> <xref:System.InvalidOperationException> 如果物件的 <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> 值為，則與現在相關的某些 api 會擲回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="059bc-102">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="059bc-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="059bc-103">Change description</span></span>

<span data-ttu-id="059bc-104">在舊版的 .NET 版本中，受影響的 Api 會在叫用時擲回， <xref:System.NullReferenceException> 而 <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> 值為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="059bc-104">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null`.</span></span> <span data-ttu-id="059bc-105">從 .NET 5.0 開始， <xref:System.InvalidOperationException> <xref:System.NullReferenceException> 如果值是在叫用時，這些 api 會擲回，而不是 <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> `null` 。</span><span class="sxs-lookup"><span data-stu-id="059bc-105">Starting in .NET 5.0, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null` when they are invoked.</span></span>

<span data-ttu-id="059bc-106">擲回會 <xref:System.InvalidOperationException> 符合 .net 執行時間的行為。</span><span class="sxs-lookup"><span data-stu-id="059bc-106">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="059bc-107">它也可以明確地傳達不正確屬性，藉此改善偵錯工具的體驗。</span><span class="sxs-lookup"><span data-stu-id="059bc-107">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="059bc-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="059bc-108">Version introduced</span></span>

<span data-ttu-id="059bc-109">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="059bc-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="059bc-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="059bc-110">Recommended action</span></span>

<span data-ttu-id="059bc-111">請檢查您的程式碼，並視需要更新它，以防止以屬性為的方式來建立受影響的類型 <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> `null` 。</span><span class="sxs-lookup"><span data-stu-id="059bc-111">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

#### <a name="category"></a><span data-ttu-id="059bc-112">類別</span><span class="sxs-lookup"><span data-stu-id="059bc-112">Category</span></span>

<span data-ttu-id="059bc-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="059bc-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="059bc-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="059bc-114">Affected APIs</span></span>

<span data-ttu-id="059bc-115">下表列出受影響的屬性和參數：</span><span class="sxs-lookup"><span data-stu-id="059bc-115">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="059bc-116">受影響的方法或屬性</span><span class="sxs-lookup"><span data-stu-id="059bc-116">Affected method or property</span></span> | <span data-ttu-id="059bc-117">驗證的屬性</span><span class="sxs-lookup"><span data-stu-id="059bc-117">Validated property</span></span> | <span data-ttu-id="059bc-118">已新增版本</span><span class="sxs-lookup"><span data-stu-id="059bc-118">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-119">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-119">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-120">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-120">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-121">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-121">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-122">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-122">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-123">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-123">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-124">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-124">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-125">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-125">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-126">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-126">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-127">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-127">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-128">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-128">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-129">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-129">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="059bc-130">5.0</span><span class="sxs-lookup"><span data-stu-id="059bc-130">5.0</span></span> |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State`
- `M:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `M:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction`

-->
