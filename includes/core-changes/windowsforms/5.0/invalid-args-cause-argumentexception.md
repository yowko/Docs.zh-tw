---
ms.openlocfilehash: 5212c5d9513a8ef5f51693857d0ddb60db4e49b9
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158386"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="341b7-101">WinForms 方法現在會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="341b7-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="341b7-102">有些 Windows Forms 方法現在會<xref:System.ArgumentException>針對不正確引數擲回，而先前並未提供。</span><span class="sxs-lookup"><span data-stu-id="341b7-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="341b7-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="341b7-103">Change description</span></span>

<span data-ttu-id="341b7-104">先前，將非預期或不正確類型的引數傳遞至特定 Windows Forms 方法會導致不定狀態。</span><span class="sxs-lookup"><span data-stu-id="341b7-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="341b7-105">從 .NET 5.0 開始，這些方法現在會在<xref:System.ArgumentException>傳遞的無效引數時擲回。</span><span class="sxs-lookup"><span data-stu-id="341b7-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="341b7-106">擲回<xref:System.ArgumentException>會符合 .net 執行時間的行為。</span><span class="sxs-lookup"><span data-stu-id="341b7-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="341b7-107">它也會藉由清楚地傳達哪個引數無效，來改善偵錯工具的經驗。</span><span class="sxs-lookup"><span data-stu-id="341b7-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="341b7-108">下表列出受影響的方法和參數：</span><span class="sxs-lookup"><span data-stu-id="341b7-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="341b7-109">方法</span><span class="sxs-lookup"><span data-stu-id="341b7-109">Method</span></span> | <span data-ttu-id="341b7-110">參數名稱</span><span class="sxs-lookup"><span data-stu-id="341b7-110">Parameter name</span></span> | <span data-ttu-id="341b7-111">狀況</span><span class="sxs-lookup"><span data-stu-id="341b7-111">Condition</span></span> | <span data-ttu-id="341b7-112">已新增版本</span><span class="sxs-lookup"><span data-stu-id="341b7-112">Version added</span></span> |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="341b7-113">引數的類型<xref:System.Windows.Forms.TabPage>不是。</span><span class="sxs-lookup"><span data-stu-id="341b7-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="341b7-114">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="341b7-114">5.0 Preview 1</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="341b7-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="341b7-115">Version introduced</span></span>

<span data-ttu-id="341b7-116">.NET 5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="341b7-116">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="341b7-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="341b7-117">Recommended action</span></span>

- <span data-ttu-id="341b7-118">更新程式碼以避免傳遞不正確引數。</span><span class="sxs-lookup"><span data-stu-id="341b7-118">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="341b7-119">如有必要，請<xref:System.ArgumentException>在呼叫方法時處理。</span><span class="sxs-lookup"><span data-stu-id="341b7-119">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="341b7-120">類別</span><span class="sxs-lookup"><span data-stu-id="341b7-120">Category</span></span>

<span data-ttu-id="341b7-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="341b7-121">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="341b7-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="341b7-122">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
