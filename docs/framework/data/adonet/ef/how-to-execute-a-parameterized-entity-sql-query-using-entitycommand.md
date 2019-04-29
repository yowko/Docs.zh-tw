---
title: HOW TO：使用 EntityCommand 執行參數化 Entity SQL 查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: 9f87ff28c4da864df8004f3baa1a8339503fb351
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606045"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a>HOW TO：使用 EntityCommand 執行參數化 Entity SQL 查詢
本主題說明如何在執行[!INCLUDE[esql](../../../../../includes/esql-md.md)]藉由使用具有參數的查詢<xref:System.Data.EntityClient.EntityCommand>物件。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1. 新增[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)至您的專案，並設定您的專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[如何：使用 Entity Data Model 精靈](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>範例  
 下列範例示範如何建構具有兩個參數的查詢字串。 然後它會建立 <xref:System.Data.EntityClient.EntityCommand>、將兩個參數加入到該 <xref:System.Data.EntityClient.EntityParameter> 的 <xref:System.Data.EntityClient.EntityCommand> 集合，並逐一查看 `Contact` 項目的集合。  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a>另請參閱

- [如何：執行參數化的查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))
- [Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
