---
title: 以獨佔模式使用預存程序來自訂作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 78db5cf448a19056d7265ab84d97d055748c3faa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164320"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="d32d4-102">以獨佔模式使用預存程序來自訂作業</span><span class="sxs-lookup"><span data-stu-id="d32d4-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>

<span data-ttu-id="d32d4-103">在常見的案例中使用預存程序存取資料。</span><span class="sxs-lookup"><span data-stu-id="d32d4-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d32d4-104">範例</span><span class="sxs-lookup"><span data-stu-id="d32d4-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d32d4-105">描述</span><span class="sxs-lookup"><span data-stu-id="d32d4-105">Description</span></span>  

 <span data-ttu-id="d32d4-106">您可以 [使用預存程式來修改自訂作業](customizing-operations-by-using-stored-procedures.md) 中提供的範例，方法是以包裝預存程式的方法呼叫取代第一個查詢 (，這會導致動態 SQL 執行) 。</span><span class="sxs-lookup"><span data-stu-id="d32d4-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="d32d4-107">假設 `CustomersByCity` 為下列範例中的方法。</span><span class="sxs-lookup"><span data-stu-id="d32d4-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d32d4-108">程式碼</span><span class="sxs-lookup"><span data-stu-id="d32d4-108">Code</span></span>  

 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="d32d4-109">下列程式碼會在沒有任何動態 SQL 的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="d32d4-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d32d4-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d32d4-110">See also</span></span>

- [<span data-ttu-id="d32d4-111">開發人員覆寫預設行為的責任</span><span class="sxs-lookup"><span data-stu-id="d32d4-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)
