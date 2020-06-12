---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702430"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="c43ee-101">WinForms 屬性現在會擲回 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="c43ee-101">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="c43ee-102">某些 Windows Forms 屬性現在 <xref:System.ArgumentOutOfRangeException> 會針對不正確引數擲回，而先前不會對其執行。</span><span class="sxs-lookup"><span data-stu-id="c43ee-102">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c43ee-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="c43ee-103">Change description</span></span>

<span data-ttu-id="c43ee-104">先前 <xref:System.NullReferenceException> <xref:System.IndexOutOfRangeException> <xref:System.ArgumentException> 在傳遞超出範圍的引數時，這些屬性會擲回各種例外狀況，例如、或。</span><span class="sxs-lookup"><span data-stu-id="c43ee-104">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="c43ee-105">從 .NET 5.0 開始，這些屬性現在 <xref:System.ArgumentOutOfRangeException> 會在傳遞的引數超出範圍時擲回。</span><span class="sxs-lookup"><span data-stu-id="c43ee-105">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="c43ee-106">擲回會 <xref:System.ArgumentOutOfRangeException> 符合 .net 執行時間的行為。</span><span class="sxs-lookup"><span data-stu-id="c43ee-106">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="c43ee-107">它也會藉由清楚地傳達哪個引數無效，來改善偵錯工具的經驗。</span><span class="sxs-lookup"><span data-stu-id="c43ee-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c43ee-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c43ee-108">Version introduced</span></span>

<span data-ttu-id="c43ee-109">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="c43ee-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c43ee-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c43ee-110">Recommended action</span></span>

- <span data-ttu-id="c43ee-111">更新程式碼以避免傳遞不正確引數。</span><span class="sxs-lookup"><span data-stu-id="c43ee-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="c43ee-112">如有必要，請 <xref:System.ArgumentOutOfRangeException> 在設定屬性時處理。</span><span class="sxs-lookup"><span data-stu-id="c43ee-112">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

#### <a name="category"></a><span data-ttu-id="c43ee-113">類別</span><span class="sxs-lookup"><span data-stu-id="c43ee-113">Category</span></span>

<span data-ttu-id="c43ee-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c43ee-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c43ee-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c43ee-115">Affected APIs</span></span>

<span data-ttu-id="c43ee-116">下表列出受影響的屬性和參數：</span><span class="sxs-lookup"><span data-stu-id="c43ee-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="c43ee-117">屬性</span><span class="sxs-lookup"><span data-stu-id="c43ee-117">Property</span></span> | <span data-ttu-id="c43ee-118">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c43ee-118">Parameter name</span></span> | <span data-ttu-id="c43ee-119">已新增版本</span><span class="sxs-lookup"><span data-stu-id="c43ee-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="c43ee-120">5.0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="c43ee-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="c43ee-121">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="c43ee-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="c43ee-122">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="c43ee-122">5.0 Preview 6</span></span> |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
