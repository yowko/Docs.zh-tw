---
title: 以獨佔模式使用預存程序來自訂作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 61230ffc5cd055ee64de9d519cdfb4d76c856ca3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128644"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="94d67-102">以獨佔模式使用預存程序來自訂作業</span><span class="sxs-lookup"><span data-stu-id="94d67-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="94d67-103">在常見的案例中使用預存程序存取資料。</span><span class="sxs-lookup"><span data-stu-id="94d67-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94d67-104">範例</span><span class="sxs-lookup"><span data-stu-id="94d67-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="94d67-105">描述</span><span class="sxs-lookup"><span data-stu-id="94d67-105">Description</span></span>  
 <span data-ttu-id="94d67-106">您可以修改中提供的範例[自訂作業藉由使用預存程序](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)藉由包裝預存程序的方法呼叫中取代甚至是第一個查詢 （這會導致動態 SQL 執行）。</span><span class="sxs-lookup"><span data-stu-id="94d67-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="94d67-107">假設 `CustomersByCity` 為下列範例中的方法。</span><span class="sxs-lookup"><span data-stu-id="94d67-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="94d67-108">程式碼</span><span class="sxs-lookup"><span data-stu-id="94d67-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="94d67-109">下列程式碼會在沒有任何動態 SQL 的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="94d67-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="94d67-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94d67-110">See also</span></span>

- [<span data-ttu-id="94d67-111">開發人員覆寫預設行為的責任</span><span class="sxs-lookup"><span data-stu-id="94d67-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
