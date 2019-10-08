---
title: HOW TO：使用與循序結果型式對應的預存程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 8378a175ab2479ab9769ca08579e1c89269eaba4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003216"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="b3790-102">HOW TO：使用與循序結果型式對應的預存程序</span><span class="sxs-lookup"><span data-stu-id="b3790-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="b3790-103">這種預存程序可以產生一個以上的結果圖案，但您會知道傳回結果的順序。</span><span class="sxs-lookup"><span data-stu-id="b3790-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="b3790-104">將此案例與您不知道傳回順序的案例相比較。</span><span class="sxs-lookup"><span data-stu-id="b3790-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="b3790-105">如需詳細資訊，請參閱[如何：使用對應至多個結果圖形 @ no__t-0 的預存程式。</span><span class="sxs-lookup"><span data-stu-id="b3790-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3790-106">範例</span><span class="sxs-lookup"><span data-stu-id="b3790-106">Example</span></span>  
 <span data-ttu-id="b3790-107">以下是可循序傳回多個結果圖案之預存程序的 T-SQL：</span><span class="sxs-lookup"><span data-stu-id="b3790-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```sql
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="b3790-108">範例</span><span class="sxs-lookup"><span data-stu-id="b3790-108">Example</span></span>  
 <span data-ttu-id="b3790-109">您可使用類似下列的程式碼來執行此預存程序。</span><span class="sxs-lookup"><span data-stu-id="b3790-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b3790-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3790-110">See also</span></span>

- [<span data-ttu-id="b3790-111">預存程序</span><span class="sxs-lookup"><span data-stu-id="b3790-111">Stored Procedures</span></span>](stored-procedures.md)
