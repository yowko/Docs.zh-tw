---
title: HOW TO：使用 Navigate 運算子巡覽關聯性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
ms.openlocfilehash: 94789bcc007056a26d206903dc554ffe35999823
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607945"
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a>HOW TO：使用 Navigate 運算子巡覽關聯性
本主題顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 物件，針對概念模型執行命令，以及如何使用 <xref:System.Data.Metadata.Edm.RefType> 擷取 <xref:System.Data.EntityClient.EntityDataReader> 結果。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1. 新增[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)至您的專案，並設定您的專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[如何：使用 Entity Data Model 精靈](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>範例  
 下列範例示範如何瀏覽中的關聯性[!INCLUDE[esql](../../../../../includes/esql-md.md)]利用[NAVIGATE](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)運算子。 `Navigate`運算子可接受下列參數： 實體、 關聯性類型、 關聯性，結尾與開頭的關聯性的執行個體。 （選擇性） 您可以在其中傳遞的實體和關聯性類型的執行個體`Navigate`運算子。  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a>另請參閱

- [Entity Framework 的 EntityClient 提供者](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
- [Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
