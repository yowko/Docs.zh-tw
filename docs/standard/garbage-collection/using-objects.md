---
title: "使用實作 IDisposable 的物件"
ms.custom: 
ms.date: 04/07/2017
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
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd78c2f99ca5c8ffe3c753e158ceba3e0c458c5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="07e8c-102">使用實作 IDisposable 的物件</span><span class="sxs-lookup"><span data-stu-id="07e8c-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="07e8c-103">Common language runtime 的記憶體回收行程會回收受管理的物件所使用的記憶體，但是使用 unmanaged 的資源的類型會實作<xref:System.IDisposable>介面，讓這些未受管理的資源，以回收配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="07e8c-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="07e8c-104">實作 <xref:System.IDisposable> 的物件使用完畢時，您應呼叫物件的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作。</span><span class="sxs-lookup"><span data-stu-id="07e8c-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="07e8c-105">您可以使用下列其中一種做法：</span><span class="sxs-lookup"><span data-stu-id="07e8c-105">You can do this in one of two ways:</span></span>  
  
* <span data-ttu-id="07e8c-106">使用 C# `using` 陳述式或 Visual Basic `Using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="07e8c-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
* <span data-ttu-id="07e8c-107">藉由實作 `try/finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="07e8c-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="07e8c-108">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="07e8c-108">The using statement</span></span>

<span data-ttu-id="07e8c-109">C# 中的 `using` 陳述式和 Visual Basic 中的 `Using` 陳述式可簡化建立和清除物件所必須撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="07e8c-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="07e8c-110">`using` 陳述式會取得一項或多項資源、執行您指定的陳述式，然後自動處置該物件。</span><span class="sxs-lookup"><span data-stu-id="07e8c-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="07e8c-111">不過，`using` 陳述式只對建構物件的方法範圍內所使用的物件有其實用之處。</span><span class="sxs-lookup"><span data-stu-id="07e8c-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="07e8c-112">下列範例會使用 `using` 陳述式建立和發行 <xref:System.IO.StreamReader?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="07e8c-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="07e8c-113">請注意，雖然 <xref:System.IO.StreamReader> 類別會實作 <xref:System.IDisposable> 介面，指出它使用的是 Unmanaged 資源，但是這個範例並不會明確呼叫 <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="07e8c-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="07e8c-114">當 C# 或 Visual Basic 編譯器遇到 `using` 陳述式時，會發出相當於下列明確包含 `try/finally` 區塊之程式碼的中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="07e8c-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="07e8c-115">C#`using`陳述式也可讓您取得內部相當於巢狀在單一陳述式的多個資源`using`陳述式。</span><span class="sxs-lookup"><span data-stu-id="07e8c-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="07e8c-116">下列範例會將兩個 <xref:System.IO.StreamReader> 物件具現化，以便讀取兩個不同檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="07e8c-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="07e8c-117">Try/finally 區塊</span><span class="sxs-lookup"><span data-stu-id="07e8c-117">Try/finally block</span></span>

<span data-ttu-id="07e8c-118">您可以選擇直接實作 `try/finally` 區塊，而不將 `try/finally` 區塊包裝在 `using` 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="07e8c-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="07e8c-119">這可成為您的個人編碼風格，也可能基於下列其中一個原因而這樣做：</span><span class="sxs-lookup"><span data-stu-id="07e8c-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
* <span data-ttu-id="07e8c-120">包含 `catch` 區塊以處理 `try` 區塊中擲回的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="07e8c-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="07e8c-121">否則，當 `try/catch` 區塊不存在時，`using` 陳述式擲回的所有例外狀況都會是未處理，就連 `using` 區塊中擲回的任何例外狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="07e8c-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
* <span data-ttu-id="07e8c-122">若要將實作 <xref:System.IDisposable> 且範圍對於物件宣告所在區塊並非區域的物件具現化。</span><span class="sxs-lookup"><span data-stu-id="07e8c-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="07e8c-123">下列範例是類似於上述範例中，不同之處在於它會使用`try/catch/finally`區塊來具現化、 使用和處置<xref:System.IO.StreamReader>物件，並處理，所擲回任何例外狀況<xref:System.IO.StreamReader>建構函式和其<xref:System.IO.StreamReader.ReadToEnd%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="07e8c-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="07e8c-124">請注意，在 `finally` 中的程式碼會先確認實作 <xref:System.IDisposable> 的物件不是 `null`，再呼叫 <xref:System.IDisposable.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="07e8c-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="07e8c-125">若未這樣做，可能導致執行階段產生 <xref:System.NullReferenceException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="07e8c-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="07e8c-126">您可以遵循這個基本模式，如果您選擇實作或必須實作`try/finally`封鎖，因為您的程式語言不支援`using`陳述式但不允許直接呼叫<xref:System.IDisposable.Dispose%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="07e8c-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="07e8c-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="07e8c-127">See also</span></span>

<span data-ttu-id="07e8c-128">[清除 Unmanaged 資源](../../../docs/standard/garbage-collection/unmanaged.md) </span><span class="sxs-lookup"><span data-stu-id="07e8c-128">[Cleaning Up Unmanaged Resources](../../../docs/standard/garbage-collection/unmanaged.md) </span></span>  
<span data-ttu-id="07e8c-129">[using 陳述式 （C# 參考）](~/docs/csharp/language-reference/keywords/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="07e8c-129">[using Statement (C# Reference)](~/docs/csharp/language-reference/keywords/using-statement.md) </span></span>  
[<span data-ttu-id="07e8c-130">使用陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07e8c-130">Using Statement (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/statements/using-statement.md)
