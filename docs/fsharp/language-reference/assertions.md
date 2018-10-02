---
title: 判斷提示 (F#)
description: "了解如何使用 '判斷提示' 運算式做為偵錯功能在 F # 程式設計語言中測試運算式。"
ms.date: 05/16/2016
ms.openlocfilehash: 85b1e839bfd19bada48b7f1821d15ddd8fa77754
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48034306"
---
# <a name="assertions"></a><span data-ttu-id="b84fd-103">判斷提示</span><span class="sxs-lookup"><span data-stu-id="b84fd-103">Assertions</span></span>

<span data-ttu-id="b84fd-104">`assert`運算式是偵錯功能，您可以使用它來測試運算式。</span><span class="sxs-lookup"><span data-stu-id="b84fd-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="b84fd-105">當運算式在偵測模式中發生錯誤時，判斷提示會顯示系統錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b84fd-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="b84fd-106">語法</span><span class="sxs-lookup"><span data-stu-id="b84fd-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="b84fd-107">備註</span><span class="sxs-lookup"><span data-stu-id="b84fd-107">Remarks</span></span>

<span data-ttu-id="b84fd-108">`assert`運算式具有類型`bool -> unit`。</span><span class="sxs-lookup"><span data-stu-id="b84fd-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="b84fd-109">在先前的語法*條件*表示要測試的布林運算式。</span><span class="sxs-lookup"><span data-stu-id="b84fd-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="b84fd-110">如果運算式評估為`true`，執行會持續不受影響。</span><span class="sxs-lookup"><span data-stu-id="b84fd-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="b84fd-111">如果評估為`false`，就會產生系統錯誤 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b84fd-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="b84fd-112">[錯誤] 對話方塊中已包含字串的標題**判斷提示失敗**。</span><span class="sxs-lookup"><span data-stu-id="b84fd-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="b84fd-113">對話方塊包含堆疊追蹤，指出判斷提示失敗發生的位置。</span><span class="sxs-lookup"><span data-stu-id="b84fd-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="b84fd-114">判斷提示檢查偵錯模式，在編譯時，才會啟用也就是說，如果常數`DEBUG`定義。</span><span class="sxs-lookup"><span data-stu-id="b84fd-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="b84fd-115">在專案系統中，根據預設，`DEBUG`常數定義在偵錯組態，但不是在發行組態。</span><span class="sxs-lookup"><span data-stu-id="b84fd-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="b84fd-116">無法使用 F # 例外狀況處理攔截判斷提示失敗錯誤。</span><span class="sxs-lookup"><span data-stu-id="b84fd-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="b84fd-117">`assert`函式會解析成<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b84fd-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="b84fd-118">範例</span><span class="sxs-lookup"><span data-stu-id="b84fd-118">Example</span></span>

<span data-ttu-id="b84fd-119">下列程式碼範例示範如何將`assert`運算式。</span><span class="sxs-lookup"><span data-stu-id="b84fd-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="b84fd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b84fd-120">See also</span></span>

- [<span data-ttu-id="b84fd-121">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="b84fd-121">F# Language Reference</span></span>](index.md)
