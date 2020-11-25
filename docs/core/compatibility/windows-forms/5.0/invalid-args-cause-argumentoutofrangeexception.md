---
title: 重大變更： WinForms 屬性現在會擲回 ArgumentOutOfRangeException
description: 瞭解 .NET 5.0 中的重大變更，其中某些 Windows Forms 屬性現在會針對不正確引數擲回 ArgumentOutOfRangeException。
ms.date: 06/18/2020
ms.openlocfilehash: 94593047d16304ce401b23993ad4ca173c10812b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760735"
---
# <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="e0bdc-103">WinForms 屬性現在會擲回 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="e0bdc-103">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="e0bdc-104">某些 Windows Forms 屬性現在會 <xref:System.ArgumentOutOfRangeException> 針對不正確引數擲回，但先前未提供這些引數。</span><span class="sxs-lookup"><span data-stu-id="e0bdc-104">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="e0bdc-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="e0bdc-105">Change description</span></span>

<span data-ttu-id="e0bdc-106">先前，這些屬性 <xref:System.NullReferenceException> <xref:System.IndexOutOfRangeException> <xref:System.ArgumentException> 在傳遞超出範圍的引數時，會擲回不同的例外狀況，例如、或。</span><span class="sxs-lookup"><span data-stu-id="e0bdc-106">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="e0bdc-107">從 .NET 5.0 開始，這些屬性現在 <xref:System.ArgumentOutOfRangeException> 會在傳遞的引數超出範圍時擲回。</span><span class="sxs-lookup"><span data-stu-id="e0bdc-107">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="e0bdc-108">擲回會 <xref:System.ArgumentOutOfRangeException> 符合 .net 執行時間的行為。</span><span class="sxs-lookup"><span data-stu-id="e0bdc-108">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="e0bdc-109">它也可清楚地傳達不正確引數，以改善偵錯工具的體驗。</span><span class="sxs-lookup"><span data-stu-id="e0bdc-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e0bdc-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e0bdc-110">Version introduced</span></span>

<span data-ttu-id="e0bdc-111">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="e0bdc-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e0bdc-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e0bdc-112">Recommended action</span></span>

- <span data-ttu-id="e0bdc-113">更新程式碼以防止傳遞不正確引數。</span><span class="sxs-lookup"><span data-stu-id="e0bdc-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="e0bdc-114">如有必要，請 <xref:System.ArgumentOutOfRangeException> 在設定屬性時處理。</span><span class="sxs-lookup"><span data-stu-id="e0bdc-114">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e0bdc-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e0bdc-115">Affected APIs</span></span>

<span data-ttu-id="e0bdc-116">下表列出受影響的屬性和參數：</span><span class="sxs-lookup"><span data-stu-id="e0bdc-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="e0bdc-117">屬性</span><span class="sxs-lookup"><span data-stu-id="e0bdc-117">Property</span></span> | <span data-ttu-id="e0bdc-118">參數名稱</span><span class="sxs-lookup"><span data-stu-id="e0bdc-118">Parameter name</span></span> | <span data-ttu-id="e0bdc-119">已新增版本</span><span class="sxs-lookup"><span data-stu-id="e0bdc-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="e0bdc-120">5.0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="e0bdc-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="e0bdc-121">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="e0bdc-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="e0bdc-122">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="e0bdc-122">5.0 Preview 6</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

### Category

Windows Forms

-->
