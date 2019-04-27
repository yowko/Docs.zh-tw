---
title: HOW TO：使用與循序結果型式對應的預存程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: e51ebacb3f6be849f7b871f2d12db3ea7476b117
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877067"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="b56d8-102">HOW TO：使用與循序結果型式對應的預存程序</span><span class="sxs-lookup"><span data-stu-id="b56d8-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="b56d8-103">這種預存程序可以產生一個以上的結果圖案，但您會知道傳回結果的順序。</span><span class="sxs-lookup"><span data-stu-id="b56d8-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="b56d8-104">將此案例與您不知道傳回順序的案例相比較。</span><span class="sxs-lookup"><span data-stu-id="b56d8-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="b56d8-105">如需詳細資訊，請參閱[如何：使用對應的多個結果圖案的預存程序](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)。</span><span class="sxs-lookup"><span data-stu-id="b56d8-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b56d8-106">範例</span><span class="sxs-lookup"><span data-stu-id="b56d8-106">Example</span></span>  
 <span data-ttu-id="b56d8-107">以下是可循序傳回多個結果圖案之預存程序的 T-SQL：</span><span class="sxs-lookup"><span data-stu-id="b56d8-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="b56d8-108">範例</span><span class="sxs-lookup"><span data-stu-id="b56d8-108">Example</span></span>  
 <span data-ttu-id="b56d8-109">您可使用類似下列的程式碼來執行此預存程序。</span><span class="sxs-lookup"><span data-stu-id="b56d8-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b56d8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b56d8-110">See also</span></span>

- [<span data-ttu-id="b56d8-111">預存程序</span><span class="sxs-lookup"><span data-stu-id="b56d8-111">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
