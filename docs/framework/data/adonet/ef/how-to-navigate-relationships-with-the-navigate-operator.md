---
title: "如何：使用 NAVIGATE 運算子導覽關聯性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 20451f661bd4bcd2338af81bef0cf1d07b0a5637
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a>如何：使用 NAVIGATE 運算子導覽關聯性
本主題顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 物件，針對概念模型執行命令，以及如何使用 <xref:System.Data.Metadata.Edm.RefType> 擷取 <xref:System.Data.EntityClient.EntityDataReader> 結果。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1.  新增[AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)至您的專案，並設定專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[How to： 使用實體資料模型精靈](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
2.  在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>範例  
 下列範例示範如何巡覽關聯性中的[!INCLUDE[esql](../../../../../includes/esql-md.md)]使用[瀏覽](../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)運算子。 `Navigate`運算子接受下列參數： 實體、 關聯性類型、 關聯性、 結尾和關聯性開始的執行個體。 （選擇性） 您可以將實體和關聯性類型的執行個體傳遞`Navigate`運算子。  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a>請參閱  
 [Entity Framework 的 EntityClient 提供者](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
