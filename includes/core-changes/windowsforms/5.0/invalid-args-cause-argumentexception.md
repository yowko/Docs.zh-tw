---
ms.openlocfilehash: f1fc70075ef09a4f036c69788342c07ee51d72ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702452"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="64ad4-101">WinForms 方法現在會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="64ad4-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="64ad4-102">有些 Windows Forms 方法現在 <xref:System.ArgumentException> 會針對不正確引數擲回，而先前並未提供。</span><span class="sxs-lookup"><span data-stu-id="64ad4-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="64ad4-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="64ad4-103">Change description</span></span>

<span data-ttu-id="64ad4-104">先前，將非預期或不正確類型的引數傳遞至特定 Windows Forms 方法會導致不定狀態。</span><span class="sxs-lookup"><span data-stu-id="64ad4-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="64ad4-105">從 .NET 5.0 開始，這些方法現在會 <xref:System.ArgumentException> 在傳遞的無效引數時擲回。</span><span class="sxs-lookup"><span data-stu-id="64ad4-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="64ad4-106">擲回會 <xref:System.ArgumentException> 符合 .net 執行時間的行為。</span><span class="sxs-lookup"><span data-stu-id="64ad4-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="64ad4-107">它也會藉由清楚地傳達哪個引數無效，來改善偵錯工具的經驗。</span><span class="sxs-lookup"><span data-stu-id="64ad4-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="64ad4-108">下表列出受影響的方法和參數：</span><span class="sxs-lookup"><span data-stu-id="64ad4-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="64ad4-109">方法</span><span class="sxs-lookup"><span data-stu-id="64ad4-109">Method</span></span> | <span data-ttu-id="64ad4-110">參數名稱</span><span class="sxs-lookup"><span data-stu-id="64ad4-110">Parameter name</span></span> | <span data-ttu-id="64ad4-111">狀況</span><span class="sxs-lookup"><span data-stu-id="64ad4-111">Condition</span></span> | <span data-ttu-id="64ad4-112">已新增版本</span><span class="sxs-lookup"><span data-stu-id="64ad4-112">Version added</span></span> |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="64ad4-113">引數的類型不是 <xref:System.Windows.Forms.TabPage> 。</span><span class="sxs-lookup"><span data-stu-id="64ad4-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="64ad4-114">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="64ad4-114">5.0 Preview 1</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="64ad4-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="64ad4-115">Version introduced</span></span>

<span data-ttu-id="64ad4-116">.NET 5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="64ad4-116">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="64ad4-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="64ad4-117">Recommended action</span></span>

- <span data-ttu-id="64ad4-118">更新程式碼以避免傳遞不正確引數。</span><span class="sxs-lookup"><span data-stu-id="64ad4-118">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="64ad4-119">如有必要，請 <xref:System.ArgumentException> 在呼叫方法時處理。</span><span class="sxs-lookup"><span data-stu-id="64ad4-119">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="64ad4-120">類別</span><span class="sxs-lookup"><span data-stu-id="64ad4-120">Category</span></span>

<span data-ttu-id="64ad4-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64ad4-121">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="64ad4-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="64ad4-122">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
