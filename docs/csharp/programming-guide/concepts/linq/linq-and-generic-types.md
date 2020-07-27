---
title: LINQ 和泛型類型 (C#)
description: '瞭解 c # 中支援查詢的泛型型別基本概念。  LINQ 查詢是以泛型型別為基礎。'
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 98054a4a21704293faa1194dac342bc48aef138d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165638"
---
# <a name="linq-and-generic-types-c"></a><span data-ttu-id="36a6a-104">LINQ 和泛型類型 (C#)</span><span class="sxs-lookup"><span data-stu-id="36a6a-104">LINQ and Generic Types (C#)</span></span>
<span data-ttu-id="36a6a-105">LINQ 查詢是以 .NET Framework 版本2.0 引進的泛型型別為基礎。</span><span class="sxs-lookup"><span data-stu-id="36a6a-105">LINQ queries are based on generic types, which were introduced in version 2.0 of .NET Framework.</span></span> <span data-ttu-id="36a6a-106">您不需要深入了解泛型，就可以開始撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="36a6a-106">You do not need an in-depth knowledge of generics before you can start writing queries.</span></span> <span data-ttu-id="36a6a-107">不過，您可能需要了解兩個基本概念：</span><span class="sxs-lookup"><span data-stu-id="36a6a-107">However, you may want to understand two basic concepts:</span></span>  
  
1. <span data-ttu-id="36a6a-108">建立泛型集合類別 (例如 <xref:System.Collections.Generic.List%601>) 的執行個體時，請將 "T" 取代為清單中會包含之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="36a6a-108">When you create an instance of a generic collection class such as <xref:System.Collections.Generic.List%601>, you replace the "T" with the type of objects that the list will hold.</span></span> <span data-ttu-id="36a6a-109">例如，字串的清單是以 `List<string>` 表示，而 `Customer` 物件的清單則是以 `List<Customer>` 表示。</span><span class="sxs-lookup"><span data-stu-id="36a6a-109">For example, a list of strings is expressed as `List<string>`, and a list of `Customer` objects is expressed as `List<Customer>`.</span></span> <span data-ttu-id="36a6a-110">泛型清單是強型別，而且優點多於以 <xref:System.Object> 形式儲存項目的集合。</span><span class="sxs-lookup"><span data-stu-id="36a6a-110">A generic list is strongly typed and provides many benefits over collections that store their elements as <xref:System.Object>.</span></span> <span data-ttu-id="36a6a-111">如果您嘗試將 `Customer` 新增至 `List<string>`，則會在編譯時收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="36a6a-111">If you try to add a `Customer` to a `List<string>`, you will get an error at compile time.</span></span> <span data-ttu-id="36a6a-112">由於不需要執行執行階段類型轉換，因此您可以輕鬆使用泛型集合。</span><span class="sxs-lookup"><span data-stu-id="36a6a-112">It is easy to use generic collections because you do not have to perform run-time type-casting.</span></span>  
  
2. <span data-ttu-id="36a6a-113"><xref:System.Collections.Generic.IEnumerable%601> 介面藉由使用 `foreach` 陳述式來列舉泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="36a6a-113"><xref:System.Collections.Generic.IEnumerable%601> is the interface that enables generic collection classes to be enumerated by using the `foreach` statement.</span></span> <span data-ttu-id="36a6a-114">泛型集合類別支援 <xref:System.Collections.Generic.IEnumerable%601>，就像 <xref:System.Collections.ArrayList> 這類非泛型集合類別支援 <xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="36a6a-114">Generic collection classes support <xref:System.Collections.Generic.IEnumerable%601> just as non-generic collection classes such as <xref:System.Collections.ArrayList> support <xref:System.Collections.IEnumerable>.</span></span>  
  
 <span data-ttu-id="36a6a-115">如需泛型的詳細資訊，請參閱[泛型](../../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="36a6a-115">For more information about generics, see [Generics](../../generics/index.md).</span></span>  
  
## <a name="ienumerablet-variables-in-linq-queries"></a><span data-ttu-id="36a6a-116">LINQ 查詢中的 IEnumerable<T\> 變數</span><span class="sxs-lookup"><span data-stu-id="36a6a-116">IEnumerable<T\> variables in LINQ Queries</span></span>  
 <span data-ttu-id="36a6a-117">LINQ 查詢變數的類型為 <xref:System.Collections.Generic.IEnumerable%601> 或衍生類型，例如 <xref:System.Linq.IQueryable%601> 。</span><span class="sxs-lookup"><span data-stu-id="36a6a-117">LINQ query variables are typed as <xref:System.Collections.Generic.IEnumerable%601> or a derived type such as <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="36a6a-118">當您看到類型為 `IEnumerable<Customer>` 的查詢變數時，只表示查詢在執行時會產生由零個以上的 `Customer` 物件所組成的序列。</span><span class="sxs-lookup"><span data-stu-id="36a6a-118">When you see a query variable that is typed as `IEnumerable<Customer>`, it just means that the query, when it is executed, will produce a sequence of zero or more `Customer` objects.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 <span data-ttu-id="36a6a-119">如需詳細資訊，請參閱 [LINQ 查詢作業中的類型關聯性](./type-relationships-in-linq-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="36a6a-119">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a><span data-ttu-id="36a6a-120">讓編譯器處理泛型型別宣告</span><span class="sxs-lookup"><span data-stu-id="36a6a-120">Letting the Compiler Handle Generic Type Declarations</span></span>  
 <span data-ttu-id="36a6a-121">如果您想要，也可以使用 [var](../../../language-reference/keywords/var.md) 關鍵字避免使用泛型語法。</span><span class="sxs-lookup"><span data-stu-id="36a6a-121">If you prefer, you can avoid generic syntax by using the [var](../../../language-reference/keywords/var.md) keyword.</span></span> <span data-ttu-id="36a6a-122">`var` 關鍵字會指示編譯器查看 `from` 子句中指定的資料來源，來推斷查詢變數的類型。</span><span class="sxs-lookup"><span data-stu-id="36a6a-122">The `var` keyword instructs the compiler to infer the type of a query variable by looking at the data source specified in the `from` clause.</span></span> <span data-ttu-id="36a6a-123">下列範例會產生與上一個範例相同的已編譯程式碼：</span><span class="sxs-lookup"><span data-stu-id="36a6a-123">The following example produces the same compiled code as the previous example:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 <span data-ttu-id="36a6a-124">當變數的類型很明顯，或不需要明確指定巢狀泛型型別 (例如群組查詢所產生的巢狀泛型型別) 時，`var` 關鍵字會很有用。</span><span class="sxs-lookup"><span data-stu-id="36a6a-124">The `var` keyword is useful when the type of the variable is obvious or when it is not that important to explicitly specify nested generic types such as those that are produced by group queries.</span></span> <span data-ttu-id="36a6a-125">一般而言，如果使用 `var`，建議您考慮到它會讓其他人更難看懂您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="36a6a-125">In general, we recommend that if you use `var`, realize that it can make your code more difficult for others to read.</span></span> <span data-ttu-id="36a6a-126">如需詳細資訊，請參閱[隱含型別區域變數](../../classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="36a6a-126">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a6a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36a6a-127">See also</span></span>

- [<span data-ttu-id="36a6a-128">泛型</span><span class="sxs-lookup"><span data-stu-id="36a6a-128">Generics</span></span>](../../generics/index.md)
