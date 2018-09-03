---
title: Interlocked 作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 361e618578e836e10cf8655f027bed42eac7affd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393135"
---
# <a name="interlocked-operations"></a><span data-ttu-id="c06c8-102">Interlocked 作業</span><span class="sxs-lookup"><span data-stu-id="c06c8-102">Interlocked Operations</span></span>
<span data-ttu-id="c06c8-103"><xref:System.Threading.Interlocked> 類別提供方法來同步處理多個執行緒所共用之變數的存取權。</span><span class="sxs-lookup"><span data-stu-id="c06c8-103">The <xref:System.Threading.Interlocked> class provides methods that synchronize access to a variable that is shared by multiple threads.</span></span> <span data-ttu-id="c06c8-104">如果變數位於共用的記憶體中，則不同處理序的執行緒可以使用這個機制。</span><span class="sxs-lookup"><span data-stu-id="c06c8-104">The threads of different processes can use this mechanism if the variable is in shared memory.</span></span> <span data-ttu-id="c06c8-105">Interlocked 作業不可部分完成，亦即，整個作業是一個單位，同一個變數上的另一個 Interlocked 作業不可將此 Interlocked 作業中斷。</span><span class="sxs-lookup"><span data-stu-id="c06c8-105">Interlocked operations are atomic — that is, the entire operation is a unit that cannot be interrupted by another interlocked operation on the same variable.</span></span> <span data-ttu-id="c06c8-106">在使用先佔式多執行緒的作業系統中，這一點很重要，因為執行緒可在從記憶體位址載入值後便加以暫停，而不致於有機會受到修改並儲存。</span><span class="sxs-lookup"><span data-stu-id="c06c8-106">This is important in operating systems with preemptive multithreading, where a thread can be suspended after loading a value from a memory address, but before having the chance to alter it and store it.</span></span>  
  
 <span data-ttu-id="c06c8-107"><xref:System.Threading.Interlocked> 類別提供下列作業：</span><span class="sxs-lookup"><span data-stu-id="c06c8-107">The <xref:System.Threading.Interlocked> class provides the following operations:</span></span>  
  
-   <span data-ttu-id="c06c8-108">在 .NET Framework 2.0 版中，<xref:System.Threading.Interlocked.Add%2A> 方法會在變數中新增整數值，並傳回新的變數值。</span><span class="sxs-lookup"><span data-stu-id="c06c8-108">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method adds an integer value to a variable and returns the new value of the variable.</span></span>  
  
-   <span data-ttu-id="c06c8-109">在 .NET Framework 2.0 版中，<xref:System.Threading.Interlocked.Read%2A> 方法會以不可部分完成的作業形式，讀取 64 位元的整數值。</span><span class="sxs-lookup"><span data-stu-id="c06c8-109">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Read%2A> method reads a 64-bit integer value as an atomic operation.</span></span> <span data-ttu-id="c06c8-110">這在 32 位元作業系統上很實用，因為讀取 64 位元的整數通常不是不可部分完成的作業。</span><span class="sxs-lookup"><span data-stu-id="c06c8-110">This is useful on 32-bit operating systems, where reading a 64-bit integer is not ordinarily an atomic operation.</span></span>  
  
-   <span data-ttu-id="c06c8-111"><xref:System.Threading.Interlocked.Increment%2A> 和 <xref:System.Threading.Interlocked.Decrement%2A> 方法會遞增或遞減變數，並傳回產生的值。</span><span class="sxs-lookup"><span data-stu-id="c06c8-111">The <xref:System.Threading.Interlocked.Increment%2A> and <xref:System.Threading.Interlocked.Decrement%2A> methods increment or decrement a variable and return the resulting value.</span></span>  
  
-   <span data-ttu-id="c06c8-112"><xref:System.Threading.Interlocked.Exchange%2A> 方法會以不可部分完成的方式，交換指定變數中的值、傳回該值，並以新值取代。</span><span class="sxs-lookup"><span data-stu-id="c06c8-112">The <xref:System.Threading.Interlocked.Exchange%2A> method performs an atomic exchange of the value in a specified variable, returning that value and replacing it with a new value.</span></span> <span data-ttu-id="c06c8-113">在 .NET Framework 2.0 版中，這個方法的泛型多載可用來對任何參考型別的變數執行這項交換。</span><span class="sxs-lookup"><span data-stu-id="c06c8-113">In the .NET Framework version 2.0, a generic overload of this method can be used to perform this exchange on a variable of any reference type.</span></span> <span data-ttu-id="c06c8-114">請參閱 <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>。</span><span class="sxs-lookup"><span data-stu-id="c06c8-114">See <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.</span></span>  
  
