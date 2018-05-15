---
title: 如何：使用 EntityCommand 執行 Entity SQL 查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: c8469f8f13178a09c636d33070fd5ad4cbb912aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="9f1b3-102">如何：使用 EntityCommand 執行 Entity SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="9f1b3-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="9f1b3-103">本主題示範如何執行[!INCLUDE[esql](../../../../../includes/esql-md.md)]使用具有參數的查詢<xref:System.Data.EntityClient.EntityCommand>物件。</span><span class="sxs-lookup"><span data-stu-id="9f1b3-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="9f1b3-104">執行此範例中的程式碼</span><span class="sxs-lookup"><span data-stu-id="9f1b3-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="9f1b3-105">新增[AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)至您的專案，並設定專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9f1b3-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="9f1b3-106">如需詳細資訊，請參閱[How to： 使用實體資料模型精靈](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)。</span><span class="sxs-lookup"><span data-stu-id="9f1b3-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="9f1b3-107">在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：</span><span class="sxs-lookup"><span data-stu-id="9f1b3-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="9f1b3-108">範例</span><span class="sxs-lookup"><span data-stu-id="9f1b3-108">Example</span></span>  
 <span data-ttu-id="9f1b3-109">下列範例示範如何建構具有兩個參數的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="9f1b3-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="9f1b3-110">然後它會建立 <xref:System.Data.EntityClient.EntityCommand>、將兩個參數加入到該 <xref:System.Data.EntityClient.EntityParameter> 的 <xref:System.Data.EntityClient.EntityCommand> 集合，並逐一查看 `Contact` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="9f1b3-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="9f1b3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f1b3-111">See Also</span></span>  
 [<span data-ttu-id="9f1b3-112">如何： 執行參數化的查詢</span><span class="sxs-lookup"><span data-stu-id="9f1b3-112">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
 [<span data-ttu-id="9f1b3-113">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="9f1b3-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
