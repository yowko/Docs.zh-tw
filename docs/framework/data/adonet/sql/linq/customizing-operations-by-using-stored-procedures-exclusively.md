---
title: 以獨佔模式使用預存程序來自訂作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 3c60a9e430b4228117fd03a43a30f27342154b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357510"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="dca60-102">以獨佔模式使用預存程序來自訂作業</span><span class="sxs-lookup"><span data-stu-id="dca60-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="dca60-103">在常見的案例中使用預存程序存取資料。</span><span class="sxs-lookup"><span data-stu-id="dca60-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dca60-104">範例</span><span class="sxs-lookup"><span data-stu-id="dca60-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="dca60-105">描述</span><span class="sxs-lookup"><span data-stu-id="dca60-105">Description</span></span>  
 <span data-ttu-id="dca60-106">您可以修改提供的範例[自訂作業所使用預存程序](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)即使第一個查詢 （這會導致執行動態 SQL） 取代為方法呼叫包裝預存程序。</span><span class="sxs-lookup"><span data-stu-id="dca60-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="dca60-107">假設 `CustomersByCity` 為下列範例中的方法。</span><span class="sxs-lookup"><span data-stu-id="dca60-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dca60-108">程式碼</span><span class="sxs-lookup"><span data-stu-id="dca60-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="dca60-109">下列程式碼會在沒有任何動態 SQL 的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="dca60-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="dca60-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dca60-110">See Also</span></span>  
 [<span data-ttu-id="dca60-111">開發人員覆寫預設行為的責任</span><span class="sxs-lookup"><span data-stu-id="dca60-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
