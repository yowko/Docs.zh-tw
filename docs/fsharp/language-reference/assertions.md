---
title: 判斷提示 (F#)
description: "了解如何使用 'assert' 運算式做為偵錯功能的測試在 F # 程式語言中的運算式。"
ms.date: 05/16/2016
ms.openlocfilehash: 83e6cd77bbbb2c32e9b778e5bf6dd9d2e9c8fe32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563142"
---
# <a name="assertions"></a><span data-ttu-id="a7c10-103">判斷提示</span><span class="sxs-lookup"><span data-stu-id="a7c10-103">Assertions</span></span>

<span data-ttu-id="a7c10-104">`assert`運算式是偵錯功能，可用來測試一個運算式。</span><span class="sxs-lookup"><span data-stu-id="a7c10-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="a7c10-105">當運算式在偵測模式中發生錯誤時，判斷提示會顯示系統錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a7c10-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7c10-106">語法</span><span class="sxs-lookup"><span data-stu-id="a7c10-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="a7c10-107">備註</span><span class="sxs-lookup"><span data-stu-id="a7c10-107">Remarks</span></span>

<span data-ttu-id="a7c10-108">`assert`運算式具有型別`bool -> unit`。</span><span class="sxs-lookup"><span data-stu-id="a7c10-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="a7c10-109">在先前的語法，*條件*表示要測試的布林運算式。</span><span class="sxs-lookup"><span data-stu-id="a7c10-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="a7c10-110">如果運算式評估為`true`，執行會持續不受影響。</span><span class="sxs-lookup"><span data-stu-id="a7c10-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="a7c10-111">如果評估為`false`，系統錯誤 對話方塊就會產生。</span><span class="sxs-lookup"><span data-stu-id="a7c10-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="a7c10-112">錯誤對話方塊具有標題包含字串**判斷提示失敗**。</span><span class="sxs-lookup"><span data-stu-id="a7c10-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="a7c10-113">此對話方塊包含堆疊追蹤，指出發生判斷提示失敗。</span><span class="sxs-lookup"><span data-stu-id="a7c10-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="a7c10-114">判斷提示檢查只有當您偵錯模式，在編譯時，才會啟用也就是說，如果常數`DEBUG`定義。</span><span class="sxs-lookup"><span data-stu-id="a7c10-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="a7c10-115">在專案系統中，依預設，`DEBUG`常數定義在偵錯組態，但不是在發行組態。</span><span class="sxs-lookup"><span data-stu-id="a7c10-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="a7c10-116">無法使用 F # 例外狀況處理攔截判斷提示失敗錯誤。</span><span class="sxs-lookup"><span data-stu-id="a7c10-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="a7c10-117">`assert`函式會解析成<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a7c10-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="a7c10-118">範例</span><span class="sxs-lookup"><span data-stu-id="a7c10-118">Example</span></span>

<span data-ttu-id="a7c10-119">下列程式碼範例說明使用`assert`運算式。</span><span class="sxs-lookup"><span data-stu-id="a7c10-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="a7c10-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7c10-120">See Also</span></span>

[<span data-ttu-id="a7c10-121">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="a7c10-121">F# Language Reference</span></span>](index.md)
