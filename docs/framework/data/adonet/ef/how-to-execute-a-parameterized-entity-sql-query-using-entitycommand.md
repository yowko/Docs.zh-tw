---
title: 作法：使用 EntityCommand 執行參數化 Entity SQL 查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: d66b77553e677c42ccedf7e66bf4f5763db92fa4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192226"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a>作法：使用 EntityCommand 執行參數化 Entity SQL 查詢

本主題說明如何 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 使用物件執行具有參數的查詢 <xref:System.Data.EntityClient.EntityCommand> 。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1. 將 [AdventureWorks Sales 模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 加入至您的專案，並將您的專案設定為使用 Entity Framework。 如需詳細資訊，請參閱 [如何：使用實體資料模型 Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>範例  

 下列範例示範如何建構具有兩個參數的查詢字串。 然後它會建立 <xref:System.Data.EntityClient.EntityCommand>、將兩個參數加入到該 <xref:System.Data.EntityClient.EntityParameter> 的 <xref:System.Data.EntityClient.EntityCommand> 集合，並逐一查看 `Contact` 項目的集合。  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a>另請參閱

- [如何：執行參數化查詢](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))
- [Entity SQL 語言](./language-reference/entity-sql-language.md)
