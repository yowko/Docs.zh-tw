---
title: "LINQ 和泛型類型 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e62a1573fa5ebf51a5f0f23b133c274730cfbeb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="linq-and-generic-types-c"></a><span data-ttu-id="dbe6a-102">LINQ 和泛型類型 (C#)</span><span class="sxs-lookup"><span data-stu-id="dbe6a-102">LINQ and Generic Types (C#)</span></span>
[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="dbe6a-103"> 查詢是以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 版中引進的泛型型別為基礎。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-103"> queries are based on generic types, which were introduced in version 2.0 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="dbe6a-104">您不需要深入了解泛型，就可以開始撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-104">You do not need an in-depth knowledge of generics before you can start writing queries.</span></span> <span data-ttu-id="dbe6a-105">不過，您可能需要了解兩個基本概念：</span><span class="sxs-lookup"><span data-stu-id="dbe6a-105">However, you may want to understand two basic concepts:</span></span>  
  
1.  <span data-ttu-id="dbe6a-106">建立泛型集合類別 (例如 <xref:System.Collections.Generic.List%601>) 的執行個體時，請將 "T" 取代為清單中會包含之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-106">When you create an instance of a generic collection class such as <xref:System.Collections.Generic.List%601>, you replace the "T" with the type of objects that the list will hold.</span></span> <span data-ttu-id="dbe6a-107">例如，字串的清單是以 `List<string>` 表示，而 `Customer` 物件的清單則是以 `List<Customer>` 表示。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-107">For example, a list of strings is expressed as `List<string>`, and a list of `Customer` objects is expressed as `List<Customer>`.</span></span> <span data-ttu-id="dbe6a-108">泛型清單是強型別，而且優點多於以 <xref:System.Object> 形式儲存項目的集合。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-108">A generic list is strongly typed and provides many benefits over collections that store their elements as <xref:System.Object>.</span></span> <span data-ttu-id="dbe6a-109">如果您嘗試將 `Customer` 新增至 `List<string>`，則會在編譯時收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-109">If you try to add a `Customer` to a `List<string>`, you will get an error at compile time.</span></span> <span data-ttu-id="dbe6a-110">由於不需要執行執行階段類型轉換，因此您可以輕鬆使用泛型集合。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-110">It is easy to use generic collections because you do not have to perform run-time type-casting.</span></span>  
  
2.  <span data-ttu-id="dbe6a-111"><xref:System.Collections.Generic.IEnumerable%601> 介面藉由使用 `foreach` 陳述式來列舉泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-111"><xref:System.Collections.Generic.IEnumerable%601> is the interface that enables generic collection classes to be enumerated by using the `foreach` statement.</span></span> <span data-ttu-id="dbe6a-112">泛型集合類別支援 <xref:System.Collections.Generic.IEnumerable%601>，就像 <xref:System.Collections.ArrayList> 這類非泛型集合類別支援 <xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-112">Generic collection classes support <xref:System.Collections.Generic.IEnumerable%601> just as non-generic collection classes such as <xref:System.Collections.ArrayList> support <xref:System.Collections.IEnumerable>.</span></span>  
  
 <span data-ttu-id="dbe6a-113">如需泛型的詳細資訊，請參閱[泛型](../../../../csharp/programming-guide/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-113">For more information about generics, see [Generics](../../../../csharp/programming-guide/generics/index.md).</span></span>  
  
## <a name="ienumerablet-variables-in-linq-queries"></a><span data-ttu-id="dbe6a-114">LINQ 查詢中的 IEnumerable<T\> 變數</span><span class="sxs-lookup"><span data-stu-id="dbe6a-114">IEnumerable<T\> variables in LINQ Queries</span></span>  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="dbe6a-115"> 查詢變數的類型為 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601> 這類衍生類型。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-115"> query variables are typed as <xref:System.Collections.Generic.IEnumerable%601> or a derived type such as <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="dbe6a-116">當您看到類型為 `IEnumerable<Customer>` 的查詢變數時，只表示查詢在執行時會產生由零個以上的 `Customer` 物件所組成的序列。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-116">When you see a query variable that is typed as `IEnumerable<Customer>`, it just means that the query, when it is executed, will produce a sequence of zero or more `Customer` objects.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]  
  
 <span data-ttu-id="dbe6a-117">如需詳細資訊，請參閱 [LINQ 查詢作業中的類型關聯性](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-117">For more information, see [Type Relationships in LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a><span data-ttu-id="dbe6a-118">讓編譯器處理泛型型別宣告</span><span class="sxs-lookup"><span data-stu-id="dbe6a-118">Letting the Compiler Handle Generic Type Declarations</span></span>  
 <span data-ttu-id="dbe6a-119">如果您想要，也可以使用 [var](../../../../csharp/language-reference/keywords/var.md) 關鍵字避免使用泛型語法。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-119">If you prefer, you can avoid generic syntax by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword.</span></span> <span data-ttu-id="dbe6a-120">`var` 關鍵字會指示編譯器查看 `from` 子句中指定的資料來源，來推斷查詢變數的類型。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-120">The `var` keyword instructs the compiler to infer the type of a query variable by looking at the data source specified in the `from` clause.</span></span> <span data-ttu-id="dbe6a-121">下列範例會產生與上一個範例相同的已編譯程式碼：</span><span class="sxs-lookup"><span data-stu-id="dbe6a-121">The following example produces the same compiled code as the previous example:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]  
  
 <span data-ttu-id="dbe6a-122">當變數的類型很明顯，或不需要明確指定巢狀泛型型別 (例如群組查詢所產生的巢狀泛型型別) 時，`var` 關鍵字會很有用。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-122">The `var` keyword is useful when the type of the variable is obvious or when it is not that important to explicitly specify nested generic types such as those that are produced by group queries.</span></span> <span data-ttu-id="dbe6a-123">一般而言，如果使用 `var`，建議您考慮到它會讓其他人更難看懂您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-123">In general, we recommend that if you use `var`, realize that it can make your code more difficult for others to read.</span></span> <span data-ttu-id="dbe6a-124">如需詳細資訊，請參閱[隱含型別區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe6a-124">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe6a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbe6a-125">See Also</span></span>  
 [<span data-ttu-id="dbe6a-126">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="dbe6a-126">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="dbe6a-127">泛型</span><span class="sxs-lookup"><span data-stu-id="dbe6a-127">Generics</span></span>](../../../../csharp/programming-guide/generics/index.md)
