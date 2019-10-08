---
title: HOW TO：以內嵌方式呼叫使用者定義函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 01ba9ab4359cbd124b2207c87d5dae904641911a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002993"
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="f7f25-102">HOW TO：以內嵌方式呼叫使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="f7f25-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="f7f25-103">雖然您可以用內嵌 (Inline) 方式呼叫使用者定義的函式，但是在執行查詢之前，並不會執行已延後執行的查詢中所含的函式。</span><span class="sxs-lookup"><span data-stu-id="f7f25-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="f7f25-104">如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="f7f25-104">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="f7f25-105">在查詢外部呼叫相同的函式時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會透過方法呼叫運算式來建立簡單的查詢。</span><span class="sxs-lookup"><span data-stu-id="f7f25-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="f7f25-106">下列是 SQL 語法 (參數 `@p0` 會繫結至傳入的常數)：</span><span class="sxs-lookup"><span data-stu-id="f7f25-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```sql  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f7f25-107">會建立下列項目：</span><span class="sxs-lookup"><span data-stu-id="f7f25-107">creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="f7f25-108">範例</span><span class="sxs-lookup"><span data-stu-id="f7f25-108">Example</span></span>  
 <span data-ttu-id="f7f25-109">在下列 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢中，您可以看到所產生之使用者定義函數方法的內嵌呼叫 `ReverseCustName`。</span><span class="sxs-lookup"><span data-stu-id="f7f25-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="f7f25-110">因為延後查詢執行，所以不會立即執行函式。</span><span class="sxs-lookup"><span data-stu-id="f7f25-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="f7f25-111">針對這個查詢建置的 SQL，會轉譯為對資料庫中使用者定義函式的呼叫 (請參閱查詢後面的 SQL 程式碼)。</span><span class="sxs-lookup"><span data-stu-id="f7f25-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```sql  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7f25-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7f25-112">See also</span></span>

- [<span data-ttu-id="f7f25-113">使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="f7f25-113">User-Defined Functions</span></span>](user-defined-functions.md)
