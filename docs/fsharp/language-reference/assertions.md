---
title: 判斷提示
description: 瞭解如何使用「判斷提示」運算式做為程式F#設計語言中測試運算式的偵錯工具。
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630032"
---
# <a name="assertions"></a><span data-ttu-id="addd4-103">判斷提示</span><span class="sxs-lookup"><span data-stu-id="addd4-103">Assertions</span></span>

<span data-ttu-id="addd4-104">`assert`運算式是一種可供您用來測試運算式的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="addd4-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="addd4-105">當運算式在偵測模式中發生錯誤時，判斷提示會顯示系統錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="addd4-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="addd4-106">語法</span><span class="sxs-lookup"><span data-stu-id="addd4-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="addd4-107">備註</span><span class="sxs-lookup"><span data-stu-id="addd4-107">Remarks</span></span>

<span data-ttu-id="addd4-108">運算式`assert`的類型`bool -> unit`為。</span><span class="sxs-lookup"><span data-stu-id="addd4-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="addd4-109">在先前的語法中,*條件*代表要測試的布林運算式。</span><span class="sxs-lookup"><span data-stu-id="addd4-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="addd4-110">如果運算式評估為`true`, 則執行會繼續受到影響。</span><span class="sxs-lookup"><span data-stu-id="addd4-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="addd4-111">如果評估為`false`, 就會產生 [系統錯誤] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="addd4-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="addd4-112">錯誤對話方塊具有包含字串判斷提示**失敗**的標題。</span><span class="sxs-lookup"><span data-stu-id="addd4-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="addd4-113">此對話方塊包含一個堆疊追蹤, 指出判斷提示失敗的位置。</span><span class="sxs-lookup"><span data-stu-id="addd4-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="addd4-114">只有當您在 Debug 模式下編譯時, 才會啟用判斷提示檢查;也就是說, 如果已定義常數`DEBUG` , 則為。</span><span class="sxs-lookup"><span data-stu-id="addd4-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="addd4-115">根據預設, 專案系統中的`DEBUG`常數是在 Debug 設定中定義, 而不是在發行設定中定義。</span><span class="sxs-lookup"><span data-stu-id="addd4-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="addd4-116">無法使用F#例外狀況處理來攔截判斷提示失敗錯誤。</span><span class="sxs-lookup"><span data-stu-id="addd4-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="addd4-117">函式會將<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>解析為。 `assert`</span><span class="sxs-lookup"><span data-stu-id="addd4-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="addd4-118">範例</span><span class="sxs-lookup"><span data-stu-id="addd4-118">Example</span></span>

<span data-ttu-id="addd4-119">下列程式碼範例說明`assert`運算式的用法。</span><span class="sxs-lookup"><span data-stu-id="addd4-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="addd4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="addd4-120">See also</span></span>

- [<span data-ttu-id="addd4-121">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="addd4-121">F# Language Reference</span></span>](index.md)
