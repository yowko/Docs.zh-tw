---
title: 重大變更： WinForms 方法現在會擲回 ArgumentException
description: 瞭解 .NET 5.0 中的重大變更，其中某些 Windows Forms 方法現在會針對不正確引數擲回 ArgumentException。
ms.date: 07/18/2020
ms.openlocfilehash: 892f4d16b80f3e42187480a7fcfb24e81868d07c
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570212"
---
# <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="75c96-103">WinForms 方法現在會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="75c96-103">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="75c96-104">某些 Windows Forms 方法現在會 <xref:System.ArgumentException> 針對不正確引數擲回，但先前未提供這些引數。</span><span class="sxs-lookup"><span data-stu-id="75c96-104">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="75c96-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="75c96-105">Change description</span></span>

<span data-ttu-id="75c96-106">先前，將非預期或不正確類型的引數傳遞至特定的 Windows Forms 方法會導致不定的狀態。</span><span class="sxs-lookup"><span data-stu-id="75c96-106">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="75c96-107">從 .NET 5.0 開始，這些方法現在會 <xref:System.ArgumentException> 在傳遞無效引數時擲回。</span><span class="sxs-lookup"><span data-stu-id="75c96-107">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="75c96-108">擲回會 <xref:System.ArgumentException> 符合 .net 執行時間的行為。</span><span class="sxs-lookup"><span data-stu-id="75c96-108">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="75c96-109">它也可清楚地傳達不正確引數，以改善偵錯工具的體驗。</span><span class="sxs-lookup"><span data-stu-id="75c96-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="75c96-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="75c96-110">Version introduced</span></span>

<span data-ttu-id="75c96-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="75c96-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="75c96-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="75c96-112">Recommended action</span></span>

- <span data-ttu-id="75c96-113">更新程式碼以防止傳遞不正確引數。</span><span class="sxs-lookup"><span data-stu-id="75c96-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="75c96-114">如有必要，請 <xref:System.ArgumentException> 在呼叫方法時處理。</span><span class="sxs-lookup"><span data-stu-id="75c96-114">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="75c96-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="75c96-115">Affected APIs</span></span>

<span data-ttu-id="75c96-116">下表列出受影響的方法和參數：</span><span class="sxs-lookup"><span data-stu-id="75c96-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="75c96-117">方法</span><span class="sxs-lookup"><span data-stu-id="75c96-117">Method</span></span> | <span data-ttu-id="75c96-118">參數名稱</span><span class="sxs-lookup"><span data-stu-id="75c96-118">Parameter name</span></span> | <span data-ttu-id="75c96-119">條件</span><span class="sxs-lookup"><span data-stu-id="75c96-119">Condition</span></span> | <span data-ttu-id="75c96-120">已新增版本</span><span class="sxs-lookup"><span data-stu-id="75c96-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="75c96-121">引數的類型不是 <xref:System.Windows.Forms.TabPage> 。</span><span class="sxs-lookup"><span data-stu-id="75c96-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="75c96-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="75c96-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="75c96-123">引數是 `null` 、 <xref:System.String.Empty?displayProperty=nameWithType> 或空白字元。</span><span class="sxs-lookup"><span data-stu-id="75c96-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="75c96-124">Preview 5</span><span class="sxs-lookup"><span data-stu-id="75c96-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="75c96-125">無法取得 `InputLanguage` 指定文化特性的。</span><span class="sxs-lookup"><span data-stu-id="75c96-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="75c96-126">Preview 7</span><span class="sxs-lookup"><span data-stu-id="75c96-126">Preview 7</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

### Category

Windows Forms

-->
