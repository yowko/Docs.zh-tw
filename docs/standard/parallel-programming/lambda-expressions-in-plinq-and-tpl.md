---
title: PLINQ 和 TPL 中的 Lambda 運算式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 3d985a003fe613699c89e38583f84be9e21b383d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290664"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="4f441-102">PLINQ 和 TPL 中的 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="4f441-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="4f441-103">工作平行程式庫 (TPL) 包含了許多會採用其中一個委派的 <xref:System.Func%601?displayProperty=nameWithType> 或 <xref:System.Action?displayProperty=nameWithType> 系列作為輸入參數的方法。</span><span class="sxs-lookup"><span data-stu-id="4f441-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="4f441-104">您可以使用這些委派將您自訂的程式邏輯傳遞到平行迴圈、工作或查詢中。</span><span class="sxs-lookup"><span data-stu-id="4f441-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="4f441-105">TPL 以及 PLINQ 的程式碼範例會使用 lambda 運算式來建立這些委派的執行個體，以作為內嵌程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="4f441-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="4f441-106">本主題將簡單介紹 Func 與 Action，並說明如何在工作平行程式庫和 PLINQ 中使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="4f441-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="4f441-107">如需有關委派的一般詳細資訊，請參閱[委派](../../csharp/programming-guide/delegates/index.md)和[委派](../../visual-basic/programming-guide/language-features/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4f441-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="4f441-108">如需 C# 和 Visual Basic 中之 lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)和 [Lambda 運算式](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="4f441-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="4f441-109">Func 委派</span><span class="sxs-lookup"><span data-stu-id="4f441-109">Func Delegate</span></span>

<span data-ttu-id="4f441-110">`Func` 委派所封裝的方法會傳回值。</span><span class="sxs-lookup"><span data-stu-id="4f441-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="4f441-111">在簽章中 `Func` ，最後一個或最右邊的型別參數一律會指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="4f441-111">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="4f441-112">其中一個常見的編譯器錯誤原因是嘗試將兩個輸入參數傳入 <xref:System.Func%602?displayProperty=nameWithType>；事實上，此型別只會採用一個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="4f441-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="4f441-113">.Net 會定義17版的 `Func` ： <xref:System.Func%601?displayProperty=nameWithType> 、 <xref:System.Func%602?displayProperty=nameWithType> 、 <xref:System.Func%603?displayProperty=nameWithType> ，依此類推 <xref:System.Func%6017?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4f441-113">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="4f441-114">Action 委派</span><span class="sxs-lookup"><span data-stu-id="4f441-114">Action Delegate</span></span>

<span data-ttu-id="4f441-115"><xref:System.Action?displayProperty=nameWithType>委派會封裝不會傳回值的方法（Visual Basic 中的 Sub）。</span><span class="sxs-lookup"><span data-stu-id="4f441-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="4f441-116">在型別簽章中 `Action` ，型別參數只代表輸入參數。</span><span class="sxs-lookup"><span data-stu-id="4f441-116">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="4f441-117">如同 `Func` ，.net 定義了17版的 `Action` ，從沒有型別參數的版本，一直到具有16個型別參數的版本。</span><span class="sxs-lookup"><span data-stu-id="4f441-117">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="4f441-118">範例</span><span class="sxs-lookup"><span data-stu-id="4f441-118">Example</span></span>

<span data-ttu-id="4f441-119">下列 <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> 方法的範例顯示如何透過使用 Lambda 運算式來表達 Func 與 Action 委派。</span><span class="sxs-lookup"><span data-stu-id="4f441-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="4f441-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f441-120">See also</span></span>

- [<span data-ttu-id="4f441-121">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="4f441-121">Parallel Programming</span></span>](index.md)
