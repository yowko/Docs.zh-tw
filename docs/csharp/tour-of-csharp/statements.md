---
title: "C# 陳述式 - C# 語言教學課程"
description: "您將使用陳述式來建立 C# 程式的動作"
keywords: ".NET, csharp, 陳述式, 語法"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 99ec2489daf89926da9b8c4e148965412826a8a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="statements"></a><span data-ttu-id="87a22-104">陳述式</span><span class="sxs-lookup"><span data-stu-id="87a22-104">Statements</span></span>

<span data-ttu-id="87a22-105">程式的動作是藉由*陳述式*來表達。</span><span class="sxs-lookup"><span data-stu-id="87a22-105">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="87a22-106">C# 支援數種不同類型的陳述式，其中一些是以內嵌陳述式來定義。</span><span class="sxs-lookup"><span data-stu-id="87a22-106">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="87a22-107">「區塊」可允許在許可單一陳述式的內容中撰寫多個陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a22-107">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="87a22-108">區塊是由在 `{` 與 `}` 分隔符號之間撰寫的陳述式清單所組成。</span><span class="sxs-lookup"><span data-stu-id="87a22-108">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="87a22-109">「宣告陳述式」可用來宣告區域變數和常數。</span><span class="sxs-lookup"><span data-stu-id="87a22-109">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="87a22-110">「運算式陳述式」可用來評估運算式。</span><span class="sxs-lookup"><span data-stu-id="87a22-110">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="87a22-111">可用來作為陳述式的運算式包括方法叫用、使用 `new` 運算子的物件配置、使用 `=` 和複合指派運算子的指派、使用 `++` 和 `--` 運算子的遞增和遞減運算，以及 `await` 運算。</span><span class="sxs-lookup"><span data-stu-id="87a22-111">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="87a22-112">「選取範圍陳述式」可用來選取一些可能陳述式的其中之一，以根據某個運算式的值來執行。</span><span class="sxs-lookup"><span data-stu-id="87a22-112">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="87a22-113">在此群組中的是 `if` 和 `switch` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a22-113">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="87a22-114">「反覆運算陳述式」可用來重複執行內嵌的陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a22-114">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="87a22-115">在此群組中的是 `while`、`do`、`for` 及 `foreach` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a22-115">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="87a22-116">「跳躍陳述式」可用來轉移控制項。</span><span class="sxs-lookup"><span data-stu-id="87a22-116">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="87a22-117">在此群組中的是 `break`、`continue`、`goto`、`throw`、`return` 及 `yield` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a22-117">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="87a22-118">`try`...`catch` 陳述式可用來攔截在執行區塊時發生的例外狀況，而 `try`...`finally` 陳述式則可用來指定不論是否發生例外狀況都一律會執行的最終處理程式碼。</span><span class="sxs-lookup"><span data-stu-id="87a22-118">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="87a22-119">`checked` 和 `unchecked` 陳述式可用來控制整數型別算術運算和轉換的溢位檢查內容。</span><span class="sxs-lookup"><span data-stu-id="87a22-119">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="87a22-120">`lock` 陳述式可用來取得所指定物件的互斥鎖定、執行陳述式，然後釋放鎖定。</span><span class="sxs-lookup"><span data-stu-id="87a22-120">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="87a22-121">`using` 陳述式可用來取得資源、執行陳述式，然後處置該資源。</span><span class="sxs-lookup"><span data-stu-id="87a22-121">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="87a22-122">以下列出可供使用的陳述式類型，並提供每個陳述式的範例。</span><span class="sxs-lookup"><span data-stu-id="87a22-122">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="87a22-123">區域變數宣告：</span><span class="sxs-lookup"><span data-stu-id="87a22-123">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="87a22-124">區域常數宣告：</span><span class="sxs-lookup"><span data-stu-id="87a22-124">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="87a22-125">運算式陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-125">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="87a22-126">`if` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-126">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="87a22-127">`switch` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-127">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="87a22-128">`while` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-128">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="87a22-129">`do` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-129">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="87a22-130">`for` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-130">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="87a22-131">`foreach` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-131">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="87a22-132">`break` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-132">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="87a22-133">`continue` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-133">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="87a22-134">`goto` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-134">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="87a22-135">`return` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-135">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="87a22-136">`yield` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-136">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="87a22-137">`throw` 陳述式和 `try` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-137">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="87a22-138">`checked` 和 `unchecked` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-138">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="87a22-139">`lock` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-139">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="87a22-140">`using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a22-140">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
<span data-ttu-id="87a22-141">[上一頁](expressions.md)
[下一頁](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="87a22-141">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
