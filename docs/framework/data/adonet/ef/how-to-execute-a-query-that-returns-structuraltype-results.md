---
title: HOW TO：執行可傳回 StructuralType 結果的查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: 7b649abb21b8f6ebbbd8aadc279b2902b3e21e25
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854543"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a>作法：執行可傳回 StructuralType 結果的查詢
本主題顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 物件，針對概念模型執行命令，以及如何使用 <xref:System.Data.Metadata.Edm.StructuralType> 擷取 <xref:System.Data.EntityClient.EntityDataReader> 結果。 <xref:System.Data.Metadata.Edm.EntityType>、<xref:System.Data.Metadata.Edm.RowType> 和 <xref:System.Data.Metadata.Edm.ComplexType> 類別都衍生自 <xref:System.Data.Metadata.Edm.StructuralType> 類別。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1. 將[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)加入至您的專案，並將專案設定為使用 Entity Framework。 如需詳細資訊，請參閱[如何：使用實體資料模型 Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>範例  
 此範例會執行傳回 <xref:System.Data.Metadata.Edm.EntityType> 結果的查詢。 如果您將下列查詢當做引數傳遞至 `ExecuteStructuralTypeQuery` 函式，則函式會顯示 `Products` 的相關詳細資料：  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 如果您傳遞了參數型查詢 (類似下列查詢)，請將 <xref:System.Data.EntityClient.EntityParameter> 物件加入至 <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> 物件的 <xref:System.Data.EntityClient.EntityCommand> 屬性。  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](./language-reference/entity-sql-reference.md)
- [Entity Framework 的 EntityClient 提供者](entityclient-provider-for-the-entity-framework.md)
