---
title: "PLINQ 和 TPL 中的 Lambda 運算式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 364d23db41aac4733226189f7c8ae85d281b9887
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="cd3dd-102">PLINQ 和 TPL 中的 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="cd3dd-102">Lambda Expressions in PLINQ and TPL</span></span>
<span data-ttu-id="cd3dd-103">工作平行程式庫 (TPL) 包含了許多會採用其中一個委派的 <xref:System.Func%601?displayProperty=nameWithType> 或 <xref:System.Action?displayProperty=nameWithType> 系列作為輸入參數的方法。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="cd3dd-104">您可以使用這些委派將您自訂的程式邏輯傳遞到平行迴圈、工作或查詢中。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="cd3dd-105">TPL 以及 PLINQ 的程式碼範例會使用 lambda 運算式來建立這些委派的執行個體，以作為內嵌程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="cd3dd-106">本主題將簡單介紹 Func 與 Action，並說明如何在工作平行程式庫和 PLINQ 中使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>  
  
 <span data-ttu-id="cd3dd-107">**注意：**一般來說，如需委派的詳細資訊，請參閱[委派](../../csharp/programming-guide/delegates/index.md)和[委派](../../visual-basic/programming-guide/language-features/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-107">**Note** For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="cd3dd-108">如需 C# 和 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中之 lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)和 [Lambda 運算式](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-108">For more information about lambda expressions in C# and [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], see [Lambda Expressions](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="func-delegate"></a><span data-ttu-id="cd3dd-109">Func 委派</span><span class="sxs-lookup"><span data-stu-id="cd3dd-109">Func Delegate</span></span>  
 <span data-ttu-id="cd3dd-110">`Func` 委派所封裝的方法會傳回值。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="cd3dd-111">在 Func 簽章中，最後一個或最右邊的型別參數一律會指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-111">In a Func signature, the last or rightmost type parameter always specifies the return type.</span></span> <span data-ttu-id="cd3dd-112">其中一個常見的編譯器錯誤原因是嘗試將兩個輸入參數傳入 <xref:System.Func%602?displayProperty=nameWithType>；事實上，此型別只會採用一個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="cd3dd-113">Framework 類別庫定義了 17 個版的 `Func`：<xref:System.Func%601?displayProperty=nameWithType>、<xref:System.Func%602?displayProperty=nameWithType>、<xref:System.Func%603?displayProperty=nameWithType> 等，依此類推一直到 <xref:System.Func%6017?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-113">The Framework Class Library defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>  
  
## <a name="action-delegate"></a><span data-ttu-id="cd3dd-114">Action 委派</span><span class="sxs-lookup"><span data-stu-id="cd3dd-114">Action Delegate</span></span>  
 <span data-ttu-id="cd3dd-115"><xref:System.Action?displayProperty=nameWithType> 委派所封裝的方法 (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中為 Sub) 不會傳回值，或是會傳回 [void](~/docs/csharp/language-reference/keywords/void.md)。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) that does not return a value, or returns [void](~/docs/csharp/language-reference/keywords/void.md).</span></span> <span data-ttu-id="cd3dd-116">在 Action 型別簽章中，型別參數只代表輸入參數。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-116">In an Action type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="cd3dd-117">就像 Func，Framework Class Library 會定義 17 個版本的 Action，從不具型別參數的版本，一直到具有 16 個型別參數的版本。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-117">Like Func, the Framework Class Library defines 17 versions of Action, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd3dd-118">範例</span><span class="sxs-lookup"><span data-stu-id="cd3dd-118">Example</span></span>  
 <span data-ttu-id="cd3dd-119">下列 <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> 方法的範例顯示如何透過使用 Lambda 運算式來表達 Func 與 Action 委派。</span><span class="sxs-lookup"><span data-stu-id="cd3dd-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="cd3dd-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd3dd-120">See Also</span></span>  
 [<span data-ttu-id="cd3dd-121">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="cd3dd-121">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
