---
title: HOW TO：執行可傳回巢狀集合的查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: accbf44c20e52fbce5104721b50bc1650d7fd565
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251501"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a>HOW TO：執行可傳回巢狀集合的查詢
顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 物件針對概念模型執行命令，以及如何使用 <xref:System.Data.EntityClient.EntityDataReader> 擷取巢狀集合結果。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1. 將[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)新增至您的專案, 並將您的[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]專案設定為使用。 如需詳細資訊，請參閱[如何：使用實體資料模型 Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>範例  
 *嵌套集合*是另一個集合中的集合。 下列程式碼會擷取 `Contacts` 的集合，以及與每一個 `SalesOrderHeaders` 相關聯的 `Contact` 巢狀集合。  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a>另請參閱

- [Entity Framework 的 EntityClient 提供者](entityclient-provider-for-the-entity-framework.md)
