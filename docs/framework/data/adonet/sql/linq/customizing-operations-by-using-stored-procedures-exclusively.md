---
title: "以獨佔模式使用預存程序來自訂作業"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 075565570d8dccc9ebd41d4a8d56014f8bb0f039
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="19639-102">以獨佔模式使用預存程序來自訂作業</span><span class="sxs-lookup"><span data-stu-id="19639-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="19639-103">在常見的案例中使用預存程序存取資料。</span><span class="sxs-lookup"><span data-stu-id="19639-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19639-104">範例</span><span class="sxs-lookup"><span data-stu-id="19639-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="19639-105">說明</span><span class="sxs-lookup"><span data-stu-id="19639-105">Description</span></span>  
 <span data-ttu-id="19639-106">您可以修改提供的範例[自訂作業所使用預存程序](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)即使第一個查詢 （這會導致執行動態 SQL） 取代為方法呼叫包裝預存程序。</span><span class="sxs-lookup"><span data-stu-id="19639-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="19639-107">假設 `CustomersByCity` 為下列範例中的方法。</span><span class="sxs-lookup"><span data-stu-id="19639-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="19639-108">程式碼</span><span class="sxs-lookup"><span data-stu-id="19639-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="19639-109">下列程式碼會在沒有任何動態 SQL 的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="19639-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="19639-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19639-110">See Also</span></span>  
 [<span data-ttu-id="19639-111">開發人員覆寫預設行為的責任</span><span class="sxs-lookup"><span data-stu-id="19639-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