-   <span data-ttu-id="c06c8-115"><xref:System.Threading.Interlocked.CompareExchange%2A> 方法也會交換兩個值，但取決於比較的結果。</span><span class="sxs-lookup"><span data-stu-id="c06c8-115">The <xref:System.Threading.Interlocked.CompareExchange%2A> method also exchanges two values, but contingent on the result of a comparison.</span></span> <span data-ttu-id="c06c8-116">在 .NET Framework 2.0 版中，這個方法的泛型多載可用來對任何參考型別的變數執行這項交換。</span><span class="sxs-lookup"><span data-stu-id="c06c8-116">In the .NET Framework version 2.0, a generic overload of this method can be used to perform this exchange on a variable of any reference type.</span></span> <span data-ttu-id="c06c8-117">請參閱 <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>。</span><span class="sxs-lookup"><span data-stu-id="c06c8-117">See <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.</span></span>  
  
 <span data-ttu-id="c06c8-118">在新型處理器上，<xref:System.Threading.Interlocked> 類別的方法通常可透過單一指令來實作。</span><span class="sxs-lookup"><span data-stu-id="c06c8-118">On modern processors, the methods of the <xref:System.Threading.Interlocked> class can often be implemented by a single instruction.</span></span> <span data-ttu-id="c06c8-119">因此，這些方法能提供極高效能的同步處理作業，並可用來建置更高層級的同步處理機制，例如微調鎖定。</span><span class="sxs-lookup"><span data-stu-id="c06c8-119">Thus, they provide very high-performance synchronization and can be used to build higher-level synchronization mechanisms, like spin locks.</span></span>  
  
 <span data-ttu-id="c06c8-120">如需使用 <xref:System.Threading.Monitor> 和 <xref:System.Threading.Interlocked> 類別組合的範例，請參閱[監視](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="c06c8-120">For an example that uses the <xref:System.Threading.Monitor> and <xref:System.Threading.Interlocked> classes in combination, see [Monitors](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="compareexchange-example"></a><span data-ttu-id="c06c8-121">CompareExchange 範例</span><span class="sxs-lookup"><span data-stu-id="c06c8-121">CompareExchange Example</span></span>  
 <span data-ttu-id="c06c8-122"><xref:System.Threading.Interlocked.CompareExchange%2A> 方法可用來保護比簡單遞增和遞減更複雜的計算。</span><span class="sxs-lookup"><span data-stu-id="c06c8-122">The <xref:System.Threading.Interlocked.CompareExchange%2A> method can be used to protect computations that are more complicated than simple increment and decrement.</span></span> <span data-ttu-id="c06c8-123">下列範例示範安全執行緒方法，此方法可新增到儲存為浮點數的計算加總 </span><span class="sxs-lookup"><span data-stu-id="c06c8-123">The following example demonstrates a thread-safe method that adds to a running total stored as a floating point number.</span></span> <span data-ttu-id="c06c8-124">(對於整數，<xref:System.Threading.Interlocked.Add%2A> 方法是較簡單的解決方案)。如需完整的程式碼範例，請參閱 <xref:System.Threading.Interlocked.CompareExchange%2A> 的多載，其可接受單精確度和雙精度浮點引數 (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> 和 <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>)。</span><span class="sxs-lookup"><span data-stu-id="c06c8-124">(For integers, the <xref:System.Threading.Interlocked.Add%2A> method is a simpler solution.) For complete code examples, see the overloads of <xref:System.Threading.Interlocked.CompareExchange%2A> that take single-precision and double-precision floating-point arguments (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> and <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a><span data-ttu-id="c06c8-125">Exchange 和 CompareExchange 的不具型別多載</span><span class="sxs-lookup"><span data-stu-id="c06c8-125">Untyped Overloads of Exchange and CompareExchange</span></span>  
 <span data-ttu-id="c06c8-126"><xref:System.Threading.Interlocked.Exchange%2A> 和 <xref:System.Threading.Interlocked.CompareExchange%2A> 方法的多載接受類型 <xref:System.Object> 的引數。</span><span class="sxs-lookup"><span data-stu-id="c06c8-126">The <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods have overloads that take arguments of type <xref:System.Object>.</span></span> <span data-ttu-id="c06c8-127">這些多載各自的第一個引數是 `ref Object` (在 Visual Basic 中為 `ByRef … As Object`)，且類型安全會要求傳遞給這個引數的變數嚴格限制為 <xref:System.Object> 類型；在呼叫這些方法時，您不能只是將第一個引數轉換為 <xref:System.Object> 類型。</span><span class="sxs-lookup"><span data-stu-id="c06c8-127">The first argument of each of these overloads is `ref Object` (`ByRef … As Object` in Visual Basic), and type safety requires the variable passed to this argument to be typed strictly as <xref:System.Object>; you cannot simply cast the first argument to type <xref:System.Object> when calling these methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c06c8-128">在 .NET Framework 2.0 版中，使用 <xref:System.Threading.Interlocked.Exchange%2A> 和 <xref:System.Threading.Interlocked.CompareExchange%2A> 方法的泛型多載來交換強式類型的變數。</span><span class="sxs-lookup"><span data-stu-id="c06c8-128">In the .NET Framework version 2.0, use the generic overloads of the <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods to exchange strongly typed variables.</span></span>  
  
 <span data-ttu-id="c06c8-129">下列程式碼範例會示範 `ClassA` 型別的屬性，這種屬性只能設定一次，因為它可能會在 .NET Framework 1.0 或 1.1 版中實作。</span><span class="sxs-lookup"><span data-stu-id="c06c8-129">The following code example shows a property of type `ClassA` that can be set only once, as it might be implemented in the .NET Framework version 1.0 or 1.1.</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c06c8-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="c06c8-130">See Also</span></span>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="c06c8-131">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="c06c8-131">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="c06c8-132">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="c06c8-132">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
