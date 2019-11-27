---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350746"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="0faac-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0faac-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="0faac-103">指定一個或多個宣告的成員變數參考可引發事件之類別的實例。</span><span class="sxs-lookup"><span data-stu-id="0faac-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="0faac-104">備註</span><span class="sxs-lookup"><span data-stu-id="0faac-104">Remarks</span></span>

<span data-ttu-id="0faac-105">使用 `WithEvents`定義變數時，您可以使用 `Handles` 關鍵字，以宣告方式指定方法處理變數的事件。</span><span class="sxs-lookup"><span data-stu-id="0faac-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="0faac-106">您只能在類別或模組層級使用 `WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="0faac-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="0faac-107">這表示 `WithEvents` 變數的宣告內容必須是類別或模組，而且不能是原始程式檔、命名空間、結構或程式。</span><span class="sxs-lookup"><span data-stu-id="0faac-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="0faac-108">您不能在結構成員上使用 `WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="0faac-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="0faac-109">您只能使用 `WithEvents`宣告個別變數（而非陣列）。</span><span class="sxs-lookup"><span data-stu-id="0faac-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="0faac-110">規則</span><span class="sxs-lookup"><span data-stu-id="0faac-110">Rules</span></span>

<span data-ttu-id="0faac-111">**元素類型。**</span><span class="sxs-lookup"><span data-stu-id="0faac-111">**Element Types.**</span></span> <span data-ttu-id="0faac-112">您必須將 `WithEvents` 變數宣告為物件變數，使其可以接受類別實例。</span><span class="sxs-lookup"><span data-stu-id="0faac-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="0faac-113">不過，您無法將它們宣告為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="0faac-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="0faac-114">您必須將它們宣告為可引發事件的特定類別。</span><span class="sxs-lookup"><span data-stu-id="0faac-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="0faac-115">`WithEvents` 修飾詞可以在此內容中使用： [Dim 語句](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="0faac-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="0faac-116">範例</span><span class="sxs-lookup"><span data-stu-id="0faac-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="0faac-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0faac-117">See also</span></span>

- [<span data-ttu-id="0faac-118">Handles</span><span class="sxs-lookup"><span data-stu-id="0faac-118">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="0faac-119">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0faac-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="0faac-120">事件</span><span class="sxs-lookup"><span data-stu-id="0faac-120">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
