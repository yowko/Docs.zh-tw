---
title: HOW TO：使用資料表值使用者定義函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: eedc2e9b997e91ed9fe0038f260aa475d23a0627
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186825"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="95614-102">HOW TO：使用資料表值使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="95614-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="95614-103">資料表值函式會傳回單一資料列集 (Rowset)，而不像預存程序 (Stored Procedure) 會傳回多個結果圖案。</span><span class="sxs-lookup"><span data-stu-id="95614-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="95614-104">因為資料表值函式的傳回型別為 `Table`，所以在可使用資料表的 SQL 中，您可以在任意處使用資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="95614-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="95614-105">您也可以如同處理資料表一樣來處理資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="95614-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95614-106">範例</span><span class="sxs-lookup"><span data-stu-id="95614-106">Example</span></span>  
 <span data-ttu-id="95614-107">下列 SQL 函式明確地指出它傳回 `TABLE`。</span><span class="sxs-lookup"><span data-stu-id="95614-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="95614-108">因此，會以隱含的方式定義傳回的資料列集結構。</span><span class="sxs-lookup"><span data-stu-id="95614-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="95614-109">函式的對應，如下所示：</span><span class="sxs-lookup"><span data-stu-id="95614-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="95614-110">範例</span><span class="sxs-lookup"><span data-stu-id="95614-110">Example</span></span>  
 <span data-ttu-id="95614-111">下列 SQL 程式碼顯示您可以聯結 (Join) 至函式所傳回的資料表，否則就如同處理其他資料表一樣地處理該資料表：</span><span class="sxs-lookup"><span data-stu-id="95614-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="95614-112">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，查詢會依照下列方式轉譯：</span><span class="sxs-lookup"><span data-stu-id="95614-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="95614-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95614-113">See also</span></span>

- [<span data-ttu-id="95614-114">使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="95614-114">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
