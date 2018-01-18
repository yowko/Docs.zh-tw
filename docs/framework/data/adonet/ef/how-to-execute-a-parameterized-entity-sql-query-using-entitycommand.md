---
title: "如何：使用 EntityCommand 執行 Entity SQL 查詢"
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
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 703b6ebc1eb985cd40eb1ff57660f96f1693c35a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a>如何：使用 EntityCommand 執行 Entity SQL 查詢
本主題示範如何執行[!INCLUDE[esql](../../../../../includes/esql-md.md)]使用具有參數的查詢<xref:System.Data.EntityClient.EntityCommand>物件。  
  
### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼  
  
1.  新增[AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)至您的專案，並設定專案使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。 如需詳細資訊，請參閱[How to： 使用實體資料模型精靈](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
2.  在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>範例  
 下列範例示範如何建構具有兩個參數的查詢字串。 然後它會建立 <xref:System.Data.EntityClient.EntityCommand>、將兩個參數加入到該 <xref:System.Data.EntityClient.EntityParameter> 的 <xref:System.Data.EntityClient.EntityCommand> 集合，並逐一查看 `Contact` 項目的集合。  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a>請參閱  
 [如何： 執行參數化的查詢](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
 [Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
