---
title: 作法：執行可傳回巢狀集合的查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 3bf6e08e7842fbf235b519680b81f79fba4a7228
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198401"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a>作法：執行可傳回巢狀集合的查詢

顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 物件針對概念模型執行命令，以及如何使用 <xref:System.Data.EntityClient.EntityDataReader> 擷取巢狀集合結果。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1. 將 [AdventureWorks Sales 模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 加入至您的專案，並將您的專案設定為使用 Entity Framework。 如需詳細資訊，請參閱 [如何：使用實體資料模型 Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>範例  

 *嵌套集合*是另一個集合內的集合。 下列程式碼會擷取 `Contacts` 的集合，以及與每一個 `SalesOrderHeaders` 相關聯的 `Contact` 巢狀集合。  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a>另請參閱

- [Entity Framework 的 EntityClient 提供者](entityclient-provider-for-the-entity-framework.md)
