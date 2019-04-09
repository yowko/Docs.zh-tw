---
title: HOW TO：以內嵌方式呼叫使用者定義函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: ed8071352902b8f97445cbfa5ff0ebe8fead9bb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163705"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="e2f99-102">HOW TO：以內嵌方式呼叫使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="e2f99-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="e2f99-103">雖然您可以用內嵌 (Inline) 方式呼叫使用者定義的函式，但是在執行查詢之前，並不會執行已延後執行的查詢中所含的函式。</span><span class="sxs-lookup"><span data-stu-id="e2f99-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="e2f99-104">如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e2f99-104">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="e2f99-105">在查詢外部呼叫相同的函式時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會透過方法呼叫運算式來建立簡單的查詢。</span><span class="sxs-lookup"><span data-stu-id="e2f99-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="e2f99-106">下列是 SQL 語法 (參數 `@p0` 會繫結至傳入的常數)：</span><span class="sxs-lookup"><span data-stu-id="e2f99-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e2f99-107">會建立下列項目：</span><span class="sxs-lookup"><span data-stu-id="e2f99-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="e2f99-108">範例</span><span class="sxs-lookup"><span data-stu-id="e2f99-108">Example</span></span>  
 <span data-ttu-id="e2f99-109">在下列[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]查詢中，您可以看到的內嵌呼叫產生的使用者定義函式方法`ReverseCustName`。</span><span class="sxs-lookup"><span data-stu-id="e2f99-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="e2f99-110">因為延後查詢執行，所以不會立即執行函式。</span><span class="sxs-lookup"><span data-stu-id="e2f99-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="e2f99-111">針對這個查詢建置的 SQL，會轉譯為對資料庫中使用者定義函式的呼叫 (請參閱查詢後面的 SQL 程式碼)。</span><span class="sxs-lookup"><span data-stu-id="e2f99-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2f99-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2f99-112">See also</span></span>

- [<span data-ttu-id="e2f99-113">使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="e2f99-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
