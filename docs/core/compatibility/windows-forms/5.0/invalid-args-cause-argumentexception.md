---
title: 重大變更： WinForms 方法現在會擲回 ArgumentException
description: 瞭解 .NET 5.0 中的重大變更，其中 sWindows 的表單方法現在會擲回無效引數的 ArgumentException。
ms.date: 07/18/2020
ms.openlocfilehash: 46fe3f3b1208a5cd676e1b7546507bed36a850f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760800"
---
# <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="beccc-103">WinForms 方法現在會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="beccc-103">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="beccc-104">某些 Windows Forms 方法現在會 <xref:System.ArgumentException> 針對不正確引數擲回，但先前未提供這些引數。</span><span class="sxs-lookup"><span data-stu-id="beccc-104">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="beccc-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="beccc-105">Change description</span></span>

<span data-ttu-id="beccc-106">先前，將非預期或不正確類型的引數傳遞至特定的 Windows Forms 方法會導致不定的狀態。</span><span class="sxs-lookup"><span data-stu-id="beccc-106">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="beccc-107">從 .NET 5.0 開始，這些方法現在會 <xref:System.ArgumentException> 在傳遞無效引數時擲回。</span><span class="sxs-lookup"><span data-stu-id="beccc-107">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="beccc-108">擲回會 <xref:System.ArgumentException> 符合 .net 執行時間的行為。</span><span class="sxs-lookup"><span data-stu-id="beccc-108">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="beccc-109">它也可清楚地傳達不正確引數，以改善偵錯工具的體驗。</span><span class="sxs-lookup"><span data-stu-id="beccc-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="beccc-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="beccc-110">Version introduced</span></span>

<span data-ttu-id="beccc-111">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="beccc-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="beccc-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="beccc-112">Recommended action</span></span>

- <span data-ttu-id="beccc-113">更新程式碼以防止傳遞不正確引數。</span><span class="sxs-lookup"><span data-stu-id="beccc-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="beccc-114">如有必要，請 <xref:System.ArgumentException> 在呼叫方法時處理。</span><span class="sxs-lookup"><span data-stu-id="beccc-114">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="beccc-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="beccc-115">Affected APIs</span></span>

<span data-ttu-id="beccc-116">下表列出受影響的方法和參數：</span><span class="sxs-lookup"><span data-stu-id="beccc-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="beccc-117">方法</span><span class="sxs-lookup"><span data-stu-id="beccc-117">Method</span></span> | <span data-ttu-id="beccc-118">參數名稱</span><span class="sxs-lookup"><span data-stu-id="beccc-118">Parameter name</span></span> | <span data-ttu-id="beccc-119">條件</span><span class="sxs-lookup"><span data-stu-id="beccc-119">Condition</span></span> | <span data-ttu-id="beccc-120">已新增版本</span><span class="sxs-lookup"><span data-stu-id="beccc-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="beccc-121">引數的類型不是 <xref:System.Windows.Forms.TabPage> 。</span><span class="sxs-lookup"><span data-stu-id="beccc-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="beccc-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="beccc-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="beccc-123">引數是 `null` 、 <xref:System.String.Empty?displayProperty=nameWithType> 或空白字元。</span><span class="sxs-lookup"><span data-stu-id="beccc-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="beccc-124">Preview 5</span><span class="sxs-lookup"><span data-stu-id="beccc-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="beccc-125">無法取得 `InputLanguage` 指定文化特性的。</span><span class="sxs-lookup"><span data-stu-id="beccc-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="beccc-126">Preview 7</span><span class="sxs-lookup"><span data-stu-id="beccc-126">Preview 7</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

### Category

Windows Forms

-->
