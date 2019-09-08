---
title: 作法：使用有參數的預存程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 4f2636d3bb248adbb6b912887012b0b9c246c590
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793070"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="a70e6-102">作法：使用有參數的預存程序</span><span class="sxs-lookup"><span data-stu-id="a70e6-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a70e6-103">會將輸出參數對應至參考參數，而且會針對實值型別 (Value Type)，將參數宣告為可為 Null。</span><span class="sxs-lookup"><span data-stu-id="a70e6-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="a70e6-104">如需如何在傳回資料列集的查詢中使用輸入參數的範例，請參閱[如何：傳回資料](how-to-return-rowsets.md)列集。</span><span class="sxs-lookup"><span data-stu-id="a70e6-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a70e6-105">範例</span><span class="sxs-lookup"><span data-stu-id="a70e6-105">Example</span></span>  
 <span data-ttu-id="a70e6-106">下列範例取用單一輸入參數 (客戶 ID)，並傳回輸出參數 (該客戶的總銷售量)。</span><span class="sxs-lookup"><span data-stu-id="a70e6-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
```  
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="a70e6-107">範例</span><span class="sxs-lookup"><span data-stu-id="a70e6-107">Example</span></span>  
 <span data-ttu-id="a70e6-108">您可如下呼叫這個預存程序 (Stored Procedure)：</span><span class="sxs-lookup"><span data-stu-id="a70e6-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a70e6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a70e6-109">See also</span></span>

- [<span data-ttu-id="a70e6-110">預存程序</span><span class="sxs-lookup"><span data-stu-id="a70e6-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="a70e6-111">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="a70e6-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="a70e6-112">使用可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="a70e6-112">Using Nullable Types</span></span>](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="a70e6-113">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="a70e6-113">Nullable Value Types</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
