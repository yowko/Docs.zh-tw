---
title: 如何：使用 NAVIGATE 運算子導覽關聯性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
ms.openlocfilehash: 4327aacf4cb7ec8b30c2f46696e2a19b1b3ae18c
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44352529"
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a><span data-ttu-id="85747-102">如何：使用 NAVIGATE 運算子導覽關聯性</span><span class="sxs-lookup"><span data-stu-id="85747-102">How to: Navigate Relationships with the Navigate Operator</span></span>
<span data-ttu-id="85747-103">本主題顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 物件，針對概念模型執行命令，以及如何使用 <xref:System.Data.Metadata.Edm.RefType> 擷取 <xref:System.Data.EntityClient.EntityDataReader> 結果。</span><span class="sxs-lookup"><span data-stu-id="85747-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="85747-104">執行此範例中的程式碼</span><span class="sxs-lookup"><span data-stu-id="85747-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="85747-105">新增[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)至您的專案，並設定您的專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="85747-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="85747-106">如需詳細資訊，請參閱 <<c0> [ 如何： 使用 Entity Data Model 精靈](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)。</span><span class="sxs-lookup"><span data-stu-id="85747-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="85747-107">在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：</span><span class="sxs-lookup"><span data-stu-id="85747-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="85747-108">範例</span><span class="sxs-lookup"><span data-stu-id="85747-108">Example</span></span>  
 <span data-ttu-id="85747-109">下列範例示範如何瀏覽中的關聯性[!INCLUDE[esql](../../../../../includes/esql-md.md)]利用[NAVIGATE](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="85747-109">The following example shows how to navigate relationships in [!INCLUDE[esql](../../../../../includes/esql-md.md)] by using the [NAVIGATE](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) operator.</span></span> <span data-ttu-id="85747-110">`Navigate`運算子可接受下列參數： 實體、 關聯性類型、 關聯性，結尾與開頭的關聯性的執行個體。</span><span class="sxs-lookup"><span data-stu-id="85747-110">The `Navigate` operator takes the following parameters: an instance of an entity, the relationship type, the end of the relationship, and the beginning of the relationship.</span></span> <span data-ttu-id="85747-111">（選擇性） 您可以在其中傳遞的實體和關聯性類型的執行個體`Navigate`運算子。</span><span class="sxs-lookup"><span data-stu-id="85747-111">Optionally, you can pass only an instance of an entity and the relationship type to the `Navigate` operator.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="85747-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85747-112">See Also</span></span>  
 [<span data-ttu-id="85747-113">Entity Framework 的 EntityClient 提供者</span><span class="sxs-lookup"><span data-stu-id="85747-113">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [<span data-ttu-id="85747-114">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="85747-114">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
