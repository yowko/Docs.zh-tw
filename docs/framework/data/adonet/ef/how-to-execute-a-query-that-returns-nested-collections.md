---
title: 如何：執行可傳回巢狀集合的查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 5e282bce5f2519592babad0afcf7f8a326cf936d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530564"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="44513-102">如何：執行可傳回巢狀集合的查詢</span><span class="sxs-lookup"><span data-stu-id="44513-102">How to: Execute a Query that Returns Nested Collections</span></span>
<span data-ttu-id="44513-103">顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 物件針對概念模型執行命令，以及如何使用 <xref:System.Data.EntityClient.EntityDataReader> 擷取巢狀集合結果。</span><span class="sxs-lookup"><span data-stu-id="44513-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="44513-104">執行此範例中的程式碼</span><span class="sxs-lookup"><span data-stu-id="44513-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="44513-105">新增[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)至您的專案，並設定您的專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="44513-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="44513-106">如需詳細資訊，請參閱 <<c0> [ 如何： 使用 Entity Data Model 精靈](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)。</span><span class="sxs-lookup"><span data-stu-id="44513-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="44513-107">在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：</span><span class="sxs-lookup"><span data-stu-id="44513-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="44513-108">範例</span><span class="sxs-lookup"><span data-stu-id="44513-108">Example</span></span>  
 <span data-ttu-id="44513-109">A*巢狀集合*是位於另一個集合的集合。</span><span class="sxs-lookup"><span data-stu-id="44513-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="44513-110">下列程式碼會擷取 `Contacts` 的集合，以及與每一個 `SalesOrderHeaders` 相關聯的 `Contact` 巢狀集合。</span><span class="sxs-lookup"><span data-stu-id="44513-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="44513-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44513-111">See Also</span></span>  
 [<span data-ttu-id="44513-112">Entity Framework 的 EntityClient 提供者</span><span class="sxs-lookup"><span data-stu-id="44513-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
