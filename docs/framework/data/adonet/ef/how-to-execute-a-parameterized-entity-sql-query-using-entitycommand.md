---
title: 作法：使用 EntityCommand 執行參數化 Entity SQL 查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: addda1a18ab325971b823d0131338a7bb824ad5c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251534"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="f2d7b-102">作法：使用 EntityCommand 執行參數化 Entity SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="f2d7b-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="f2d7b-103">本主題說明如何[!INCLUDE[esql](../../../../../includes/esql-md.md)] <xref:System.Data.EntityClient.EntityCommand>使用物件執行具有參數的查詢。</span><span class="sxs-lookup"><span data-stu-id="f2d7b-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="f2d7b-104">執行此範例中的程式碼</span><span class="sxs-lookup"><span data-stu-id="f2d7b-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="f2d7b-105">將[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)新增至您的專案，並將您的[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]專案設定為使用。</span><span class="sxs-lookup"><span data-stu-id="f2d7b-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="f2d7b-106">如需詳細資訊，請參閱[如何：使用實體資料模型 Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="f2d7b-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="f2d7b-107">在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：</span><span class="sxs-lookup"><span data-stu-id="f2d7b-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="f2d7b-108">範例</span><span class="sxs-lookup"><span data-stu-id="f2d7b-108">Example</span></span>  
 <span data-ttu-id="f2d7b-109">下列範例示範如何建構具有兩個參數的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="f2d7b-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="f2d7b-110">然後它會建立 <xref:System.Data.EntityClient.EntityCommand>、將兩個參數加入到該 <xref:System.Data.EntityClient.EntityParameter> 的 <xref:System.Data.EntityClient.EntityCommand> 集合，並逐一查看 `Contact` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="f2d7b-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="f2d7b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2d7b-111">See also</span></span>

- <span data-ttu-id="f2d7b-112">[如何：執行參數化查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f2d7b-112">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>
- [<span data-ttu-id="f2d7b-113">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="f2d7b-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
